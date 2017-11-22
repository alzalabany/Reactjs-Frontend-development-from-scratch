# Internet Story

## Definitions

## HTTP Request

open up Google Chrome &gt; Development tools &gt; Network, and go to anywebsite, you will see lots of HTTP request flying around, select any request in the list.

### Header

[request](./assets/chrome.png)  
in Headers tab, you can see General, and Request Headers, these are headers that the browser automaticly defined for you and sent with the request to the server.

the paramaterms that matters with you as a frontend developer are.

* General
  * Request URL: is this where the request is going
  * Method: Type of request as mentioned before
  * Remote Address: this is the value the browser got after asking the DNS server "see i told you in the story :\)"
* Request Headers
  * Accept: this is very important variable, in this the browser try to tell the server : hey these are filetypes i can open, so please send me something i understand.
    * in above picture, it accept text, html, xhtml, & xml.
  * Cookie: this is how the server remembers you ! more on that on [Chapter 4 cookies section](../chapter_4/cookies-sessions.md)
  * and some more information like Host, and User-Agent "browser name"

All these are supposed to guid the server so that the server can understand  
1. who he is talking to "host, cookie"  
2. what do you want from him. "url"  
3. what is format you prefer "content-type"

### Request Body

the request body contain data that you send in a form for example,

## Response

Servers responde to your request in "text Strings", the content-type in the response header instruct your browsers/client how he can read and present such text.

### Header

[request](./assets/response.png)  
after the server get your request, he process it and send you back request  
the request body contain data that you send in a form for example,

* content-type : this tell the browser what are the type of the data in the **response.body**, a well configured server and a smart web application should always set this paramter, and should always respect the **content-accept in the Request.header**. this is called **Content Negotiation** more about this later

* and status code:



