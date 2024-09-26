### Create method from viewset
This method handles the `POST` request logic in the view, which by default does:

-   instantiate the serializer with whatever data comes as payload in the request
-   executed the `is_valid` method on the serializer
-   perform the actual create by calling `.save()` method on serializer
-   returns the view `Response` with serialized data and 201 status

You don't really need to override the `create` method on viewset, if is something that you need to send to the serializer from the view itself you can override `perform_create` which by default does `serializer.save()`


### Create method from serializer
This method just creates the actual model instance using the `validated_data`.

```python
def create(self, validated_data):
        items_data = validated_data.pop('items')

        # similar to Parent.objects.create(**validated_data)
        parent = super().create(**validated_data)

        for item_data in items_data:
            Item.objects.create(parent=parent, **item_data)
        return parent
```

So here you are sending a payload with data regarding the `Parent` object but also a list of `items` with their representation, so now the `create` method will create also the Items and link them with the Parent instance.

To summarize this:

-   in viewset the create method handles request-response flow
-   in serializer the create method handles model instance creation using validated data.


### Filtering

There are different methods to *get*  data from a model into a QuerySet.
- The `values()` method allows you to return each object as a Python dictionary, with the names and values as key/value pairs
- The `values_list()` method allows you to return only the columns that you specify.
- You can filter the search to only return specific rows/records, by using the `filter()` method.
	- We can use multiple `filter()` methods, separated by a pipe `|` character. The results will merge into one model.
		 ```python 
mydata = Member.objects.filter(firstname='Emil').values() | Member.objects.filter(firstname='Tobias').values()
		 ```
	- The `filter()` method takes the arguments as **kwargs (keyword arguments), so you can filter on more than one field by separating them by a comma.**
		```python
		mydata = Member.objects.filter(lastname='Refsnes', id=2).values()
		```
	- Another common method is to import and use Q expressions:
		```python
		from django.http import HttpResponse
		from django.template import loader
		from .models import Member
		from django.db.models import Q
		
		def testing(request):
		  mydata = Member.objects.filter(Q(firstname='Emil') | Q(firstname='Tobias')).values()
		  template = loader.get_template('template.html')
		  context = {
		    'mymembers': mydata,
		  }
		  return HttpResponse(template.render(context, request))
		```
	- All Field lookup keywords must be specified with the fieldname, **followed by two(!) underscore characters**, and the keyword.
		```python
		mydata = Member.objects.filter(firstname__startswith='L').values()
		```

- A list of all field look up keywords:

![[Screenshot from 2023-01-09 10-47-21 2.png|1000]]

![[Screenshot from 2023-01-09 10-49-35.png|1000]]

**Filtering against query parameters**

The default behavior of REST framework's generic list views is to return the entire queryset for a model manager. We should overwrite the default `get_queryset` method;
```python
def get_queryset(self):
        """
        Optionally restricts the returned articles to given regions,
        by filtering against a `regions` query parameter in the URL.
        """
        regions = self.request.query_params.get("regions", None)
        if regions:
            qs = Article.objects.filter()
            for region in regions.split(self.region_separator):
                qs = qs.filter(regions__code=region)

            return qs

        return super().get_queryset()
```

It filters articles when `regions` query param provided, when there is no param it returns _all_ articles.

**Generic Filtering**
As well as being able to override the default queryset, REST framework also includes support for generic filtering backends that allow you to easily construct complex searches and filters.
```python
class PurchasedProductsList(generics.ListAPIView):
    """
    Return a list of all the products that the authenticated
    user has ever purchased, with optional filtering.
    """
    model = Product
    serializer_class = ProductSerializer
    filter_class = ProductFilter

    def get_queryset(self):
        user = self.request.user
        return user.purchase_set.all()
```

### Visualize your models 
1. Install *django_extensions*
2. add it to installed apps
3. add also to your settings 
	
```python   
GRAPH_MODELS = {
"all_applications": True,
"group_models": True,
}
```

