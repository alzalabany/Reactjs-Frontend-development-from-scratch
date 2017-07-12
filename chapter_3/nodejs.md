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

save and run this should output
```shell
Momens-MacBook-Air:course-workspace momen$ node ./firstnode.js name=momen age=32
Hello momen, you are 32 years old awesome !
```

***Now go and explore!***, anything you can run inside google chrome’s console, you can run inside node,

So go explore and try to write few terminal apps that you need !, if you want to know how something is done don’t be afraid to ask Google !, like if you want to write to disk file this will lead you to use a library named “fs” this is nodejs library to manipulate file systems, or node’s “request” which let you fetch remote content.