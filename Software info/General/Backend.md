### What is DNS
The Domain Name System (DNS) is the phonebook of the Internet.Web browsers interact through [Internet Protocol (IP)](https://www.cloudflare.com/learning/network-layer/internet-protocol/) addresses. DNS translates domain names to [IP addresses](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/) so browsers can load Internet resources.DNS servers eliminate the need for humans to memorize IP addresses such as 192.168.1.1 (in IPv4), or more complex newer alphanumeric IP addresses such as 2400:cb00:2048:1::c629:d7a2 (in IPv6).
### There are 4 DNS servers involved in loading a webpage:
-   **[DNS recursor](https://www.cloudflare.com/learning/dns/dns-server-types#recursive-resolver)** - The recursor can be thought of as a librarian who is asked to go find a particular book somewhere in a library. The DNS recursor is a server designed to receive queries from client machines through applications such as web browsers. Typically the recursor is then responsible for making additional requests in order to satisfy the client’s DNS query.
-   **Root nameserver** - The [root server](https://www.cloudflare.com/learning/dns/glossary/dns-root-server/) is the first step in translating (resolving) human readable host names into IP addresses. It can be thought of like an index in a library that points to different racks of books - typically it serves as a reference to other more specific locations.
-   **[TLD nameserver](https://www.cloudflare.com/learning/dns/dns-server-types#tld-nameserver)** - The top level domain server ([TLD](https://www.cloudflare.com/learning/dns/top-level-domain/)) can be thought of as a specific rack of books in a library. This nameserver is the next step in the search for a specific IP address, and it hosts the last portion of a hostname (In example.com, the TLD server is “com”).
-   **[Authoritative nameserver](https://www.cloudflare.com/learning/dns/dns-server-types#authoritative-nameserver)** - This final nameserver can be thought of as a dictionary on a rack of books, in which a specific name can be translated into its definition. The authoritative nameserver is the last stop in the nameserver query. If the authoritative name server has access to the requested record, it will return the IP address for the requested hostname back to the DNS Recursor (the librarian) that made the initial request.

### What is the difference between a domain name and a URL?

A uniform resource locator (URL), sometimes called a web address, contains the domain name of a site as well as other information, including the protocol and the path. For example, in the URL ‘https://cloudflare.com/learning/’, ‘cloudflare.com’ is the domain name, while ‘[https](https://www.cloudflare.com/learning/ssl/what-is-https/)’ is the protocol and ‘/learning/’ is the path to a specific page on the website.



### Web Hosting
Web hosting refers to the practice of storing websites and their associated files on servers that are connected to the internet. This allows users to access the website from anywhere in the world through a web browser.

When a website is hosted, the web hosting company provides the server space, internet connectivity, and other necessary resources for the website to function. 
**Other necessary resources for a website to function include:**

1.  Bandwidth: The amount of data that can be transferred between the server and the users' web browsers.
    
2.  Storage: The amount of disk space needed to store the website files and data.
    
3.  Server software: The software used to run the website, such as a web server (e.g. Apache, Nginx), a database server (e.g. MySQL, PostgreSQL), and programming languages (e.g. PHP, Python, Ruby).
    
4.  Email service: A service for sending and receiving email from the website domain name.
    
5.  Security features: Measures to protect the website and its visitors from hacking, malware, and other security threats.
    
6.  Backups: Regular backups of the website files and data to ensure that the website can be restored in case of data loss.
    
7.  Technical support: Support from the hosting company to help with technical issues and maintenance tasks.
    

Some hosting companies may provide these resources as part of their hosting packages, while others may offer them as add-ons or separate services.
There are different types of web hosting services, including shared hosting, dedicated hosting, and cloud hosting, each with their own advantages and disadvantages.

Shared hosting is a cost-effective solution that allows multiple websites to share a single server. Dedicated hosting, on the other hand, provides a single client with an entire server and is ideal for large and resource-intensive websites. Cloud hosting provides scalability and reliability by using a network of virtual servers to host websites.

Regardless of the type of web hosting service used, it is important to choose a reliable and trustworthy hosting provider with good customer support, as the uptime and performance of the website depends on the quality of the hosting service.

### Kernel
The kernel is the central part of an operating system that manages system resources and provides services to other software. It acts as a bridge between applications and the computer hardware. The kernel provides low-level services like memory management, process management, device management, and security management. It also handles input/output requests from software and allocates resources like CPU time and memory to different processes running on the system.
### POSIX Standard

POSIX stands for Portable Operating System Interface. It’s a family of standards specified by IEEE for maintaining compatibility among operating systems. Therefore, **any software that conforms to POSIX standards should be compatible with other operating systems that adhere to the POSIX standards**.

For that reason, most of the tools we use on Linux and Unix-like operating systems behave almost the same. For example, if we use the _ps_ command, it should behave the same under OpenBSD, Debian, and macOS.

### Stack vs Heap
In computer science, the stack and heap are two types of memory that are used for storing data in a program.

The stack is a region of memory that is used for storing variables that are declared inside a function or method. The stack is organized as a last-in, first-out (LIFO) data structure, which means that the most recently added item is the first one to be removed. The stack is usually small and limited in size, but it is very fast to access.

The heap, on the other hand, is a larger region of memory that is used for dynamic memory allocation. This is where objects, arrays, and other complex data structures are created at runtime. Unlike the stack, the heap is not organized in a specific order, so it can be slower to access. The heap is also larger than the stack, but it is less limited in size.

In general, the stack is used for storing temporary data that is needed by a function or method, while the heap is used for storing data that needs to persist beyond the lifetime of a function or method.
### Memory Management
Memory management is the process of controlling and coordinating the way a software application access **computer memory**

When a software runs on a target Operating system on a computer it needs access to the computers **RAM**(Random-access memory) to:

-   load its own **bytecode** that needs to be executed
-   store the **data values** and **data structures** used by the program that is executed
-   load any **run-time systems** that are required for the program to execute

#### Stack
The stack is used for **static memory allocation** and as the name suggests it is a last in first out(**LIFO**) stack (Think of it as a stack of boxes).

-   Due to this nature, the process of storing and retrieving data from the stack is **very fast** as there is no lookup required, you just store and retrieve data from the topmost block on it.
-   But this means any data that is stored on the stack has to be **finite and static**(The size of the data is known at compile-time).
-   This is where the execution data of the functions are stored as **stack frames**(So, this is the actual execution stack). Each frame is a block of space where the data required for that function is stored. For example, every time a function declares a new variable, it is "pushed" onto the topmost block in the stack. Then every time a function exits, the topmost block is cleared, thus all of the variables pushed onto the stack by that function, are cleared. These can be determined at compile time due to the static nature of the data stored here.
-   **Multi-threaded applications** can have a **stack per thread**.
-   Memory management of the stack is **simple and straightforward** and is done by the OS.
-   Typical data that are stored on stack are **local variables**(value types or primitives, primitive constants), **pointers** and **function frames**.
-   This is where you would encounter **stack overflow errors** as the size of the stack is limited compared to the Heap.
	- Stack overflow errors occur when a program's call stack, which is a region of memory used to manage function calls and their parameters, exceeds its allocated size. This can happen when a function repeatedly calls itself or other functions, leading to an accumulation of function call data on the stack that eventually overflows its bounds. When this happens, the program will typically terminate with an error message indicating a stack overflow.
-   There is a **limit on the size** of value that can be stored on the Stack for most languages.

#### Heap
Heap is used for **dynamic memory allocation** and unlike stack, the program needs to look up the data in heap using **pointers** (Think of it as a big multi-level library).

-   It is **slower** than stack as the process of looking up data is more involved but it can store more data than the stack.
-   This means data with **dynamic size** can be stored here.
-   Heap is **shared** among threads of an application.
-   Due to its dynamic nature heap is **trickier to manage** and this is where most of the memory management issues arise from and this is where the automatic memory management solutions from the language kick in.
-   Typical data that are stored on the heap are **global variables**, **reference types** like objects, strings, maps, and other complex data structures.
-   This is where you would encounter **out of memory errors** if your application tries to use more memory than the allocated heap(Though there are many other factors at play here like GC, compacting).
-   Generally, there is **no limit** on the size of the value that can be stored on the heap. Of course, there is the upper limit of how much memory is allocated to the application.
### I/O Devices
In general, a device will have a set of control registers which can be accessed by the CPU and permit CPU/device interactions. These registers are typically divided into: **command registers**, that the CPU uses to control the device; **data registers**, that are used by the CPU to transfer data in and out of the device; **status registers** that are used by the CPU to understand what is happening on the device.
I/O devices communicate with the kernel through device drivers, which are software programs that interface between the operating system and the device hardware. The device driver sends requests to the device controller, which is a hardware component that manages the communication between the device and the computer. The controller translates the requests into signals that the device can understand and sends them to the device. When the device sends data back, the controller converts the signals into a format that the computer can use and sends them to the device driver, which processes the data and sends it to the operating system.

The Peripheral Component Interconnect (PCI) bus is a high-speed data pathway that connects the device controller to the rest of the computer. The PCI bus allows the controller to communicate with the CPU and memory directly, without going through the slower input/output pathways.

In summary, device drivers are software programs that manage communication between the operating system and the device hardware, device controllers are hardware components that manage communication between the device and the computer, and the PCI bus is a high-speed data pathway that connects the controller to the rest of the computer.

Device controllers are on the device itself?

Yes, device controllers are usually located on the device itself. The device controller is responsible for controlling the device and managing its interactions with the computer's CPU and memory. The controller interprets the commands sent to the device and translates them into the appropriate electrical or mechanical signals to operate the device. For example, the controller for a hard disk drive is located on the hard drive itself and is responsible for controlling the movement of the read/write head and managing the flow of data to and from the disk platters.

### Computer Networking
#### What are the types of computer network architecture?

Computer network design falls under two broad categories:

1. Client-server architecture

In this type of computer network, nodes may be servers or clients. Server nodes provide resources like memory, processing power, or data to client nodes. Server nodes may also manage client node behavior. Clients may communicate with each other, but they do not share resources. For example, some computer devices in enterprise networks store data and configuration settings. These devices are the servers in the network. Clients may access this data by making a request to the server machine.

2. Peer-to-peer architecture

In Peer-to-Peer (P2P) architecture, connected computers have equal powers and privileges. There is no central server for coordination. Each device in the computer network can act as either client or server. Each peer may share some of its resources, like memory and processing power, with the entire computer network. For example, some companies use P2P architecture to host memory-consuming applications, such as 3-D graphic rendering, across multiple digital devices.

#### What is network topology?

The arrangement of nodes and links is called network topology. They can be configured in different ways to get different outcomes. Some types of network topologies are:

Bus topology

Each node is linked to one other node only. Data transmission over the network connections occurs in one direction.

Ring topology

Each node is linked to two other nodes, forming a ring. Data can flow bi-directionally. However,single node failure can bring down the entire network.

Star topology

A central server node is linked to multiple client network devices. This topology performs better as data doesn’t have to go through each node. It is also more reliable.

Mesh topology

Every node is connected to many other nodes. In a full mesh topology, every node is connected to every other node in the network.

#### What are the types of enterprise computer networks?

Depending on the organization's size and requirements, there are three common types of enterprise private networks:

Local area network (LAN)

A LAN is an interconnected system limited in size and geography. It typically connects computers and devices within a single office or building. It is used by small companies or as a test network for small-scale prototyping.

Wide area networks (WAN)

An enterprise network spanning buildings, cities, and even countries, is called a wide area network (WAN). While local area networks are used to transmit data at higher speeds within close proximity, WANs are set up for long-distance communication that is secure and dependable.

SD-WAN or software-defined WAN is virtual WAN architecture controlled by software technologies. An SD-WAN offers more flexible and dependable connectivity services that can be controlled at the application level without sacrificing security and quality of service.

Service provider networks

Service provider networks allow customers to lease network capacity and functionality from the provider. Network service providers may consist of telecommunications companies, data carriers, wireless communications providers, Internet service providers, and cable television operators offering high-speed Internet access.

Cloud networks

Conceptually, a cloud network can be seen as a WAN with its infrastructure delivered by a cloud-based service. Some or all of an organization’s network capabilities and resources are hosted in a public or private cloud platform and made available on demand. These network resources can include virtual routers, firewalls, bandwidth, and network management software,with other tools and functions available as required.

Businesses today use cloud networks to accelerate time-to-market, increase scale, and manage costs effectively. The cloud network model has become the standard approach for building and delivering applications for modern enterprises.

### Programs Threads and Processes

- Program
A program is the code that is stored on your computer that can complete a certain task. There are many types of programs, including programs built into the operating system and ones to complete specific tasks. Generally, task-specific programs are called applications (or apps). For example, you are probably reading this post using a web browser application. Other common applications include email clients, word processors, and games.

- Process
You might have multiple instances of a single program. In that situation, each instance of that running program is a process. Each process has a separate memory address space. That separate memory address is helpful because it means that a process runs independently and is isolated from other processes. However, processes cannot directly access shared data in other processes. Switching from one process to another requires some amount of time (relatively speaking) for saving and loading registers, memory maps, and other resources.

- Thread
A thread is the unit of execution within a process. A process can have anywhere from one thread to many.

In summary, a program is a set of instructions, a process is an instance of a program in execution, and a thread is a lightweight process that runs within a process.




### Authentication Authorization

- **Basic Flow of Session Based Authentication
1.  In the browser, the user enters their username and password, and the request goes from the client application to the server.
2.  Server checks for the user, authenticates it and sends a unique token to the user’s client application. (It also saves this unique token in memory or database)
3.  The client application stores the token in cookies and sends it back with each subsequent request.
4.  The server receives every request that requires authentication and uses the token to authenticate the user and returns the requested data back to the client application.
5.  When someone logs out, the client application removes that token, so that subsequent requests from the client become unauthorized.

A few major problems arise with this method of authentication:

-   Every time a user is authenticated, the server will need to create a record somewhere on the server. This is usually done in memory and when there are many users authenticating, the overhead on the server increases.
-   As sessions are stored in memory, this causes problems with scalability. If you replicate your server to multiple instances, you have to replicate all of the user sessions to all your servers, which complicates the scalability process. (Although it can be avoided by having a single dedicated server for session management but that is not always feasible and easy to implement.)

- **Basic Flow of Token-Based Authentication
1.  User enters their login credentials.
2.  Server verifies the credentials and returns a signed token (the JWT) which can contain some additional information as metadata, such as user_id, permissions, etc.
3.  This token is stored client-side, most commonly in local storage, but it can be stored in session storage or a cookie as well.
4.  Subsequent requests to the server include this token, generally as an additional authorization header in the form of a _Bearer_, but it can additionally be sent in the body of a `POST` request, or even as a query parameter.
5.  The server decodes the JWT, and, if the token is valid, processes the request.
6.  Once a user logs out, the token is destroyed client-side, no interaction with the server is necessary.
- **Benefits of this Method
1. Stateless
2. Store any type of Metadata
3. Single calls to database
4. Simpler to implement
- **Passwordless
1.  Instead of a user giving an email/username and password, they enter only their email address.
2.  Your application sends them a one-time-use link to that email, which the user clicks on to be automatically logged in to your website or application.
3.  In the case of a passwordless login, the app assumes that you will get the login link from your inbox if the email provided is indeed yours.

- **Single Sign On (SSO)
1.  The user accesses the first Google product.
2.  The user receives a Google Accounts-generated cookie.
3.  The user navigates to another Google product.
4.  The user is redirected again to Google Accounts.
5.  Google Accounts sees that the user already has an authentication-related cookie, so it redirects the user to the requested product.

-  **Social Sign In
Using this, you can authenticate a user based on their social networking accounts. Users don’t need to register separately in your application.

Social sign-in, or social login, is not technically a different authentication method. Rather, it’s a form of single sign-on which simplifies the registration/login process of a user to your application and that’s why you should know about it (as a developer).

- **Two Factor Authentication
It is a type of [multi-factor authentication](https://en.wikipedia.org/wiki/Multi-factor_authentication) which provides an extra layer of security.
After enabling two-factor authentication in your account, every time you need to login to your account, first you provide the login credentials, such as email or password (verify that you know the credentials).

Then, a one-time password (OTP) is sent to you through SMS (verify that you possess the device), and you have to enter it correctly to complete your login process.

- **OAUTH vs JWT**
JWT (JSON Web Token) is a format for token-based authentication that is used to securely transmit information between parties as a JSON object. It is often used as a way to authenticate users in web applications.

OAuth, on the other hand, is an authorization protocol. It is used to grant applications access to protected resources without requiring users to share their passwords. OAuth allows users to grant access to their resources to third-party applications without sharing their credentials.

In short, JWT is a format for transmitting information, while OAuth is a protocol for authorizing access to resources.
### GraphQL
GraphQL is an open-source query language for APIs that was developed by Facebook. It provides a more efficient, powerful and flexible alternative to traditional RESTful APIs. Instead of making multiple requests to different endpoints for fetching data, in GraphQL, the client can specify the exact data it needs from the server in a single request. The server responds with a JSON object that exactly matches the structure of the query.

One of the main differences between RESTful APIs and GraphQL is how the data is requested and returned. With RESTful APIs, the client has to make multiple requests to different endpoints to get all the data it needs. In contrast, with GraphQL, the client can request all the data it needs in a single request.

Another difference is that RESTful APIs are resource-oriented, while GraphQL is more about data relationships. In RESTful APIs, resources are typically represented by URLs, while in GraphQL, data is represented by a graph, and the client specifies the data it needs by traversing that graph.

Overall, GraphQL is a more efficient and powerful alternative to RESTful APIs, especially for applications that require a lot of data and have complex data relationships. However, it does require a bit more complexity in terms of implementation and understanding.
### Caching
Caching is a process or method of storing a copy of the continuously asked data in a temporary storage location or cache to be quickly accessed when needed.

A cache is a memory reserved for storing temporary files or data from apps, servers, websites, or browsers to help load faster when requested. It includes images, videos, animation, gifs, scripts, files, etc.
#### Server-Side Caching

Server-side caching temporarily stores web files and data on the origin server to reuse later.

When the user first requests for the webpage, the website goes under the normal process of retrieving data from the server and generates or constructs the webpage of the website. After the request has happened and the response has been sent back, the server copies the webpage and stores it as a cache.

Next time the user revisits the website, it loads the already saved or cached copy of the webpage, thus making it faster.
-   Object Caching - In Object Caching, we store database queries. As a result, it is easier to access the next time the request is made.
-  Opcode Caching - Opcode Caching is a performance booster for PHP that compiles human-readable PHP to bytecode understood by web servers.
-  CDN Caching - Content Delivery Network or CDN Caching is a group of servers around the globe to provide content delivery to website visitors.

#### Drawbacks of Server Side Caching

The main problem with server-side caching is latency. Latency may be defined as the total time for the data packet to travel from source to destination. High latency means a significant delay user's request and the server's response.

Another problem with server-side caching is that if the data changes on the webpage, the server has to reconstruct it from scratch.

#### Client-Side Caching

Client-side caching temporarily stores web files and data in the browser memory instead of keeping it in the server.

When a user visits a website, the webpage gets cached in the user's browser memory, which means a copy of the webpage is stored.
#### Types of Client-side Caching

In Client-side Caching, we try to cache enough information about a webpage without creating repetitive requests to the server. These are of the following types.

-   Browser Request Caching - Browser Request Caching is the most widely used and oldest form of caching. It is built into the HTTP protocol standard.
-   Javascript/AJAX Caching - The Javascript/AJAX caching modifies the websites to display changes made to dynamic content in real-time without refreshing the entire page.
-   HTML 5 Caching - In HTML Caching, we try to cache images and scripts and HTML content. Since HTML takes too long to load, it will delay other processes.
#### Drawbacks of Client-Side Caching

One of the drawbacks of client-side caching is that it is browser-specific, and if you use multiple browsers, there would be various cache files of the same webpage.

Another disadvantage of client-side caching is that it is more complex than server-side caching.

#### Remote Caching

Remote Caching is similar to Server Side Caching, but it can also run an application to serialize and deserialize the data. The difference is that you control the remote server, and someone else does not operate it.
### Containerization vs. Virtualization

Containerization and virtualization are both technologies that allow multiple applications or workloads to run on a single physical machine or host.
A **[virtual machine](https://middleware.io/blog/what-is-virtual-machine/)** (VM) is a technology for stimulating a physical computer. It contains the same components, an operating system (OS), a network interface, and applications. However, it’s sandboxed inside a physical computer.

This means one computer can run multiple VMs and their isolated components. These can be used to develop, stage, and produce the application code. You can build virtualized computing environments with VMs, considered the first generation of cloud computing. 

A virtual machine **cannot run without a hypervisor**. These lightweight software layers separate VMs and allocate processors, memory, and storage. They’re basically machine monitors that enable multiple operating systems to run simultaneously.
**Virtualization** refers to the process of using software to create a virtual resource that runs on a layer separate from the physical hardware. The most common use case of virtualization is cloud computing.

#### What are containers?

Containers are a means of isolating an application from its surroundings by encapsulating its dependencies and configurations in a single unit. After that, the unit can be shipped to other environments such as private clouds, public clouds, and data centres.

Containers are more lightweight and agile when it comes to virtualizing your environment without a hypervisor. They enable [DevOps](https://middleware.io/blog/what-is-devops/) to concentrate on developing and deploying code, allowing for faster resource provision. A containerized application behaves consistently across development, staging, and production environments.

Containerization works by **sharing the host OS kernel** with other containers as a read-only resource. You can deploy multiple containers on a single server or virtual machine as they’re lightweight and scalable. 


This way, you only maintain one OS and don’t dedicate an entire server to one application. Containerization is the answer to several DevOps problems. This is why several enterprises adopt this approach to migrate managed services to the cloud.

Containers let you break down applications into their smallest components or microservices. These services are developed and deployed independently, eliminating a monolithic unit.

For example, if you support multiple action buttons on your website, the failure of one doesn’t affect the performance of others. This reduces downtime, maintenance pressure, and dependency.

In simpler terms, Docker is a tool that allows you to create and run containers, while Kubernetes is a tool that helps you manage and orchestrate those containers.

Some key differences between Docker and Kubernetes are:

-   Complexity: Docker is relatively simple and easy to use, while Kubernetes has a steeper learning curve and requires more advanced knowledge and skills.
-   Scalability: Kubernetes is designed for managing large-scale container deployments, while Docker is more suited for smaller projects or single containers.
-   High Availability: Kubernetes provides advanced features for high availability and disaster recovery, while Docker lacks these capabilities.
-   Deployment: Docker can be deployed on any system that supports containers, while Kubernetes requires a dedicated infrastructure to deploy and manage containers.
Overall, Docker and Kubernetes are complementary tools that serve different purposes in the containerization and deployment process. Docker is great for creating and running containers, while Kubernetes is ideal for managing large-scale container deployments and automating the container orchestration process.
### WebSockets
Web sockets are defined as a two-way communication between the servers and the clients, which mean both the parties, communicate and exchange data at the same time. This protocol defines a full duplex communication from the ground up. Web sockets take a step forward in bringing desktop rich functionalities to the web browsers.
### Web Servers
#### Hardware Side:

A hardware web server is a computer that houses web server software and the files that make up a website (for example, HTML documents, images, CSS stylesheets, and JavaScript files). A web server establishes a connection to the Internet and facilitates the physical data exchange with other web-connected devices.

#### Software side:

A software web server has a number of software components that regulate how hosted files are accessed by online users. This is at the very least an HTTP server. Software that knows and understands HTTP and URLs (web addresses) is known as an HTTP server (the protocol your browser uses to view webpages). The content of these hosted websites is sent to the end user’s device through an HTTP server, which may be accessed via the domain names of the websites it holds.

Basically, an HTTP request is made by a browser anytime it wants a file that is stored on a web server. The relevant (hardware) web server receives the request, which is then accepted by the appropriate (software) HTTP server, which then locates the requested content and returns it to the browser over HTTP. (If the server cannot locate the requested page, it responds with a 404 error.)

### Performance Optimization
Improving performance in applications and websites involves various strategies beyond pagination. Here are some additional techniques and best practices to enhance performance:

1. **Caching:**
   - Implement server-side caching to store frequently accessed data and reduce the need to regenerate content for every request.
   - Use client-side caching to store static assets (such as images, stylesheets, and scripts) in the user's browser, reducing the need to download them with each page load.

2. **Content Delivery Network (CDN):**
   - Utilize a CDN to distribute static assets across multiple servers geographically closer to users, reducing latency and improving loading times.

3. **Minification and Compression:**
   - Minify and compress CSS, JavaScript, and other files to reduce their size, improving download times. Tools like UglifyJS and Terser can be used for JavaScript, while CSSNano and csso are common for CSS.

4. **Image Optimization:**
   - Optimize images by compressing them without compromising quality. Tools like ImageOptim, TinyPNG, and ImageMagick can help reduce image file sizes.

5. **Lazy Loading:**
   - Implement lazy loading for images, especially for those below the fold. This defers the loading of images until they are about to be displayed, improving initial page load times.

6. **Asynchronous Loading:**
   - Load non-essential scripts asynchronously to prevent them from blocking the rendering of the page. The `async` and `defer` attributes in the script tag can be used for this purpose.

7. **Database Optimization:**
   - Optimize database queries to reduce response times. Use indexes, limit the number of queries, and consider database caching where applicable.

8. **Code Splitting:**
   - Employ code splitting techniques to break down large bundles of code into smaller, more manageable chunks. This allows for more efficient loading of only the necessary code for a specific page.

9. **HTTP/2 and HTTP/3:**
   - Utilize the latest versions of the HTTP protocol, such as HTTP/2 and HTTP/3, which offer performance improvements over earlier versions by allowing multiple requests to be multiplexed over a single connection.

10. **Responsive Design:**
    - Design responsive layouts that adapt to different screen sizes and devices. This not only improves the user experience but also ensures that users download only the resources needed for their specific device.

11. **Prefetching and Preloading:**
    - Use prefetching and preloading techniques to fetch and cache resources that are likely to be needed in the future. This can be done with the `<link rel="prefetch">` and `<link rel="preload">` HTML tags.

12. **Reduce Server Requests:**
    - Minimize the number of server requests by combining and optimizing files. For example, combine multiple CSS or JavaScript files into a single file.

By incorporating these techniques into your application or website, you can significantly enhance its performance, providing users with a faster and more efficient experience. It's often beneficial to use a combination of these strategies based on the specific needs and characteristics of your project.