4. also install  `pip install pygraphviz
5. generate the graph `python manage.py graph_models -a -g -o my_project_visualized.png`

### Foreign Keys

**ForeignKey is a Field (which represents a column in a database table), and it’s used to create many-to-one relationships within tables**
**The primary key defines the unique value for a row in a table. Foreign key connects tables using the primary key value from another table.**

```python 

class Author(models.Model):
    name = models.CharField(max_length=512)


class Book(models.Model):
    title = models.CharField(max_length=512)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

One Author can write multiple books, and one Book can be written only by one Author. That’s why we placed ForeignKey in the Book model.

**Many-to-many relationship in a database**

To maintain a many-to-many relationship between two tables in a database, the only way is to have a third table which has references to both of those tables. This table is called a “through” table and each entry in this table will connect the source table (sandwich in this case) and the target table (sauce in this case).

‍This is exactly what Django does under the hood when you use a ManyToManyField. It creates a through model which is not visible to the ORM user and whenever one needs to fetch all of the sandwiches that use a particular sauce given only the name of the sauce, the above 3 tables are joined.Joining 3 tables may not be very efficient, so if you query this information using the sauce ID instead of name, Django internally Joins only 2 tables (sandwiches_sauces and sandwiches). These join operations are invisible to the user but it helps to know what’s going on in the database so that the queries can be made as efficient as possible.

``` python

from django.db import models

class Sauce(models.Model):

	name = models.CharField(max_length=100)
	
	def __str__(self):

		return self.name

class Sandwich(models.Model):

	name = models.CharField(max_length=100)
	
	sauces = models.ManyToManyField(Sauce)

	def __str__(self):
	
		return self.name
```

Running a database migration on these models will create a Sandwich table, a Sauce table and a through table connecting the two. Let us now look at how we can access this information using the Django ORM.

**The possible values for the "foreign key" :**

-   models.CASCADE: when the referenced object is deleted, also delete the objects that have a foreign key to it.
    
-   models.PROTECT: prevent deletion of the referenced object by raising a ProtectedError.
    
-   models.SET_NULL: set the foreign key value to NULL.
    
-   models.SET_DEFAULT: set the foreign key to its default value.
    
-   models.SET_ONE: similar to SET_NULL, but for OneToOneFields only.
    
-   models.DO_NOTHING: do nothing. This is to allow the programmer to catch the IntegrityError exception raised by other database engines.

### WGSI
WSGI stands for Web Server Gateway Interface. It is a standard interface between web servers and Python web applications or frameworks, such as Django. It specifies how a web server should interact with a web application and how the application should respond to server requests. WSGI allows for a common interface for web servers and web applications to communicate, making it easier to deploy and run Python web applications. Django includes a built-in WSGI server for development, but it is typically deployed behind a production-ready web server such as Apache or Nginx in order to handle tasks such as serving static files and handling SSL.

-  **WGSI and NGINX
	- Here is an example of how to do this:

1.  Install and configure NGINX on your server.
2.  Create a configuration file for your WSGI application in the `/etc/nginx/sites-available` directory.
3.  In the configuration file, specify the location of your WSGI application and the appropriate settings for handling requests.

`server {     listen 80;     server_name example.com;     access_log /var/log/nginx/access.log;     error_log /var/log/nginx/error.log;      location / {         proxy_pass http://127.0.0.1:8000;         proxy_set_header Host $host;         proxy_set_header X-Real-IP $remote_addr;         proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;     }      location /static/ {         alias /path/to/static/;     } }`

In this example, the `location /` block tells NGINX to forward all incoming requests to the IP address `127.0.0.1` on port `8000`, where the WSGI application is running.

4.  Link the configuration file in the `/etc/nginx/sites-enabled` directory.
5.  Test the configuration by running the command `nginx -t`.
6.  Reload or restart the NGINX service with the command `systemctl reload nginx` or `systemctl restart nginx`

With this configuration, NGINX will handle all incoming HTTP requests and forward them to the WSGI application. NGINX can also handle tasks such as serving static files, SSL termination, and caching, which can improve the performance and security of your application.

You can also use other web servers such as Apache with the mod_wsgi module to handle the requests and forward it to the WSGI application.

