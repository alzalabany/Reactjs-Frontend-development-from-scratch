## NodeJS {#nodejs}

### What is Node.js ? {#what-is-node-js}

Node allow us to create command line tools open your terminal.Node.js is built on top of Chrome&#039;s JavaScript runtime;

Node.js uses an event-driven,

It’s has a non-blocking I/O model; just like JavaScript queue system. that makes it lightweight and efficient, and perfect for data-intensive real-time applications that can run across multiple devices “Mac, window, Mobiles!” think of it as a mini-version of Chrome; or as a JavaScript interpreter. It can run and execute any JavaScript code using directly from your terminal,

So finally, JavaScript developers are able to build more sophisticated applications that doesnot have to run inside a browser only, can create applications easily and so building fast and scalable network applications.

### Command line tools with node.js {#command-line-tools-with-node-js}

```bash
echo "console.log('hello world');" > firstnode.js;
node ./firstnode.js;
```

the following 2 commands will create a firstnode.js file with `console.log` statement inside it, then it will tell node to execute it, this will print “hello world” message on console . This is an example of a application that hold no state “stateless application”, node will execute this file then will end since there is nothing more to do!, you can also create “Statefull apps” that keep running and maintain its own internal state “like express applications !” more on that later but for now.

Congratulations you have written your first node application!

Lets extend this app so that it can become and let it echo back hello with your name !

Open vscode to end firstnode.js file
```bash
code ./firstnode.js;
```

so how can we create a NodeJS app and pass arguments to it ? what we want is
```c
code ./firstnode.js name=momen age=32
Hello momen, you are 32 years old awesome !
```

