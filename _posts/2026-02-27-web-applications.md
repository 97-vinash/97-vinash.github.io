---
title: "LWM #2 - Web Application Fundamentals"
tags: [Learn With Me, Web, Web Applications, Fundamentals]
date: 2025-09-07
excerpt: Understanding web application architecture is essential for security testing—from front-end components like HTML and JavaScript to back-end servers, databases, and APIs. Each layer introduces potential vulnerabilities like XSS and CSRF. By learning how clients interact with servers through GET/POST requests, how different databases store data, and how to probe with tools like cURL, you'll know exactly where to look for weaknesses—and how to research public exploits when you find them.
---

## web-apps
Web apps are interactive and changes based on client input.
These apps are also application like Operating System applications but, they run on the server and shows the result on your browser.

**To Pentest these Applications:-**  
-> Start by testing front-end components (html, css, js) to find -> Sensitive Data Exposure & XSS.  
-> Then move to interaction b/w browser and server to find the technologies the web-server uses.  
-> then look for flaws in those technologies. (Test for both authenticated and unauthenticated users)

**NOTE:**  
-Front-end components gets executed or interpreted on client-side (browser).  
-Back-end components gets compiled and executed at server-side.

**Different Web-App Infrastructures**  
-> One server (integrated DB server)  
-> Many servers & 1 DB server  
-> Many servers & Many DB servers

**Components in a Web-App**  
-> Client  
-> Server  
-> Services (microservices)  
-> Functions (serverless)

* A server deployed in CGI mode can run backend code.
eg -> GET /form.cgi?name=John

**Microservices** - independent single task oriented programs, they interact with each other to get the final desired goal,  
**Serverless Application** is when an app uses a cloud service provider like AWS to host their app on their server & manage it for them.

**4 Main Components in a Backend**  
^ Back-end server (hardware + OS)  
^ Web-servers (nginx, apache, iis)  
^ Databases (relational databases - *MySQL*, *Oracle*, *PostgreSQL*. non-relational databases include *NoSQL* and *MongoDB*.)  
^ Frameworks - *Laravel* (PHP), *ASP.NET* (C#), *Spring* (Java), *Django* (Python), and *Express* (NodeJS JavaScript).  
  
**APIs** - application programming interfaces helps computers or programs to connect and interact with each other,
API offers many services and when a program or programmer uses this services it said that we are "calling" that API service. (more on wiki -> API)

Frontend source code reviewing for vulnerabilities is a part of **WHITEBOX pentesting**.  
- Html files consists of html elements these elements can be included inside other elements, but the main element or the outer most element should be a <html></html> elemet, that consists all other elements on that page.  
- Both starting and ending tags with everything inside is a single element.  
- DOM is an API, independent of platform & laguage, It represents a document like html or xml as a tree and where each node is an object representing a part of the document. (for more -> DOM on wiki)  
- With Ajax, web applications(on the client side) can send and retrieve data from a server asynchronously (in the background) without interfering with the display and behaviour of the existing page.  
  
* Check source-code of the page. (Ctrl + U)  
* Check source-code for HTML injection.  
* Check for XSS injection as well in same field as html.  
* CSRF attack occurs when a malicious web site, email or program tricks an authenticated user's web browser into performing an unwanted action on a trusted site.  
  
Stack Combinations for Serevers!  
- **LAMP** - Linux, Apache, MySQL, PHP  
- **WAMP** - Windows, Apache, MySQL, PHP  
- **WINS** - Windows, IIS, .NET, SQL Server  
- **MAMP** - macOS, Apache, MySQL, PHP  
- **XAMPP** - Cross-Platform, Apache, MySQL, PHP/PERL  
  
**Apache** AKA **"httpd"** is open-source web-server. used in approx 40% of the internet.  
**NGINX** is also open source and used in almost 30% of the internet.  
**Microsoft IIS** -> used 15% and good for active directory authentication.  
  
**Code**                                **Description**  
*Successful responses*	
200 OK	                                The request has succeeded  
  
*Redirection messages*	
301 Moved Permanently	                The URL of the requested resource has been changed permanently  
302 Found	                            The URL of the requested resource has been changed temporarily  
  
*Client error responses*	
400 Bad Request	                        The server could not understand the request due to invalid syntax  
401 Unauthorized	                    Unauthenticated attempt to access page  
403 Forbidden	                        The client does not have access rights to the content  
404 Not Found	                        The server can not find the requested resource  
405 Method Not Allowed	                The request method is known by the server but has been disabled and cannot be used  
408 Request Timeout	                    This response is sent on an idle connection by some servers, even without any previous request by the client  

*Server error responses*	
500 Internal Server Error	            The server has encountered a situation it doesn't know how to handle  
502 Bad Gateway	                        The server, while working as a gateway to get a response needed to handle the request, received an invalid response  
504 Gateway Timeout	                    The server is acting as a gateway and cannot get a response in time  
  
  
- curl -I (for headers)
- curl (for source code)

* HTTP code 201 means "created", when you try to create to add something new on the server and its successful its shows code 201.

* Databases in back-end uses Relational and Non-Relational Databases to store Data.
* Relational stores data in table format.
* Non-Relational stores data in different formats like-
Key-Value
Document-Based
Wide-Column
Graph

* Relational Databases include
- MySQL
- MSSQL
- Oracle
- PostgreSQL
- SQLite
- MariaDB
- Azure SQL
- Amazon Aurora

* Non-Relational Databases include
- NoSQL
- MongoDB
- ElasticSearch
- Apache Cassandra 
- Redis
- Neo4j
- couchDB
- Amazon DynamoDB

* on the back-end which has web-servers that hosts web-applications, we also use certain Frameworks for ease of development (so we don't have to build every functionality from scratch). eg - Laravel, Django, Express, Rails.

* Web APIs are used when you want to connect your front-end to interact with the backend. (send data to each other)

* Default method to send arguments to the backend is through GET / POST request. 
* GET requests are given directly in the url. 
* POST requests are in the body of the HTTP requests -> generally at the bottom.

* If we want to get some functionality of something for a website we use API and give GET req then the backend server there will process it and return the result in JSON or XML format.

* to enable use of API in a web-app, on the backend we have to follow API standards like SOAP and REST.
* in SOAP the request and response both are done in XML through HTTP requests.
* REST uses JSON, XML, x-www-form-urlencoded types to transfer data, 


*  Find the version of Web-application.
*  search for public exploits of that version on Google or these Databases.
- Exploit DB
- Rapid7 DB
- Vulnerability Lab
* First check for 8-10 high lvl vulnerability if not available go lower.
* Check what components they use like Plugins or APIs and then check for their public exploits the same way.
* 
