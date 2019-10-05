# Backend Development Notes

## Sources
    - s1. Node Design Patterns, 2nd Edition, Mario Casciaro, Luciano Mammino
    - s2. Patterns of Enterprise Application Architecture, Martin Fowler
    - s3. Web Development with Node and Express, Ethan Brown

## Programming

### Programming > Patterns

**Microservice**
> In short, the microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource API. These services are built around business capabilities and independently deployable by fully automated deployment machinery. There is a bare minimum of centralized management of these services, which may be written in different programming languages and use different data storage technologies. - https://martinfowler.com/microservices/

### Programming > Concepts

**Virtual Machine**
> A virtual machine is a computer file, typically called an image, that behaves like an actual computer. In other words, creating a computer within a computer. It runs in a window, much like any other program, giving the end user the same experience on a virtual machine as they would have on the host operating system itself. The virtual machine is sandboxed from the rest of the system, meaning that the software inside a virtual machine can’t escape or tamper with the computer itself. This produces an ideal environment for testing other operating systems including beta releases, accessing virus-infected data, creating operating system backups, and running software or applications on operating systems they weren’t originally intended for. - https://azure.microsoft.com/en-us/overview/what-is-a-virtual-machine/

## Programming > Terms

**Pattern**
> There’s no generally accepted definition of a pattern, but perhaps the best place to start is Christopher Alexander, an inspiration for many pattern enthusiasts: “Each pattern describes a problem which occurs over and over again in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice” [Alexander et al.]. - s2


**Throughput**
> Throughput is how much stuff you can do in a given amount of time. If you’re timing the copying of a file, throughput might be measured in bytes per second. For enterprise applications a typical measure is transactions per second
(tps), but the problem is that this depends on the complexity of your transaction. For your particular system you should pick a common set of transactions. - s2

**Scalability**
> Scalability is a measure of how adding resources (usually hardware) affects performance. A scalable system is one that allows you to add hardware and get a commensurate performance improvement, such as doubling how many servers you have to double your throughput. Vertical scalability, or scaling up, means adding more power to a single server, such as more memory. Horizontal scalability, or scaling out, means adding more servers. - s2

## Programming >  Principles

**DRY**
Don't Repeat Yourself

## API

>  API is an application programming interface. It is a set of rules that allow programs to talk to each other. The developer creates the API on the server and allows the client to talk to it. - https://www.smashingmagazine.com/2018/01/understanding-using-rest-api/

### API > Rest

> REST stands for REpresentational State Transfer. It means when a RESTful API is called, the server will transfer to the client a representation of the state of the requested resource. - https://medium.com/extend/what-is-rest-a-simple-explanation-for-beginners-part-1-introduction-b4a072f8740f


## Git

**.gitignore**
> If you create a file in your repository named .gitignore, Git uses it to determine which files and directories to ignore, before you make a commit. A .gitignore file should be committed into your repository, in order to share the ignore rules with any other users that clone the repository. - https://help.github.com/en/articles/ignoring-files
```git
# ignore packages installed by npm
node_modules

# put any other files you don't want to check in here,
# such as .DS_Store (OSX), *.bak, etc.
```

## Web

### Web > Tools

**curl**

> command line tool and library for transferring data with URLs - https://curl.haxx.se/
> API documentations are normally written with reference to cURL. If you understand how to use cURL, you’ll have no problems understanding API documentations. - https://www.smashingmagazine.com/2018/01/understanding-using-rest-api/

