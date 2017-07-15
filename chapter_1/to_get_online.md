# To Get Online & Internet

- To get online you need to be subscriped with an internet service provider or ISP for short
- htis isp handle assigning you a unique ip address for your machine, along with connecting you with internet.

- in you home you might have a wireless network, or at work you can have a network for inside office, this network might be connected with another bigger network that connect all offices in your company together, adn the company network can be connected to anther bigger network and so on until we have one huge network that connect Billions of devices accross world together. this huge network is called internet

## IP Adress Role

Internet is based on TCP/IP protocols, which mean that every node/machine on this network need to have a unique IP address, so when ever a mchaine want tp send a request to another, it need to send request addressed to the machine IP.

192.168.1.* 

all 4 parts can be anything from [1-255].
localnetworks are usually starting with "192.168.1.1" and last digit increase everytime a new computer connects to this network.

## What is Ports

every computer have over 50,000 port avaliable for any application to use.

imagin you have 2 applications on your PC that needs to connect with a remote server

1. facebook application
1. whatsapp application

now whenever the server will want to send you a message it will send it to your ip, 

**but how can it send it to a specfic application on your machine ?**

thats the function of **ports**, every application that expects to recieve a message from remote origin it needs to register it self on a specific port on your machines, so that when ever a remote origin wants to connect to this application it send request to that specfic port on your machine.

PROTOCOL://[YOU IP]:[APP PORT] *Tip: Common Protocols can be "Http, Https, FTP"*

lets assume facebook app will in our example will listen to port 8000, and whatsapp will listen on 9000,

now when the fb server will want to connect to you it will send message to yourip:8000

any application that Listen on a Specific port and wait for remote clients is named a "Server application"

- for example you can install a web server on your machine
- this webserver will be listening on PORT 80
- Now if any browser try to connect to you on port 80 the webserver you have on your machine will responde.

*Tip* in web browsers you can specify the port you want after the domain namin example

- http://mysite.com:80/  --> this will connect to mysite.com on port 80
- http://mysite.com:2082/  --> this will connect to mysite.com on port 2082 (cpanels of most websites are on 209822)
- ftp://mysite.com:21/  --> ftp servers are usually listening on port 21. and this url should open ftp connection with this remote site inside your browser 

example i have a nodejs server overhere, i will instruct this app to use port 3000.

now when i open browser and go to 127.0.0.1:3000 this server will answer me
[nodejs server on port 3000](./assets/server3000.png);

lets open nodejs and change port to 8000, and now try to connect to localhost:3000  again it will fail,
try to go to localhost:8000 it will work :).
[nodejs server on port 8000](./assets/server8000.png);

This is how you specify the port inside a browser.

## What defines a client

* A client is the one who initiate/start the connection.
* He ask the server for information, and the server reply to him
* This is the part that the user control
* a Client can Be a Browser, a Mobile Application, or a Javscript Application
* All Frontend communication is done using HTTP protocols.

## What defines a Server

* Server is a machine that has a server application running and listening at a specefic port.
* Webservers default port is 80
* a Web server main join is to wait and listen on port 80 waitting for a client to try to connect to him once connection established, server parse the request from the client, calculate the response, send it back to the client and terminate connection
* A server can also connect to another server, in such case such Server will act as a Client that connect to other Server to get information from
  * Database Server : your web server will connect to it, send querys, retreive data, then close connection at end.

### HTTP/Web Servers are Stateless

Servers Are stateless by default, which mean that they dont have a state. which mean they done hold variables that hold data !
Every request the client send to a server must include all information required for server to be able to responde

So What do you mean by stateless ?

Imagin This story

1. You went to page mysite.com/login --> server sent you back html for login page.
2. you enter username and password --> server said your username and password is correct and sent you a dashboard page html
3. you refresh page.. now should server still send you the dashboard ? or he dont know who you are any more ?

The answer is since its Stateless he have no clue who you are any more !!

Every request is independent, its not like a chain, All requests need to contain all information so that server can identify who is the client, this is done using **Cookies**

## Cookies and Sessions
Cookies are a small files that the server ask the browser to save and send it back with every future request.
So in above story, after you login for example, the server will return in the Response a small Cookie that contain forexample "user\_session=123". from now on, all requests sent by client will contain this cookie. and the server will use this user\_session variable to find a file that it keep server side and contain all your information "user_id, username, password whatever the server wants.

### Security Tip:
So for security wise, the cookie will only contain a pointer to a file, and all session data will be save on a file on the server so that it stay safe.
And for further security, these cookies are usually encrypted using a key, so that if a Hacked tried to change the data inside the cookie the whole cookie become unreadable. also most servers will create long hard unique names for the session files, so that hackers even if they could somehow change data inside cookie they cannot guess session id of another user and impersonate him. this was called **Session hijacking** in history, now most servers and browsers are aware of such vulnarability and use methods mentioned above to protect themself.