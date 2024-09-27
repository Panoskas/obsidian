### Equal method

``` ruby
a = "hello" 
b = "hello" 

a.equal?(b) # => false, because they are different string objects with different object IDs.

c = a 
a.equal?(c) # => true, because c references the same object as a.
```

``` ruby
array = [] 
array.empty? # => true, because the array is empty. 
str = nil str.nil? # => true, because str is nil.
```

### Spaceship operator

`<=>` (spaceship operator) returns the following:

- `-1` if the value on the left is less than the value on the right;
- `0` if the value on the left is equal to the value on the right; and
- `1` if the value on the left is greater than the value on the right.

```ruby
5 <=> 10    #=> -1
10 <=> 10   #=> 0
10 <=> 5    #=> 1
```


### Difference between == and .equal? operator

- `==` checks if the values of two objects are the same.
- `equal?` checks if two variables point to the exact same object.

### Case statement

```ruby
grade = 'F'

did_i_pass = case grade #=> create a variable `did_i_pass` and assign the result of a call to case with the variable grade passed in
  when 'A' then "Hell yeah!"
  when 'D' then "Don't tell your mother."
  else "'YOU SHALL NOT PASS!' -Gandalf"
end

```

### Unless statement

An `unless` statement works in the opposite way as an `if` statement: it only processes the code in the block if the expression evaluates to `false`. There isn’t much more to it.

```ruby
age = 19
unless age < 18
  puts "Get a job."
end

```

### Ternary Operator

The ternary operator is a one-line `if...else` statement that can make your code much more concise.

Its syntax is `conditional statement ? <execute if true> : <execute if false>`. You can assign the return value of the expression to a variable.

```ruby
age = 19
response = age < 18 ? "You still have your entire life ahead of you." : "You're all grown up."
puts response #=> "You're all grown up."
```

### Loops
#### Until loop
The `until` loop is the opposite of the `while` loop. A `while` loop continues for as long as the condition is true, whereas an `until` loop continues for as long as the condition is false. These two loops can therefore be used pretty much interchangeably. Ultimately, what your break condition is will determine which one is more readable.

As much as possible, you should avoid negating your logical expressions using `!` (not). First, it can be difficult to actually notice the exclamation point in your code. Second, using negation makes the logic more difficult to reason through and therefore makes your code more difficult to understand. These situations are where `until` shines.

We can re-write our `while` loop examples using `until`.

```ruby
i = 0
until i >= 10 do
 puts "i is #{i}"
 i += 1
end
```


You can see here that using `until` means that the loop will continue running until the condition i >= 10 is true.

The next example shows how you can use `until` to avoid the negation `!` that the above `while` loop had to use.

```ruby
until gets.chomp == "yes" do
  puts "Do you like Pizza?"
end
```

#### Ranges