```terminal
$ curl -H "Content-Type: application/json" https://api.github.com -v

* Rebuilt URL to: https://api.github.com/
*   Trying 192.30.253.116...
* TCP_NODELAY set
* Connected to api.github.com (192.30.253.116) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
* Cipher selection: ALL:!EXPORT:!EXPORT40:!EXPORT56:!aNULL:!LOW:!RC4:@STRENGTH
* successfully set certificate verify locations:
*   CAfile: /etc/ssl/cert.pem
  CApath: none
* TLSv1.2 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (IN), TLS handshake, Server key exchange (12):
* TLSv1.2 (IN), TLS handshake, Server finished (14):
* TLSv1.2 (OUT), TLS handshake, Client key exchange (16):
* TLSv1.2 (OUT), TLS change cipher, Client hello (1):
* TLSv1.2 (OUT), TLS handshake, Finished (20):
* TLSv1.2 (IN), TLS change cipher, Client hello (1):
* TLSv1.2 (IN), TLS handshake, Finished (20):
* SSL connection using TLSv1.2 / ECDHE-RSA-AES128-GCM-SHA256
* ALPN, server accepted to use http/1.1
* Server certificate:
*  subject: C=US; ST=California; L=San Francisco; O=GitHub, Inc.; CN=*.github.com
*  start date: Jul  8 00:00:00 2019 GMT
*  expire date: Jul 16 12:00:00 2020 GMT
*  subjectAltName: host "api.github.com" matched cert's "*.github.com"
*  issuer: C=US; O=DigiCert Inc; OU=www.digicert.com; CN=DigiCert SHA2 High Assurance Server CA
*  SSL certificate verify ok.
> GET / HTTP/1.1
> Host: api.github.com
> User-Agent: curl/7.54.0
> Accept: */*
> Content-Type: application/json
> 
< HTTP/1.1 200 OK
< Server: GitHub.com
< Date: Sun, 29 Sep 2019 14:03:05 GMT
< Content-Type: application/json; charset=utf-8
< Content-Length: 2165
< Status: 200 OK
< X-RateLimit-Limit: 60
< X-RateLimit-Remaining: 56
< X-RateLimit-Reset: 1569769385
< Cache-Control: public, max-age=60, s-maxage=60
< Vary: Accept
< ETag: "7dc470913f1fe9bb6c7355b50a0737bc"
< X-GitHub-Media-Type: github.v3; format=json
< Access-Control-Expose-Headers: ETag, Link, Location, Retry-After, X-GitHub-OTP, X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset, X-OAuth-Scopes, X-Accepted-OAuth-Scopes, X-Poll-Interval, X-GitHub-Media-Type
< Access-Control-Allow-Origin: *
< Strict-Transport-Security: max-age=31536000; includeSubdomains; preload
< X-Frame-Options: deny
< X-Content-Type-Options: nosniff
< X-XSS-Protection: 1; mode=block
< Referrer-Policy: origin-when-cross-origin, strict-origin-when-cross-origin
< Content-Security-Policy: default-src 'none'
< X-GitHub-Request-Id: 26AC:05B4:6F2CA2:1017C46:5D90B999
< 
{
  "current_user_url": "https://api.github.com/user",
  "current_user_authorizations_html_url": "https://github.com/settings/connections/applications{/client_id}",
  "authorizations_url": "https://api.github.com/authorizations",
  "code_search_url": "https://api.github.com/search/code?q={query}{&page,per_page,sort,order}",
  "commit_search_url": "https://api.github.com/search/commits?q={query}{&page,per_page,sort,order}",
  "emails_url": "https://api.github.com/user/emails",
  "emojis_url": "https://api.github.com/emojis",
  "events_url": "https://api.github.com/events",
  "feeds_url": "https://api.github.com/feeds",
  "followers_url": "https://api.github.com/user/followers",
  "following_url": "https://api.github.com/user/following{/target}",
  "gists_url": "https://api.github.com/gists{/gist_id}",
  "hub_url": "https://api.github.com/hub",
  "issue_search_url": "https://api.github.com/search/issues?q={query}{&page,per_page,sort,order}",
  "issues_url": "https://api.github.com/issues",
  "keys_url": "https://api.github.com/user/keys",
  "notifications_url": "https://api.github.com/notifications",
  "organization_repositories_url": "https://api.github.com/orgs/{org}/repos{?type,page,per_page,sort}",
  "organization_url": "https://api.github.com/orgs/{org}",
  "public_gists_url": "https://api.github.com/gists/public",
  "rate_limit_url": "https://api.github.com/rate_limit",
  "repository_url": "https://api.github.com/repos/{owner}/{repo}",
  "repository_search_url": "https://api.github.com/search/repositories?q={query}{&page,per_page,sort,order}",
  "current_user_repositories_url": "https://api.github.com/user/repos{?type,page,per_page,sort}",
  "starred_url": "https://api.github.com/user/starred{/owner}{/repo}",
  "starred_gists_url": "https://api.github.com/gists/starred",
  "team_url": "https://api.github.com/teams",
  "user_url": "https://api.github.com/users/{user}",
  "user_organizations_url": "https://api.github.com/user/orgs",
  "user_repositories_url": "https://api.github.com/users/{user}/repos{?type,page,per_page,sort}",
  "user_search_url": "https://api.github.com/search/users?q={query}{&page,per_page,sort,order}"
}

```