[**https://nodejs.org/api/process.html#process_process_argv**](https://nodejs.org/api/process.html) **-nodejs official documentation-**

these are times where platform documentation is your best friend, so according to docs lets edit our app and add following
```javascript
var args = {};

process.argv.forEach(function (val, index, array) {
  let parts = val.split('=');

  if(parts.length === 2 &&  !args[parts[0]])
    args[parts[0]] = parts[1];
});

console.log(`Hello ${args.name}, you are ${args.age} years old awesome !`);
```

save and run this should output &gt;

```shell
Momens-MacBook-Air:course-workspace momen$ node ./firstnode.js name=momen age=32
```

Hello momen, you are 32 years old awesome !

Now go and explore!, anything you can run inside google chrome’s console, you can run inside node,

So go explore and try to write few terminal apps that you need !, if you want to know how something is done don’t be afraid to ask Google !, like if you want to write to disk file this will lead you to use a library named “fs” this is nodejs library to manipulate file systems, or node’s “request” which let you fetch remote content.

### Create backend server with Express {#create-backend-server-with-express}

Okay enough with playing around we want to create something really useful, lets create a Web Server with nodejs !!

Node is so powerful it can even replace entire need for PHP or Apache! –100% wrong statement you will hear often, well I nodejs is powerful, but every new technology has its pros and cons. And definatly ruby and PHP are not going anywhere..-

Lets create our first Server: using “Express” [https://expressjs.com/](https://expressjs.com/).

Express is a thin layer on top of node, that allow you to create backend’s, Web applications, API’s, Resful servers, Microservices everything !.

Lets start our first Express project from our command line as usual.
```bash
Momens-Air:course-workspace momen$ mkdir node-server
Momens-Air:node-server momen$ echo “console.log(123);” > index.js
Momens-Air:node-server momen$ yarn add express
Momens-Air:course-workspace momen$ mkdir node-server
Momens-Air:course-workspace momen$ cd node-server
Momens-Air:node-server momen$ echo "console.log('hello');" > index.js
Momens-Air:node-server momen$ node ./index.js
hello
Momens-Air:node-server momen$ yarn add express
✨  Done in 41.28s.
Momens-Air:node-server momen$ code ./index.js
```

Okay, now yarn will add express to our node_modules folder inside node-server folder we just created,

Lets edit our index.js file now.
```javascript

const express = require('express');
const app = express();

app.get('/', function (req, res) {
  res.send("Hello world");
})

app.listen(8000, function () {
  console.log("Server started on http://localhost:8000!");
})
```

I hope this what we are doing here is:-

1.  import express library into variable we name it express
2.  create our app by calling `express()` we can pass any config we need to express function but for this simple server we just want default setting server, so we didn’t pass anything.
3.  `app.get(‘/’ …` line this tell the app that if a request where sent to the url / [the root path] call the function and give it 2 variables
    1.  req = request variable this will hold all information about the request sent from client browser to us
    2.  res = response variable this hold all information we will send back to the browser .


If you have read [HTTP and DNS](chapter_1/http_and_dns.md) you already understand that every Web http communication starts with a Client “browser in most cases” sending request to a server, and server responde back with response.

Lets run our 1<sup>st</sup> server and see what happen

```bash
Momens-MacBook-Air:node-server momen$ node ./index.js
Server started on http://localhost:8000!
```

Now open browser to http://localhost:8000
![Screen%20Shot%202017-07-11%20at%202.05.20%20PM.png](../assets/screen20shot202017-07-1120at202.png)

Awesome our server is running and it give us “hello world”

Now lets add another route to our server

app.get(&#039;/:name&#039;, function (req, res) {

res.send(&#039;Hello Mr. &#039;+req.params.name);

})

now this route will match if url has anything after the first / , and since we use “**:**” this way we are telling express to take whatever it find after first / and add it into “name” variable on the req.params object !

now append add following code to you index.js, and go back to your terminal.

First press Control+C , to terminate current node, then re-run node ./index.js to refresh server

![Screen%20Shot%202017-07-11%20at%202.12.08%20PM.png](../assets/screen20shot202017-07-1120at202.png)Momens-MacBook-Air:node-server momen$ node ./index.js

Example app listening on port http://localhost:8000!

^C

Momens-MacBook-Air:node-server momen$ node ./index.js

Example app listening on port http://localhost:8000!

Back to browser, refresh page to make sure Hello World page at

root route http://localhost:8000/ is still working,

Then go to [http://localhost:8000/momen](http://localhost:8000/momen) and see what happen.

Great ! now it greet us with name from url. Try to change url and

See how Express will always match url and echo the name you want.

Now lets Use the Stateful nature of NodeJs and add one last route /history/:name to our app

### Stateful NodeJs Server {#stateful-nodejs-server}

This is the final look of our server.

const express = require(&#039;express&#039;)

const app = express();

var names = []; // Note we added a new variable, this will hold all names that visited our server

app.get(&#039;/&#039;, function (req, res) {

res.send(&#039;Hello world&#039;);

})

app.get(&#039;/:name&#039;, function (req, res) {

res.send(&#039;Hello Mr. &#039;+req.params.name);

})

// This is the new route, it will echo our Greeting for you, and tell you who else visited

// This server since you started it!. –this is what is meant by stateful, that application can

// keep variables defined while its running, and can use this State to answer all requests.

app.get(&#039;/history/:name&#039;, function (req, res) {

res.send(

&#039;Hello Mr. &#039;+req.params.name + &#039;&lt;hr/&gt;&lt;h1&gt;history&lt;/h1&gt;&#039; + names.join(&#039;&lt;br/&gt;&#039;)

);

names.push(req.params.name+ &#039; : visited at &#039;+ new Date().toLocaleDateString(&#039;en-GB&#039;));

})

app.listen(8000, function () {

console.log(&#039;Example app listening on port http://localhost:8000!&#039;)

})

Now try to open your browser, and visit [http://localhost:8000/history/yourName](http://localhost:8000/history/yourName), then refresh or change yourName to anyother name and watch nodejs keep track of all visits inside “names” variable.

Try to stop server and rerun again and you will see that names variable is empty.

This is because NodeJS was alive, and kept all names inside the variable in its memory, but once you shutdown server, memory get cleared.

This is very useful when creating Backserver, this is something you cannot do with PHP for example because PHP is stateless.. which mean that PHP spin up, reply to every request, then die. It doesnot keep any state around, and only way to make PHP stateful is by using Cookies, or Sessions, which is client specific state but not Server Wide State.

This is one of the features I love most about Nodejs and one that you can Hack to solve many problems !

Continue Along with us To **Chapter 5 of this book, we will be creating and Advanced Express Statefull Server With Express And will show you how Powerful Stateful server Architecture can be.. and how easy and simple it is too !.**

**That’s enough as introduction to NodeJs, next lets talk about JavaScript Linters, and other Command line Tools that you will need to build a full Large Scale Applications with JavaScript**

Linters [eslint, .eslintrc, extends existent rules, ide plugins]