What if we know exactly how many times we want our loop to run? Ruby lets us use something called a [range](https://docs.ruby-lang.org/en/3.3/Range.html) to define an interval. All we need to do is give Ruby the starting value, the ending value, and whether we want the range to be inclusive or exclusive.

```ruby
(1..5)      # inclusive range: 1, 2, 3, 4, 5
(1...5)     # exclusive range: 1, 2, 3, 4

# We can make ranges of letters, too!
('a'..'d')  # a, b, c, d
```


#### For loop

A `for` loop is used to iterate through a collection of information such as an array or range. These loops are useful if you need to do something a given number of times while also using an iterator.

```ruby
for i in 0..5
  puts "#{i} zombies incoming!"
end
```


#### Times loop

If you need to run a loop for a specified number of times, then look no further than the trusty `#times` loop. It works by iterating through a loop a specified number of times and even throws in the bonus of accessing the number it’s currently iterating through.

```ruby
5.times do
  puts "Hello, world!"
end
```


I’m sure you can guess what that code does. Ruby is easily readable that way!

```ruby
5.times do |number|
  puts "Alternative fact number #{number}"
end
```



Remember, loops will start counting from a zero index unless specified otherwise, so the first loop iteration will output `Alternative fact number 0`.

#### Arrays

An array can also be created by calling the `Array.new` method. When you call this method, you can also include up to 2 optional arguments (initial size and default value):

```ruby
Array.new               #=> []
Array.new(3)            #=> [nil, nil, nil]
Array.new(3, 7)         #=> [7, 7, 7]
Array.new(3, true)      #=> [true, true, true]
```

#### Adding and removing elements

Adding an element to an existing array is done by using the `#push` method or the shovel operator `<<`. Both methods will add elements to the end of an array and return that array with the new elements. The `#pop` method will remove the element at the end of an array and return the element that was removed.

```ruby
num_array = [1, 2]

num_array.push(3, 4)      #=> [1, 2, 3, 4]
num_array << 5            #=> [1, 2, 3, 4, 5]
num_array.pop             #=> 5
num_array                 #=> [1, 2, 3, 4]
```


The methods `#shift` and `#unshift` are used to add and remove elements at the beginning of an array. The `#unshift` method adds elements to the beginning of an array and returns that array (much like `#push`). The `#shift` method removes the first element of an array and returns that element (much like `#pop`).

```ruby
num_array = [2, 3, 4]

num_array.unshift(1)      #=> [1, 2, 3, 4]
num_array.shift           #=> 1
num_array                 #=> [2, 3, 4]
```

#### Adding and subtracting arrays

What do you think will be the outcome of `[1, 2, 3] + [3, 4, 5]`?

If you guessed `[1, 2, 3, 3, 4, 5]`, congratulations! Adding two arrays will return a new array built by concatenating them, similar to string concatenation. The `concat` method works the same way.

```ruby
a = [1, 2, 3]
b = [3, 4, 5]

a + b         #=> [1, 2, 3, 3, 4, 5]
a.concat(b)   #=> [1, 2, 3, 3, 4, 5]
```


To find the difference between two arrays, you can subtract them using `-`. This method returns a copy of the first array, removing any elements that appear in the second array.

```ruby
[1, 1, 1, 2, 2, 3, 4] - [1, 4]  #=> [2, 2, 3]
```

#### Basic Methods

Ruby gives you many methods to manipulate arrays and their contents (over 150!), many of which are beyond the scope of this lesson. To learn about other methods, go to the official documentation and browse the [Array class documentation](https://docs.ruby-lang.org/en/3.3/Array.html) page, where you can find methods listed alphabetically (by scrolling the left sidebar) or summarized and grouped by purpose (by reading under “What’s Here”).

Calling the `#methods` method on an array will also yield a long list of the available methods.

```ruby
num_array.methods       #=> A very long list of methods
```

Copy

Here is a brief look at some other common array methods you might run into:

```ruby
[].empty?               #=> true
[[]].empty?             #=> false
[1, 2].empty?           #=> false

[1, 2, 3].length        #=> 3

[1, 2, 3].reverse       #=> [3, 2, 1]

[1, 2, 3].include?(3)   #=> true
[1, 2, 3].include?("3") #=> false

[1, 2, 3].join          #=> "123"
[1, 2, 3].join("-")     #=> "1-2-3"
```

### Hashes

#### Create Hash

Let’s dive in and create a hash!

```ruby
my_hash = {
  "a random word" => "ahoy",
  "Dorothy's math test score" => 94,
  "an array" => [1, 2, 3],
  "an empty hash within a hash" => {}
}
```


This example shows the most basic way to create a hash, which is to use the hash literal of curly braces (`{}`).

The above hash has four keys that point to four different values. For example, the first key, `"a random word"`, points to the value `"ahoy"`. As you can see, the values of a hash can be a number, a string, an array, or even another hash. Keys and values are associated with a special operator called a **hash rocket**: `=>`.

Just like with an array, you can also create a new hash by calling the good old `::new` method on the `Hash` class.

```ruby
my_hash = Hash.new
my_hash               #=> {}
```


Of course, hashes don’t only take strings as keys and values. Ruby is a pretty flexible language, so you can jam any old thing in there and it’ll work just fine.

```ruby
hash = { 9 => "nine", :six => 6 }
```

#### Accessing Values

You can access values in a hash the same way that you access elements in an array. When you call a hash’s value by key, the key goes inside a pair of brackets, just like when you’re calling an array by index.

```ruby
shoes = {
  "summer" => "sandals",
  "winter" => "boots"
}

shoes["summer"]   #=> "sandals"
```


If you try to access a key that doesn’t exist in the hash, it will return `nil`:

```ruby
shoes["hiking"]   #=> nil
```


Sometimes, this behavior can be problematic for you if silently returning a `nil` value could potentially wreak havoc in your program. Luckily, hashes have a `fetch` method that will raise an error when you try to access a key that is not in your hash.

```ruby
shoes.fetch("hiking")   #=> KeyError: key not found: "hiking"
```


Alternatively, this method can return a default value instead of raising an error if the given key is not found.

```ruby
shoes.fetch("hiking", "hiking boots") #=> "hiking boots"
```

#### Adding and changing data

You can add a key-value pair to a hash by calling the key and setting the value, just like you would with any other variable.

```ruby
shoes["fall"] = "sneakers"

shoes     #=> {"summer"=>"sandals", "winter"=>"boots", "fall"=>"sneakers"}
```

Copy

You can also use this approach to change the value of an existing key.

```ruby
shoes["summer"] = "flip-flops"
shoes     #=> {"summer"=>"flip-flops", "winter"=>"boots", "fall"=>"sneakers"}
```

#### Removing Data
Deleting data from a hash is done with the hash’s `#delete` method, which provides the cool functionality of returning the value of the key-value pair that was deleted from the hash.

```ruby
shoes.delete("summer")    #=> "flip-flops"
shoes                     #=> {"winter"=>"boots", "fall"=>"sneakers"}
```

#### Merging two hashes
Occasionally, you’ll come across a situation where two hashes wish to come together in holy union. Luckily, there’s a method for that. (No ordained minister required!)

```ruby
hash1 = { "a" => 100, "b" => 200 }
hash2 = { "b" => 254, "c" => 300 }
hash1.merge(hash2)      #=> { "a" => 100, "b" => 254, "c" => 300 }
```


Notice that the values from the hash getting merged in (in this case, the values in `hash2`) overwrite the values of the hash getting… uh, merged _at_ (`hash1` here) when the two hashes have a key that’s the same.

#### Symbols as hash keys
n this lesson, we mostly used strings for hash keys, but in the real world, you’ll almost always see symbols (like `:this_guy`) used as keys. This is predominantly because symbols are far more performant than strings in Ruby, but they also allow for a much cleaner syntax when defining hashes. Behold the beauty:

```ruby
# 'Rocket' syntax
american_cars = {
  :chevrolet => "Corvette",
  :ford => "Mustang",
  :dodge => "Ram"
}
# 'Symbols' syntax
japanese_cars = {
  honda: "Accord",
  toyota: "Corolla",
  nissan: "Altima"
}
```

Copy

That last example brings a tear to the eye, doesn’t it? Notice that the hash rocket and the colon that represents a symbol have been mashed together. This unfortunately only works for symbols, though, so don’t try `{ 9: "value" }` or you’ll get a syntax error.

When you use the cleaner ‘symbols’ syntax to create a hash, you’ll still need to use the standard symbol syntax when you’re trying to access a value. In other words, regardless of which of the above two syntax options you use when creating a hash, they both create symbol keys that are accessed the same way.

```ruby
american_cars[:ford]    #=> "Mustang"
japanese_cars[:honda]   #=> "Accord"
```

### Methods

#### Bang Methods
Observe the example below:

```ruby
whisper = "HELLO EVERYBODY"

puts whisper.downcase #=> "hello everybody"
puts whisper #=> "HELLO EVERYBODY"
```


What gives? We thought we downcased that thing! So why was it back to all uppercase when we called it again?

When we call a method on an object, such as our `whisper` string above, it does not modify the original value of that object. A general rule in programming is that you do not want your methods to overwrite the objects that you call them on. This protects you from irreversibly overwriting your data by accident. You _are_ able to overwrite your data by explicitly re-assigning a variable (such as `whisper = whisper.downcase`). Another way to do this type of reassignment is with **bang methods**, which are denoted with an exclamation mark (`!`) at the end of the method name.

By adding a `!` to the end of your method, you indicate that this method performs its action and simultaneously overwrites the value of the original object with the result.

```ruby
puts whisper.downcase! #=> "hello everybody"
puts whisper #=> "hello everybody"
```

Copy

Writing `whisper.downcase!` is the equivalent of writing `whisper = whisper.downcase`.

#### Difference between puts and return
A common source of confusion for new programmers is the difference between `puts` and `return`.

- `puts` is a method that prints whatever argument you pass it to the console.
- `return` is the final output of a method that you can use in other places throughout your code.

For example, we can write a method that calculates the square of a number and then `puts` the output to the console.

```ruby
def puts_squared(number)
  puts number * number
end
```

Copy

This method only prints the value that it calculated to the console, but it doesn’t return that value. If we then write `x = puts_squared(20)`, the method will print `400` in the console, but the variable `x` will be assigned a value of `nil`. (If you need a refresher on this, go back and review the Ruby Input and Output lesson.)

Now, let’s write the same method but with an implicit return instead of `puts`. (Using an explicit return will act exactly the same in this example.)

```ruby
def return_squared(number)
  number * number
end
```


When we run the `return_squared` method, it won’t print any output to the console. Instead, it will `return` the result in a way that allows it to be used in the rest of your code. We can save the output of running this method in a variable (`x` in the code below) and use that variable in a variety of ways. If we would still like to see the result of the method in the console, we can `puts` that variable to the console using string interpolation.

```ruby
x = return_squared(20) #=> 400
y = 100
sum = x + y #=> 500

puts "The sum of #{x} and #{y} is #{sum}."
#=> The sum of 400 and 100 is 500.
```


### Enumerable
##### The each method
`#each` is the granddaddy of the enumerable methods. It’s a bit like Chuck Norris: it can do anything. As you’ll see throughout this lesson, though, just because you can use `#each` to do just about anything doesn’t mean it’s always the best or most efficient tool for the job.

Calling `#each` on an array will iterate through that array and will yield each element to a code block, where a task can be performed:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.each { |friend| puts "Hello, " + friend }

#=> Hello, Sharon
#=> Hello, Leo
#=> Hello, Leila
#=> Hello, Brian
#=> Hello, Arun

#=> ["Sharon", "Leo", "Leila", "Brian" "Arun"]
```

Copy

Let’s break down this syntax:

- `friends` is the array that contains strings of your friends’ names.
- `.each` is the enumerable method you are calling on your `friends` array.
- `{ |friend| puts "Hello, " + friend }` is a **block**, and the code inside this block is run for each element in your array. Because we have 5 friends in our array, this block will be run 5 times, once with each of the 5 elements.
- Within the block, you’ll notice that we have `|friend|`, which is known as a **block variable**. This is the element from your array that the block is currently iterating over. You can use any variable name that you find helpful here; in this example, we could have used `|x|`, but `|friend|` is more descriptive of what each element is. In the first iteration, the value of `|friend|` will be `'Sharon'`; in the second iteration, its value will be `'Leo'`; in the third, `'Leila'`; and so on until it reaches the end of the array.

What if the block you want to pass to a method requires more logic than can fit on one line? It starts to become less readable and looks unwieldy. For multi-line blocks, the commonly accepted best practice is to change up the syntax to use `do...end` instead of `{...}`:

```ruby
my_array = [1, 2]

my_array.each do |num|
  num *= 2
  puts "The new number is #{num}."
end

#=> The new number is 2.
#=> The new number is 4.

#=> [1, 2]
```


`#each` also works for hashes with a bit of added functionality. By default, each iteration will yield both the key and value individually or together (as an array) to the block depending on how you define your block variable:

```ruby
my_hash = { "one" => 1, "two" => 2 }

my_hash.each { |key, value| puts "#{key} is #{value}" }

one is 1
two is 2
#=> { "one" => 1, "two" => 2}

my_hash.each { |pair| puts "the pair is #{pair}" }

the pair is ["one", 1]
the pair is ["two", 2]
#=> { "one" => 1, "two" => 2}
```


You may have noticed in the above code examples that `#each` returns the original array or hash regardless of what happens inside the code block. This is an important thing to keep in mind when debugging your code as it can lead to some confusion.

Take this code as an example:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.each { |friend| friend.upcase }

#=> ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']
```


You might expect this to return `['SHARON', 'LEO', 'LEILA', 'BRIAN', 'ARUN']`, but you’d be wrong—dead wrong. It actually returns the original array you called `#each` on. You’re _still_ not invited, Brian.

#### The each_with_index method

This method is nearly the same as `#each`, but it provides some additional functionality by yielding two **block variables** instead of one as it iterates through an array. The first variable’s value is the element itself, while the second variable’s value is the index of that element within the array. This allows you to do things that are a bit more complex.

For example, if we only want to print every other word from an array of strings, we can achieve this like so:

```ruby
fruits = ["apple", "banana", "strawberry", "pineapple"]

fruits.each_with_index { |fruit, index| puts fruit if index.even? }

#=> apple
#=> strawberry
#=> ["apple", "banana", "strawberry", "pineapple"]
```


Just like with the `#each` method, `#each_with_index` returns the original array it’s called on.

#### The map method

Remember when we tried to use `#each` to write all of your friends’ names in all caps? For reference, this is the code that we tried:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.each { |friend| friend.upcase }

#=> ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']
```


As we can see, `#each` returns the original array, but that’s not what we want. WE WANT CAPS!

Let’s modify our `#each` code to get it to work:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']
shouting_at_friends = []

friends.each { |friend| shouting_at_friends.push(friend.upcase) }
#=> ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

shouting_at_friends #=> ['SHARON', 'LEO', 'LEILA', 'BRIAN', 'ARUN']
```


It works! It took quite a bit of extra work, though. We had to introduce another array that could store the transformed elements. This code is starting to look more clunky and suspiciously like the `for` loop example in the first section that we’re trying to get away from.

Luckily, we have the `#map` enumerable method to save us from our misery!

The `#map` method (also called `#collect`) transforms each element from an array according to whatever block you pass to it and returns the transformed elements in a new array. `#map` may seem confusing at first, but it is extremely useful. We’ll go through several examples and use cases, which should help you understand how and when you can use this enumerable power for good.

First, let’s use `#map` to improve on our code that transforms all of our friends’ names to uppercase:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.map { |friend| friend.upcase }
#=> `['SHARON', 'LEO', 'LEILA', 'BRIAN', 'ARUN']`
```


We’re back down to two lines of code, baby! Isn’t it beautiful?

Maybe now you’re getting hungry from all this intense learning and you want to change your McDonald’s order from medium to extra large. With `#map` and [`#gsub`](https://docs.ruby-lang.org/en/3.3/String.html#method-i-gsub), that’s easy peasy:

```ruby
my_order = ['medium Big Mac', 'medium fries', 'medium milkshake']

my_order.map { |item| item.gsub('medium', 'extra large') }
#=> ["extra large Big Mac", "extra large fries", "extra large milkshake"]
```

Maybe you’ve decided that it’s time for you to get your finances in order, and you want to deduct your rent payments from your salary over the past few months to make sure that you haven’t been spending all of your remaining money on extra large Big Mac meals:

```ruby
salaries = [1200, 1500, 1100, 1800]

salaries.map { |salary| salary - 700 }
#=> [500, 800, 400, 1100]
```


Whenever you want to return a new array with the results of running your block of code, `#map` is the method for you!

#### The select method

You’ve already seen the `#select` method in action at the beginning of this lesson in our quest to make Brian an outcast.

The `#select` method (also called `#filter`) passes every item in an array to a block and returns a new array with only the items for which the condition you set in the block evaluated to `true`.

First, let’s explore how we would accomplish the same thing using `#each`:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']
invited_list = []

friends.each do |friend|
  if friend != 'Brian'
    invited_list.push(friend)
  end
end

invited_list
 #=> ["Sharon", "Leo", "Leila", "Arun"]
```

Copy

Using our shiny new `#select` method, this code can be simplified down to two lines:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.select { |friend| friend != 'Brian' }

 #=> ["Sharon", "Leo", "Leila", "Arun"]
```


Now that we’ve cut out Brian, we can send out the invites! Let’s say that the friends who you invited to your party have gotten back to you, and their responses are all recorded in a hash. Let’s use `#select` to see who’s coming. Recall that when you use an enumerable method with a hash, you need to set up block variables for both the key and the value:

```ruby
responses = { 'Sharon' => 'yes', 'Leo' => 'no', 'Leila' => 'no', 'Arun' => 'yes' }
responses.select { |person, response| response == 'yes'}
#=> {"Sharon"=>"yes", "Arun"=>"yes"}
```


Looks like only Sharon and Arun can go. You’re going to need more people for a good party. Sounds like it’s time for you to reluctantly call Brian, who you know will bring a batch of his awful home-brewed IPA. Maybe his last batch has gotten better?

#### The reduce method
The `#reduce` method (also called `#inject`) is possibly the most difficult-to-grasp enumerable for new coders. The general idea is that it takes an array or hash and reduces it down to a single object. You should use `#reduce` when you want to get an output of a single value.

A classic example of when `#reduce` is useful is obtaining the sum of an array of numbers. First, let’s explore how we would achieve this using `#each`:

```ruby
my_numbers = [5, 6, 7, 8]
sum = 0

my_numbers.each { |number| sum += number }

sum
#=> 26
```

Copy

This isn’t too bad in terms of number of lines of code, but we had to introduce a temporary local variable (`sum`) outside of the enumerable. It would be much nicer if we could do all of this within the enumerable:

```ruby
my_numbers = [5, 6, 7, 8]

my_numbers.reduce { |sum, number| sum + number }
#=> 26
```

Copy

Whoa! What?! There’s a lot happening here, so let’s walk through what it’s doing step by step.

The first block variable in the `#reduce` enumerable (`sum` in this example) is known as the **accumulator**. The result of each iteration is stored in the accumulator and then passed to the next iteration. The accumulator is also the value that the `#reduce` method returns at the end of its work. By default, the initial value of the accumulator is the first element in the collection, so for each step of the iteration, we would have the following:

1. Iteration 0: sum = 5 + 6 = 11
2. Iteration 1: sum = 11 + 7 = 18
3. Iteration 2: sum = 18 + 8 = 26

We can also set a different initial value for the accumulator by directly passing in a value to the `#reduce` method.

```ruby
my_numbers = [5, 6, 7, 8]

my_numbers.reduce(1000) { |sum, number| sum + number }
#=> 1026
```

Copy

Now let’s look at a more elaborate example that shows just how powerful this method can be. This one is much more complicated, so don’t be discouraged if you don’t fully understand it at this point. Just know that `#reduce` can save you many lines of code in certain scenarios.

Now that you know who’s coming to your party, you need to decide where to go. You don’t actually like making decisions very much, so you put it to a vote among your friends.

The options are St. Mark’s Bistro, a classy place suited for a sophisticated person such as yourself. The other option is Bob’s Dirty Burger Shack, which you know is Brian’s favorite place. Since he’s coming to the party now, it’s best to include it as an option to avoid any arguments. Your friends’ votes are collected in the `votes` array.

```ruby
votes = ["Bob's Dirty Burger Shack", "St. Mark's Bistro", "Bob's Dirty Burger Shack"]

votes.reduce(Hash.new(0)) do |result, vote|
  result[vote] += 1
  result
end
#=> {"Bob's Dirty Burger Shack"=>2, "St. Mark's Bistro"=>1}
```

Copy

Alright, so what happened here? Other than Brian ruining your party. Again.

First, we passed in a much more interesting initial value for our accumulator this time. When we pass in an argument to `Hash.new`, that becomes the default value when accessing keys that do not exist in the hash. For example, we could say the following:

```ruby
hundreds = Hash.new(100)
hundreds["first"]         #=> 100
hundreds["mine"]          #=> 100
hundreds["yours"]         #=> 100
```

Copy

Once you set the value for a key equal to something else, the default value is overwritten:

```ruby
hundreds = Hash.new(100)
hundreds["new"]           #=> 100
hundreds["new"] = 99
hundreds["new"]           #=> 99
```

Copy

Now that we know that this new hash with a default value of `0` is our accumulator (which is called `result` in the code block), let’s see what happens in each iteration:

1. Iteration 0:
    - result = {}
    - Remember, this hash already has default values of `0`, so `result["Bob's Dirty Burger Shack"] == 0` and `result["St. Mark's Bistro"] == 0`
2. Iteration 1:
    - The method runs `result["Bob's Dirty Burger Shack"] += 1`
    - result = {“Bob’s Dirty Burger Shack” => 1}
3. Iteration 2:
    - The method runs `result["St. Mark's Bistro"] += 1`
    - result = {“Bob’s Dirty Burger Shack” => 1, “St. Mark’s Bistro” => 1}
4. Iteration 3:
    - The method runs `result["Bob's Dirty Burger Shack"] += 1`
    - result = {“Bob’s Dirty Burger Shack” => 2, “St. Mark’s Bistro” => 1}

Note that this example returns a hash with several `key => value` pairs. So even though the result is more complicated, `#reduce` still just returns one object, a hash.

#### Bang methods

Earlier, we mentioned that enumerables like `#map` and `#select` return new arrays but don’t modify the arrays that they were called on. This is by design since we won’t often want to modify the original array or hash and we don’t want to accidentally lose that information. For example, if enumerables did mutate the original array, then using `#select` to filter out Brian from our invitation list would _permanently_ remove him from our friends list. Whoa! That’s a bit drastic. Brian may be a nutcase at parties, but he’s still our friend.

To see this principle in action, let’s go back to an earlier example where we wrote each of our friends’ names in all caps:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.map { |friend| friend.upcase }
#=> `['SHARON', 'LEO', 'LEILA', 'BRIAN', 'ARUN']`

friends
#=> ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']
```

Copy

You can see that when we call our original `friends` array again, it remains unchanged.

If you wanted to change your `friends` array instead, you could use the bang method `#map!`:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

friends.map! { |friend| friend.upcase }
#=> `['SHARON', 'LEO', 'LEILA', 'BRIAN', 'ARUN']`

friends
#=> `['SHARON', 'LEO', 'LEILA', 'BRIAN', 'ARUN']`
```

Copy

Now when we call our original `friends` array again, it returns the changed values from the `#map!` method. Instead of returning a new array, `#map!` modified our original array.

As you’ll recall from the Methods lesson, **bang methods** can be easily identified by their exclamation marks (`!`) at the end of their name. All bang methods are **destructive** and modify the object they are called on. Many of the enumerable methods that return new versions of the array or hash they were called on have a bang method version available, such as `#map!` and `#select!`.

It’s best practice to avoid using these methods, however, as you or a future developer working on your code may need the original version. Remember that violent psychopath who you should expect will end up maintaining your code? Keep that in mind when making the decision to use bang methods.

#### Return values of enumerables


So if it’s not a good idea to use bang methods but we need to reuse the result of an enumerable method throughout our program, what can we do instead?

One option is to put the result of an enumerable method into a local variable:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

invited_friends = friends.select { |friend| friend != 'Brian' }

friends
#=> ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

invited_friends
#=> ["Sharon", "Leo", "Leila", "Arun"]
```

An even better option would be to wrap your enumerable method in a method definition:

```ruby
friends = ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

def invited_friends(friends)
  friends.select { |friend| friend != 'Brian' }
end

friends
#=> ['Sharon', 'Leo', 'Leila', 'Brian', 'Arun']

invited_friends(friends)
 #=> ["Sharon", "Leo", "Leila", "Arun"]
```

### Multi Threading

Ruby has support for multithreading, but its implementation has some important caveats:

1. Native threads: Ruby uses native operating system threads, allowing true parallelism on multi-core systems.

2. Global Interpreter Lock (GIL): In the standard implementation (MRI - Matz's Ruby Interpreter), a Global Interpreter Lock prevents multiple Ruby threads from executing Ruby code in parallel. This means that while I/O operations can run concurrently, CPU-bound tasks are limited to running on a single core.

3. Alternative implementations: Some Ruby implementations like JRuby and TruffleRuby don't have a GIL, allowing true parallel execution of Ruby code.

As for handling asynchronous requests, Ruby offers several options:

1. Thread-based concurrency: Using Ruby's Thread class to handle multiple tasks concurrently.

2. Event-driven programming: Libraries like EventMachine provide an event-driven I/O model for handling asynchronous operations.

3. Fiber-based concurrency: Fibers allow for cooperative multitasking within a single thread.

4. Async gems: There are gems like 'async' that provide abstractions for writing asynchronous code more easily.

5. Concurrent Ruby: This gem offers various tools for concurrent and parallel programming in Ruby.

6. Background job processing: Gems like Sidekiq or Resque are commonly used for handling asynchronous tasks in web applications.

1. **MRI (Matz's Ruby Interpreter)**:
   - The most commonly used Ruby interpreter.
   - Implements native threads, but due to the Global Interpreter Lock (GIL), it cannot execute more than one thread at a time in a single process. This means that while threads are useful for I/O-bound operations, they do not provide true parallelism for CPU-bound operations.

2. **JRuby**:
   - An implementation of Ruby on the Java Virtual Machine (JVM).
   - Does not have a GIL, allowing true parallel execution of threads. This makes JRuby a good choice for CPU-bound multithreaded applications.

3. **Rubinius**:
   - Another Ruby implementation which also supports native threads and does not have a GIL, allowing for true parallelism.

4. **TruffleRuby**:
   - A high-performance implementation of Ruby built on the GraalVM. It also supports parallel execution without a GIL.

#### Practical Considerations

- **I/O-bound vs. CPU-bound**: In MRI, multithreading can be quite effective for I/O-bound tasks where threads spend a lot of time waiting for external resources (e.g., reading files, network requests), as the GIL is released during these waits.
- **Concurrency Models**: For CPU-bound tasks, MRI's GIL limits the effectiveness of multithreading, so using JRuby, Rubinius, or TruffleRuby might be more appropriate.
- **Libraries and Ecosystem**: The choice of interpreter might also be influenced by the ecosystem and libraries you plan to use. MRI has the largest community and library support, which might be a consideration if certain gems are crucial for your project.

#### Example Code

Here's a simple example demonstrating multithreading in Ruby:

```ruby
threads = []

10.times do |i|
  threads << Thread.new do
    sleep(rand(0.1..1.0)) # Simulate work
    puts "Thread #{i} finished"
  end
end

threads.each(&:join)
```

This code creates and runs 10 threads, each performing a simulated workload with `sleep`.

#### Conclusion

Ruby supports multithreading across various implementations, but the efficiency and true parallelism depend on the presence of the GIL. For I/O-bound tasks, MRI's threading model is usually sufficient. For CPU-bound tasks requiring true parallelism, consider using JRuby, Rubinius, or TruffleRuby.