### Web > Terms

**static resources**
>  HTML and alogo image. These are called “static resources” because they don’t change (as opposed to, for example, a stock ticker: every time you reload the page, the stock prices change). - s3

**localhost**
> localhost, as the name implies, refers to the computer you’re on. This is a common alias for the IPv4 loopback address 127.0.0.1, or the IPv6 loopback address ::1. You will often see 127.0.0.1 used instead - s3

**slug**
> A ‘slug' is the part that comes at the very end of a URL, and refers to a specific page or post. For example, the slug for the URL above (https://prettylinks.com/2017/08/link-redirect-types/) is link-redirect-types. - https://prettylinks.com/2018/03/url-slugs/

### Web > HTTP

### Web > HTTP > Headers

> General headers - apply to both requests and responses, but with no relation to the data transmitted in the body.
> Request headers - contain more information about the resource to be fetched, or about the client requesting the resource.
> Response headers-  hold additional information about the response, like its location or about the server providing it.
> Entity headers - contain information about the body of the resource, like its content length or MIME type.
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers

**Content-Type**
> One common header that you need to set is the Content-Type of the response so that the client knows how to interpret the data the server sends in the body. For example, if you are sending down an HTML file to the client, you should set the Content-Type to text/html, which you can with the following code:
```javascript
response.setHeader(“Content-Type”, “text/html”);
```
- https://codeburst.io/all-about-http-in-node-js-and-3-best-ways-for-http-requests-in-web-development-6e5b6876c3a4


## Database

### Database > SQL (Structured Query Language)

## Javascript

### JavaScript > Patterns

**Callback Pattern**
> In JavaScript, a callback is a function that is passed as an argument to another function and is invoked with the result when the operation completes. - s1
>  Callbacks are functions that are invoked to propagate the result of an operation and this is exactly what we need when dealing with asynchronous operations. They do replace the use of the return instruction that always executes synchronously. - s1
```javascript
function add(a, b, callback) {
 callback(a + b);
}
add(1, 2, result => console.log('Result: ' + result));
>> Result: 3
```

```javascript
const fs = require('fs');

function readFile(filename, callback) {
    // you pass readFile a file name, and it gives you a callback with the data as the first param when it gets it
    fs.readFile(filename, 'utf8', (err, data) => {
      callback(data);
 });
}

function createFileReader(filename) {
  const listeners = [];
  // The callback we are passing to readFile is a function definition with a param of value, and a body that calls each listener
  readFile(filename, value => {
    listeners.forEach(listener => {
      listener(value)
     });
  });
  return {
    onDataReady: listener => {
      // pushes onto the listeners array one or more function definitions, which are invoked when readFile returns data
      listeners.push(listener)
      listeners.push(() => console.log('The file has returned its data.'))
    }
  };
}

// returns an object with a property called 'onDataReady'. 
const reader1 = createFileReader('data.txt');

// calls the 'onDataReady' property with a function definition as a parameter. This function definition gets pushed onto the list of listeners. Each of these listeners is invoked when the readFile returns data
reader1.onDataReady(data => {
  console.log(data)
});

>> {data from data.txt}
>> The file has returned its data.
```

### Javascript > ES6

**Const**
* Allows user to make constant variables. 
> const does not indicate that the assigned value will be constant, but that the binding with the value is constant. - s1
```javascript
const x = {};
x.name = 'John';
console.log(x.name)
>>  'John'
```

**Template Literals**
> The main benefits are that template literal syntax can interpolate variables or expressions using ${expression}
inside the string (this is the reason why this syntax is called “template”) and that a single string can finally be easily written in multiple lines.  - s1
```javascript
const name = 'John';
const greeting = `Hi, my name is ${name}`;
console.log(greeting);
>>  Hi, my name is John
```

**Let**
> Historically, JavaScript only offered function scope and global scope to control the lifetime
and the visibility of a variable. ES2015 introduces the let keyword to declare variables that respect the block
scope - s1
```javascript
if (false) {
 let x = "hello";
}
console.log(x);
>>  ReferenceError: x is not defined 
```

