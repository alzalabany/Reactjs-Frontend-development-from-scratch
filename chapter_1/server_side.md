## Server Side {#server-side}

* Deliver our front end code.
* Get data content
* databases and persistance
* hosting and webservers setup
* age of api's
  * pros and cons of api based backend\#
  
  The server side (also known as the backend) is responsible for handling and responding to clients' requests.
  When the client requests a certain webpage, the server responsible for this webpage responds with the requested webpage. Communication with servers is mainly done through HTTP requests, in which the client sends a request and the server responds to this request and then the connection between them is closed. In such case the server can no longer contact the client, as the connection is no longer available.
  The server Side consists of three main components:
  * The server: Any computer that receives the requests.
  * The application: The Application running on the server that listens for requests, retrieves information from the database, and sends responses.
  * The Database: Databases are used to organize and persist data.

  Hosting allows making websites and/or applications accessible on the internet. It's usually done through a internet hosting service, which allows you to 'rent a server' or a piece of it to host your app.(We discuss this in details in chapter 2). It suffices to say that internet hosting services usually removes the hustle of setting up the server.
  
  Most of servers are API based, which mostly means REST API (also described as RESTful). REST (
Representational state transfer) API is an architectural style defining a set of constraints to make the communication between the client and server uniform and stateless.
PROS:
* Great flexibility
* Lower maintenance costs
* High scalability
* Simplicity 

CONS:
* High bandwith usage.
* Higher latency (request processing times).
* Require too much work from the provider in defining and .supporting 