**Arrow Functions**
* Updated syntax for writing functions
> But there is another important feature to know about arrow functions: arrow functions are
bound to their lexical scope. This means that inside an arrow function the value of this is
the same as in the parent block. - s1
```javascript
function Person(name) {
 this.name = name;
 this.species = 'person'
}

Person.prototype.greet = function() {
  console.log(this);
  return 'Hi ' + this.name;
};

Person.prototype.waitAndGreet = function() {
  setTimeout(function cb() {
    console.log(this);
    return 'Hi ' + this.name;
  }, 500)
};

Person.prototype.waitAndGreetTwo = function() {
  setTimeout(() => {
    console.log(this);
    return 'Hi ' + this.name;
  }, 500)
};

const person = new Person('John');
person.greet();
>> Person { name: 'John', species: 'person' }
>> 'Hi John'

person.waitAndGreet();
>> undefined
>> Timeout {
  _called: true,
  _idleTimeout: 500,
  
person.waitAndGreetTwo();  
>> undefined
>> Person { name: 'John', species: 'person' }
  
```

**Classes**
- super
- constructor
- class
- extends
- static
```javascript
class Person {
 constructor (name, surname, age) {
 this.name = name;
 this.surname = surname;
 this.age = age;
 }
 getFullName () {
 return this.name + ' ' + this.surname;
 }
 static older (person1, person2) {
 return (person1.age >= person2.age) ? person1 : person2;
 }
}

class PersonWithMiddlename extends Person {
 constructor (name, middlename, surname, age) {
 super(name, surname, age);
 this.middlename = middlename;
 }
 getFullName () {
   return this.name + ' ' + this.middlename + ' ' + this.surname;
 }
}

const person1 = new Person('John', 'Smith', 47);
const person3 = new PersonWithMiddlename('Juan', 'James', 'Smythe', 49);

person3.getFullName()
>> 'Juan James Smythe'

PersonWithMiddlename.older(person3, person1).name
>> Juan
```


**Enhanced object literals**
- get
- set
>  This
syntax offers a shorthand to assign variables and functions as members of the object, allows
us to define computed member names at creation time, and also handy setter and getter
methods. - s1
```javascript
const person = {
  name : 'George',
  surname : 'Boole',
  greet(x) {
    return `${x}, ${this.name}`;
  },
  get fullname () {
    return this.name + ' ' + this.surname;
  },
  set fullname (fullname) {
    let parts = fullname.split(' ');
    this.name = parts[0];
    this.surname = parts[1];
  }
};

console.log(person.fullname);
 >> "George Boole"
console.log(person.fullname = 'Alan Turing'); 
>> "Alan Turing"
console.log(person.name); 
>> "Alan"
person.greet('Howdy')
>> "Howdy, Alan"
```

### Javascript > Node

### JavaScript > Node > npm

**npm**
>  short for Node Package Manager, is two things: first and foremost, it is an online repository for the publishing of open-source Node.js projects; second, it is a command-line utility for interacting with said repository that aids in package installation, version management, and dependency management. - https://nodejs.org/en/knowledge/getting-started/npm/what-is-npm/

**npm install --save**
npm install --save express
> If you specify the --save flag, it will update the package.json file - s3

### JavaScript > Node > npm > dotenv
> A common application level tool is dotenv which allows us to load environment variables from a file named .env. - https://codeburst.io/process-env-what-it-is-and-why-when-how-to-use-it-effectively-505d0b2831e7
```javascript
const dotenv = require('dotenv');
dotenv.config();

// in .env file
NODE_ENV=development
PORT=3001
```

### JavaScript > Node > Libraries

### JavaScript > Node > Libraries > path

**extname**
```javascript
path.extname('index.html');

>> '.html'
```

### JavaScript > Node > Libraries > process

**env**
> The process.env global variable is injected by the Node at runtime for your application to use and it represents the state of the system environment your application is in when it starts. For example, if the system has a PATH variable set, this will be made accessible to you through process.env.PATH which you can use to check where binaries are located and make external calls to them if required. - https://codeburst.io/process-env-what-it-is-and-why-when-how-to-use-it-effectively-505d0b2831e7
Can be called from the terminal:
```terminal
PORT=8626 NODE_ENV=development node server.js
```
or from a .env file using the dotenv npm package.

**nextTick()**
>  which defers the execution of a function until the next pass of the event loop. Its functioning is very simple; it takes a callback as an argument and pushes it to the top of the event queue, in front of any pending I/O event, and returns immediately. The callback will then be invoked as soon as the event loop runs again. - s1
``` javascript
const fs = require('fs');

function readFile(filename, callback) {
    fs.readFile(filename, 'utf8', (err, data) => {
      process.nextTick(() => callback(data));
 });
}

readFile('data.txt', data => {
  console.log(data)
});
```

**argv**
argument vector
> returns an array containing the command line arguments passed when the Node.js process was launched. The first element will be process.execPath. The second element will be the path to the JavaScript file being executed. The remaining elements will be any additional command line arguments. - https://nodejs.org/api/process.html#process_process_argv

```javascript
// from terminal
node example.js -a -b -c

// in example.js
console.log(process.argv)

>> [
  '/usr/bin/node',
  '/some/path/to/example.js',
  '-a',
  '-b',
  '-c'
]
```
> code from https://alligator.io/nodejs/command-line-arguments-node-scripts/

### JavaScript > Node > Libraries > http

**createServer**
> takes a callback and returns an HTTP server. On each client request, the callback is passed in two arguments — the incoming request stream and an outgoing server response stream. - https://codeburst.io/all-about-http-in-node-js-and-3-best-ways-for-http-requests-in-web-development-6e5b6876c3a4
```javascript
const http = require('http');
const port = 3000;

const requestHandler = (request, response) => {
  console.log(request.url)
  response.end('Hello Node.js Server!')
}

const server = http.createServer(requestHandler)

server.listen(port, (err) => {
  if (err) {
    return console.log('something bad happened', err)
  }
  console.log(`server is listening on ${port}`)
})
```
> code from https://blog.risingstack.com/your-first-node-js-http-server/


### JavaScript > Node > Libraries > url

**parse**
```javascript
const urlParse = require('url').parse;
const parsedUrl = urlParse('http://www.example.com/stuff?cats=3');
console.log(parsedUrl)

>>  Url {
  protocol: 'http:',
  slashes: true,
  auth: null,
  host: 'www.example.com',
  port: null,
  hostname: 'www.example.com',
  hash: null,
  search: '?cats=3',
  query: 'cats=3',
  pathname: '/stuff',
  path: '/stuff?cats=3',
  href: 'http://www.example.com/stuff?cats=3' }
```

### JavaScript > Node > Antipatterns

**callback hell/pyramid of doom**
> The situation where the abundance of closures and in-place callback definitions transform the code into an unreadable and unmanageable blob - s1
> The most evident problem with code such as the preceding snippet, is the poor readability. Due to the nesting being too deep, it's almost impossible to keep track of where a function ends and where another one begins - s1
```javascript
asyncFoo( err => {
 asyncBar( err => {
   asyncFooBar( err => {
     //...
   });
 });
});
```

### JavaScript > Node > Patterns

**Module System**
> Modules are the bricks for structuring non-trivial applications, but also the main mechanism to enforce information hiding by keeping private all the functions and variables that are not explicitly marked to be exported.  - s1

> Node.js uses the concept of a module as a fundamental means to structure the code of a program. . It is the building block for creating applications and reusable libraries called packages (a package is also frequently referred to as a module since, usually, it has one single module as an entry point).  - s1

> The essential concept to remember is that everything inside a module is private unless it's assigned to the module.exports variable. The content of this variable is then cached and returned when the module is loaded using require(). - s1

### JavaScript > Node > Gotchas

>  Throwing inside an asynchronous callback will cause the exception to jump up to the event loop and never be propagated to the next callback. In Node.js, this is an unrecoverable state and the application will simply shut down printing the error to the stderr interface. - s1

### Javascript > Node > Concepts

**event-driven programming**
> The core philosophy behind Node is that of event-driven programming.What that means for you, the programmer, is that you have to understand what events are available to you and how to respond to them. Many people are introduced to event-driven programming by implementing a user interface: the user clicks on something, and you handle the “click event.” - s3

**the app is the web server**
> If you’ve ever built a static HTML website before, or are coming from a PHP or ASP background, you’re probably used to the idea of the web server (Apache or IIS, for example) serving your static files so that a browser can view them over the network. Node offers a different paradigm than that of a traditional web server: the app that you write is the web server. Node simply provides the framework for you to build a web server.- s3

**Asynchronous vs. Synchronous**
* A synchronous callback
``` javascript
function add(a, b, callback) {
 callback(a + b);
}

console.log('before');
add(1, 2, result => console.log('Result: ' + result));
console.log('after');

>> before
>> Result: 3
>> after
```
* An asynchronous callback
``` javascript
function additionAsync(a, b, callback) {
 setTimeout(() => callback(a + b), 100);
}
console.log('before');
additionAsync(1, 2, result => console.log('Result: ' + result));
console.log('after');

>> before
>> after
>> Result: 3
```
> Since setTimeout() triggers an asynchronous operation, it will not wait for the callback to
be executed, but instead, it returns immediately, giving the control back to
additionAsync(), and then back to its caller. This property in Node.js is crucial, as it gives
control back to the event loop as soon as an asynchronous request is sent, thus allowing a
new event from the queue to be processed.

### Javascript > Node > Features

**__dirname**
> \_\_dirname will resolve to the directory the executing script resides in. So if your script resides in /home/sites/app.js, \_\_dirname will resolve to /home/sites. It’s a good idea to use this handy global whenever possible. Failing to do so can cause hard-to-diagnose errors if you run your app from a different directory. - s3
```javascript
fs.readFile(__dirname + '/cat.txt', function(err, data) {
  if (err) {
    console.log(err)
  } else {
     onsole.log(data)
  }
```


### Javascript > Vanilla

### Javascript > Vanilla > Concepts

**Expression**
> An expression is any valid unit of code that resolves to a value. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators
> Every syntactically valid expression resolves to some value but conceptually, there are two types of expressions: with side effects (for example: those that assign value to a variable) and those that in some sense evaluate and therefore resolve to a value. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators

**Function Expression**
Assigning a function definition to a value
```javascript
var sayHi = function() {
    console.log("Hello, World!");
};

sayHi(); 

>>  "Hello, World!"
```



**Falsey**
- false
- undefined
- null
- 0
- NaN
- the empty string ("")
All other values, including all objects, evaluate to true when passed to a conditional statement. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling

** Lexical Scoping **
> defines how variable names are resolved in nested functions: inner functions contain the scope of parent functions even if the parent function has returned. - https://stackoverflow.com/questions/1047454/what-is-lexical-scope

**Closures**
> closure is the combination of a function and the lexical environment within which that function was declared.
> Closures are useful because they let you associate some data (the lexical environment) with a function that operates on that data. This has obvious parallels to object-oriented programming, where objects allow us to associate some data (the object's properties) with one or more methods. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures
> With closures, we can in fact reference the environment in which a function was created; we can always maintain the context in which the asynchronous operation was requested, no matter when or where its callback is invoked. - s1
```javascript
function makeFunc() {
  var name = 'Mozilla';
  function displayName() {
    console.log(name);
  }
  return displayName;
}

var myFunc = makeFunc();
myFunc();
>> Mozilla
```

### JavaScript > Vanilla > Features

**setTimeOut**
Can be used to simulate an asynchronous event
```javascript
setTimeout(function(){
  console.log('I waited'), 1000);
}
>> I waited
```

**throw**
> The throw statement throws a user-defined exception. Execution of the current function will stop (the statements after throw won't be executed), and control will be passed to the first catch block in the call stack. If no catch block exists among caller functions, the program will terminate. -https://developer.mozilla.org/enUS/docs/Web/JavaScript/Reference/Statements/throw
```javacript
function getRectArea(width, height) {
  if (isNaN(width) || isNaN(height)) {
    throw new Error("Parameter is not a number!");
  }
}

try {
  getRectArea(3, 'A');
}
catch(e) {
  console.error(e);
}

>> Error: Parameter is not a number!
```


**this**
> refer to the current object. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators
```javacript
const Person = function(name, favMusicGenre) {
  this.name = name;
  this.favMusicGenre = favMusicGenre;

  this.greet = function() {
    console.log(this);
    return `Hi, I'm ${this.name} and I like ${favMusicGenre} music.`;
  }
}

const timmy = new Person('Timmy', 'Rock');
timmy.greet();

>> Person { name: 'Timmy', favMusicGenre: 'Rock', greet: [Function] }
>> 'Hi, I\'m Timmy and I like Rock music.'
```

**try...catch**
> marks a block of statements to try, and specifies a response, should an exception be thrown. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch
```javacript
try {
  nonExistentFunction();
}
catch(error) {
  console.error(error);
}

>> ReferenceError: nonExistentFunction is not defined
```

