# Backend Development Notes

**TO LEARN**
- git rebase
- git fetch
- git as a graph
- memory leaks in JS
- cookies vs. sessions
- package-lock.json
- ssh
- kafka + node
- https://blog.risingstack.com/node-js-security-checklist/
- kubernetes
- base 64 encoding
- http vs https

## Sources
    - s1. Node Design Patterns, 2nd Edition, Mario Casciaro, Luciano Mammino
    - s2. Patterns of Enterprise Application Architecture, Martin Fowler
    - s3. Web Development with Node and Express, Ethan Brown
    - s4. Node.js 8 the Right Way, Jim R. Wilson
    - s5. JavaScript for Impatient Programmers, Dr. Axel Rauschmayer
    - s6. You Don't Know JS: Async & Performance, Kyle Simpson
    - s7. Eloquent JavaScript, Marijn Haverbeke
    - s8. Computer Systems: A Programmer's Perspective, 3rd Edition, Randal E. Bryant, Carnegie Mellon University

David R. O'Hallaron, Carnegie Mellon University

## Computing

**buses**
> Running throughout the system is a collection of electrical conduits calledbuses that carry bytes of information back and forth between the components. Buses are typically designed to transfer fixed-sized chunksof bytes known as words. The number of bytes in a word (theword size) is a fundamental system parameterthat varies across systems.  Most machines today have word sizes of either 4 bytes (32 bits) or 8 bytes (64bits). - s8

**I/O**
> Input/output (I/O) devices are the system’s connection to the external world.  Our example system has fourI/O devices: a keyboard and mouse for user input, a display for user output, and a disk drive (or simply disk)for long-term storage of data and programs. - s8


### Computing > Concepts



** process **
> A process is an executing (i.e., running) instance of a program. Processes are also frequently referred to as tasks. - http://www.linfo.org/process.html

** program / executable file **
> A program is an executable file that is held in storage. Storage refers to devices or media that can retain data for relatively long periods of time (e.g., years or even decades), such as hard disk drives (HDDs), optical disks and magnetic tape. This contrasts with memory, whose contents can be accessed (i.e., read and written to) at extremely high speeds but which are retained only temporarily (i.e., while in use or only as long as the power supply remains on).

An executable file is a binary file (i.e., a file at least part of which is not plain text) that has been compiled (i.e., converted using a special type of program called a compiler) from source code into machine machine code, which is a pattern of bytes that can be read directly by a central processing unit (CPU). Source code is the version of software as it is originally written (i.e., typed into a computer) by a human in plain text (i.e., human readable alphanumeric characters). A CPU is the main logic unit of a computer. - http://www.linfo.org/process.html

** shell **
> A shell is a program that provides the traditional, text-only user interface for Unix-like operating systems. Its primary function is to read commands that are typed into a console (i.e., an all-text display mode) or terminal window (an all-text window in a GUI) and then execute (i.e., run) them. A command is an instruction telling a computer to do something, such as start a program. - http://www.linfo.org/process.html

** PID **
> In Unix-like operating systems, each process is given a unique number, referred to as a process identification (PID), when it is created, and this number is used by the system to reference the process. Each process is guaranteed to have a unique PID, which is always a non-negative integer. - http://www.linfo.org/process.html

**thread**
> A thread is basically a single process that a program can use to complete tasks. Each thread can only do a single task at once: Task A --> Task B --> Task C. Each task will be run sequentially; a task has to complete before the next one can be started. - https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Concepts

**Virtual Machine**
> A virtual machine is a computer file, typically called an image, that behaves like an actual computer. In other words, creating a computer within a computer. It runs in a window, much like any other program, giving the end user the same experience on a virtual machine as they would have on the host operating system itself. The virtual machine is sandboxed from the rest of the system, meaning that the software inside a virtual machine can’t escape or tamper with the computer itself. This produces an ideal environment for testing other operating systems including beta releases, accessing virus-infected data, creating operating system backups, and running software or applications on operating systems they weren’t originally intended for. - https://azure.microsoft.com/en-us/overview/what-is-a-virtual-machine/

**protocol**
>  protocol is a convention or standard that controls or enables the connection, communication, and data transfer between computing endpoints. In its simplest form, a protocol can be defined as the rules governing the syntax, semantics, and synchronization of communication. Protocols may be implemented by hardware, software, or a combination of the two. At the lowest level, a protocol defines the behavior of a hardware connection. While protocols can vary greatly in purpose and sophistication, most specify one or more of the following properties:
- Detection of the underlying physical connection (wired or wireless), or the existence of the other endpoint or node
- Handshaking (dynamically setting parameters of a communications channel)
- Negotiation of various connection characteristics
- How to start and end a message
- How to format a message
- What to do with corrupted or improperly formatted messages (error correction)
- How to detect unexpected loss of the connection, and what to do next
- Termination of the session and or connection.

from https://en.wikibooks.org/wiki/Network_Plus_Certification/Technologies/Common_Protocols



## Programming

### Programming > Tools

### Programming > Tools > ssh

> SSH, or Secure Shell, is a remote administration protocol that allows users to control and modify their remote servers over the Internet. It uses cryptographic techniques to ensure that all communication to and from the remote server happens in an encrypted manner. It provides a mechanism for authenticating a remote user, transferring inputs from the client to the host, and relaying the output back to the client.It uses port 22 and communicate over TCP protocol.
The SSH command consists of 3 distinct parts:
ssh {user}@{host}
{user} represents the account you want to access.
{host} refers to the computer you want to access. This can be an IP Address or a domain name
ssh ubuntu@x.x.x.x or ssh ubuntu@test.com
- https://schh.medium.com/ssh-for-dummies-ea168e6ff547

**Steps to get set up**
> Step 1 : Generate the client’s keyPairs
> ssh-keygen -t rsa -b 2048 -C "client@example.com"
> The client’s public and private key will be stored in ssh/id_rsa.pub and ssh/id_rsa respectively
> Step 2 : The admin system should copy the client’s public key to the remote server in .ssh/authorized_keys file
> ssh-copy-id -f -i id_rsa.pub ubuntu@x.x.x.x
> Step 3 : The client can then connect to the remote server
> ssh ubuntu@x.x.x.x
- https://schh.medium.com/ssh-for-dummies-ea168e6ff547

### Programming > Tools > Nomad

> Running containers in production is tough. You don’t want to log into a machine and simply run a docker run or docker-compose up. Why not? Well, what happens if the containers die? How do you scale across several machines? Container orchestration solves this problem. Tools like Kubernetes, Swarm, Nomad, and ECS all help solve this problem, all in slightly different ways. The general idea is that you have “managers” who receive expected state. This state might be “I want to run two instances of my web app and expose port 80.” The managers then look at all of the machines in the cluster and delegate work to “worker” nodes. The managers watch for changes (such as a container quitting) and then work to make actual state reflect the expected state. - https://docs.docker.com/get-started/11_what_next/

### Programming > Tools > Homebrew

**homebrew**
> BSD UNIX, of which Darwin or OS X is a derivative, does not have a built-in package manager like aptitude, which is why Homebrew calls itself the “missing package manager.” Homebrew is one of several package managers for OS X, including MacPorts and Fink. Most of the popular UNIX software packages are available to be installed through Homebrew and those that aren't can be made available through some configuration in Ruby. - https://www.quora.com/What-is-Homebrew-for-macOS

### Programming > Tools > Docker

#### Programming > Tools > Docker > Defintions

**docker**
> Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. - https://aws.amazon.com/docker/

**Dockerfile**
>  A Dockerfile is simply a text-based script of instructions that is used to create a container image. - https://docs.docker.com/get-started/02_our_app/

**container**
> Simply put, a container is simply another process on your machine that has been isolated from all other processes on the host machine. - https://docs.docker.com/get-started/

**image**
> A Docker image is a private filesystem, just for your container. It provides all the files and code your container will need. - https://hub.docker.com/?overlay=onboarding

> When running a container, it uses an isolated filesystem. This custom filesystem is provided by a container image. Since the image contains the container’s filesystem, it must contain everything needed to run an application - all dependencies, configuration, scripts, binaries, etc. The image also contains other configuration for the container, such as environment variables, a default command to run, and other metadata. - https://docs.docker.com/get-started/

**volume**
> Volumes are the preferred mechanism for persisting data generated by and used by Docker containers. - https://docs.docker.com/storage/volumes/

> Volumes provide the ability to connect specific filesystem paths of the container back to the host machine. If a directory in the container is mounted, changes in that directory are also seen on the host machine. If we mount that same directory across container restarts, we’d see the same files. - https://docs.docker.com/get-started/05_persisting_data/

> Create a volume by using the docker volume create command.
```
 docker volume create todo-db
```
- https://docs.docker.com/get-started/05_persisting_data/

> Start the todo app container, but add the -v flag to specify a volume mount. We will use the named volume and mount it to /etc/todos, which will capture all files created at the path.
```
 docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
```
- https://docs.docker.com/get-started/05_persisting_data/

**docker build**
>  ...build the container image using the docker build command.
```
 docker build -t getting-started .
```
- Definition and Code from https://docs.docker.com/get-started/02_our_app/


> Running the docker build command creates a Docker image using the Dockerfile. This built image is in your machine's local Docker image registry. - https://hub.docker.com/?overlay=onboarding

**docker run**
Running a container launches your software with private resources, securely isolated from the rest of your machine. - https://hub.docker.com/?overlay=onboarding

If no image can be found locally, one is downloaded from dockerhub and then run.
The following example downloads from here: https://hub.docker.com/r/docker/whalesay/
```
 docker run docker/whalesay cowsay Hello World
 _____________ 
< Hello World >
 ------------- 
    \
     \
      \     
                    ##        .            
              ## ## ##       ==            
           ## ## ## ##      ===            
       /""""""""""""""""___/ ===        
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~   
       \______ o          __/            
        \    \        __/             
          \____\______/   

```


### Programming > Patterns

**Microservice**
> In short, the microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP resource API. These services are built around business capabilities and independently deployable by fully automated deployment machinery. There is a bare minimum of centralized management of these services, which may be written in different programming languages and use different data storage technologies. - https://martinfowler.com/microservices/

### Programming > Concepts

**version control / Version Control System (VCS)**
> Version control is a system that records changes to a file or set of files over time so that you can recall specific versions later. - https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control

**SDK**
Software Development Kit
> An SDK seems to be a complete set of APIs that allow you to perform most any action you would need to for creating applications. In addition an SDK may include other tools for developing for the platform/item that it is for. An API on the other hand is just a series of related methods that may be good for a specific purpose. As an example, the JDK (Java Development Kit) contains the API as well as the compilers, runtimes, and other miscellaneous tools. The Java API is simply all the libraries that make up the core language that you can work with out of the box. - https://softwareengineering.stackexchange.com/questions/101873/whats-the-difference-between-an-api-and-an-sdk

**CRM**
> is a technology for managing all your company’s relationships and interactions with customers and potential customers. The goal is simple: Improve business relationships. A CRM system helps companies stay connected to customers, streamline processes, and improve profitability. When people talk about CRM, they are usually referring to a CRM system, a tool that helps with contact management, sales management, productivity, and more. A CRM solution helps you focus on your organization’s relationships with individual people — including customers, service users, colleagues, or suppliers — throughout your lifecycle with them, including finding new customers, winning their business, and providing support and additional services throughout the relationship. - https://www.salesforce.com/crm/what-is-crm/

**package manager**
>  job is to obtain appropriate libraries and dependent software necessary to compile and run software on a particular operating system. - https://www.quora.com/What-is-Homebrew-for-macOS

**unit testing**
>  Unit testing is very fine-grained, testing single components to make sure they function properly - s4

**integration testing**
>  tests the interaction between multiple components, or even the whole system - s4

**pattern**
> There’s no generally accepted definition of a pattern, but perhaps the best place to start is Christopher Alexander, an inspiration for many pattern enthusiasts: “Each pattern describes a problem which occurs over and over again in our environment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice” [Alexander et al.]. - s2

**throughput**
> Throughput is how much stuff you can do in a given amount of time. If you’re timing the copying of a file, throughput might be measured in bytes per second. For enterprise applications a typical measure is transactions per second
(tps), but the problem is that this depends on the complexity of your transaction. For your particular system you should pick a common set of transactions. - s2

**scalability**
> Scalability is a measure of how adding resources (usually hardware) affects performance. A scalable system is one that allows you to add hardware and get a commensurate performance improvement, such as doubling how many servers you have to double your throughput. Vertical scalability, or scaling up, means adding more power to a single server, such as more memory. Horizontal scalability, or scaling out, means adding more servers. - s2

## Programming >  Principles

**DRY**
Don't Repeat Yourself

## API

>  API is an application programming interface. It is a set of rules that allow programs to talk to each other. The developer creates the API on the server and allows the client to talk to it. - https://www.smashingmagazine.com/2018/01/understanding-using-rest-api/

### API > Rest

> REST stands for REpresentational State Transfer. It means when a RESTful API is called, the server will transfer to the client a representation of the state of the requested resource. - https://medium.com/extend/what-is-rest-a-simple-explanation-for-beginners-part-1-introduction-b4a072f8740f


## Shell

**mkdir**
makes a directory
```bash
mkdir test
```

**cp**
copies a file to a destination
```bash
cp node_modules/mocha/mocha.js public/vendor
```

**., ./, ../**
Pathnames that start with /, ./, or ../ are resolved relative to the current module’s path, where . stands for the current directory, ../ for one directory up, and / for the root of the file system. So if you ask for "./graph" from the file /tmp/robot/robot.js, Node will try to load the file /tmp/robot/graph.js. - s7

** ps **
> The ps command is used to list the currently running processes and their PIDs. - http://www.linfo.org/process.html
```
$ ps
  PID TTY           TIME CMD
    1 ??        30:26.72 /sbin/launchd
   62 ??         0:54.92 /usr/sbin/syslogd
```

**touch**
creates a file
```
 touch first.sh
```

**Create and Run a Shell File**
``` 
$ touch first.sh
$ nano first.sh
{Enter the following}
#!/bin/sh
echo Hello World
{Save the file and exit}
$  chmod 755 first.sh
$ ./first.sh
{outputs Hello World}
```
- https://www.shellscript.sh/first.html

## Git

**.gitignore**
> If you create a file in your repository named .gitignore, Git uses it to determine which files and directories to ignore, before you make a commit. A .gitignore file should be committed into your repository, in order to share the ignore rules with any other users that clone the repository. - https://help.github.com/en/articles/ignoring-files
```git
# ignore packages installed by npm
node_modules

# put any other files you don't want to check in here,
# such as .DS_Store (OSX), *.bak, etc.
```

**stash**

Places uncommitted changes into a holding area, and applies them to whatever branch you're on when you $ git stash apply.

Can be used if you're on the wrong branch with uncommitted changes
```bash
git status
{on branch master with uncommitted changes}
git stash
git checkout dev
git stash apply
{changes applied to dev branch}
```

**cherry pick**

Copies a commit from one branch to another

Can be used if you're on the wrong branch with committed changes
```bash
git status
{on branch master with uncommitted changes}
git log
{commit f02b862a17d3942f0f95b8593e02035c01a835b0 (HEAD -> master)}
git checkout dev
git cherry-pick f02b862a17
{commit added to dev branch}
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

**XMLHttpRequest (XHR)**
> Use XMLHttpRequest (XHR) objects to interact with servers. You can retrieve data from a URL without having to do a full page refresh. This enables a Web page to update just part of a page without disrupting what the user is doing. XMLHttpRequest is used heavily in AJAX programming. Despite its name, XMLHttpRequest can be used to retrieve any type of data, not just XML. - https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest

**ajax (Asynchronous JavaScript and XML)**
> The term Ajax has come to represent a broad group of Web technologies that can be used to implement a Web application that communicates with a server in the background, without interfering with the current state of the page. In the article that coined the term Ajax, Jesse James Garrett explained that the following technologies are incorporated:
- HTML (or XHTML) and CSS for presentation
- The Document Object Model (DOM) for dynamic display of and interaction with data
- JSON or XML for the interchange of data, and XSLT for its manipulation
- The XMLHttpRequest object for asynchronous communication
- JavaScript to bring these technologies together
> https://en.wikipedia.org/wiki/Ajax_(programming)

**Internet Media Types / MIME Types / Content Type**
> The Content-Type header is critically important: without it, the client would have to painfully guess how to render the content. The format of the Content-Type header is an Internet media type, which consists of a type, subtype, and optional parameters. For example, text/html; charset=UTF-8 specifies a type of “text,” a subtype of “html,” and a character encoding of UTF-8. The Internet Assigned Numbers Authority maintains an official list of Internet media types. Often, you will hear “content type,” “Internet media type,” and “MIME type” used interchangeably. MIME (Multipurpose Internet Mail Extensions) was a precursor of Internet media types and, for the most part, is equivalent. - s3

**URI**
>  is a string of characters that unambiguously identifies a particular resource.  - https://en.wikipedia.org/wiki/Uniform_Resource_Identifier

> Examples are: mailto:John.Doe@example.com, telnet://192.0.2.16:80/, https://example.com/path/resource.txt#fragment - https://en.wikipedia.org/wiki/Uniform_Resource_Identifier

**URL (Universal Resource Locator)**
![Anatomy of a URL](https://cascadingmedia.com/assets/images/insites/2015/02/url-anatomy/url-anatomy-55598c24.png)
> image from https://cascadingmedia.com/insites/2015/02/url-anatomy-seo-tips.html

> A Uniform Resource Locator (URL) is a URI that specifies the means of acting upon or obtaining the representation of a resource, i.e. specifying both its primary access mechanism and network location. For example, the URL http://example.org/wiki/Main_Page refers to a resource identified as /wiki/Main_Page, whose representation, in the form of HTML and related code, is obtainable via the Hypertext Transfer Protocol (http:) from a network host whose domain name is example.org. - https://en.wikipedia.org/wiki/Uniform_Resource_Identifier

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

> Note that the browser will respect the Content-Type header regardless of what the URL path is. So you could serve HTML from a path of /image.jpg or an image from a path of /text.html.  - s3

> The Content-Type header is critically important: without it, the client would have to painfully guess how to render the content. - s3

> Summary; if you have binary (non-alphanumeric) data (or a significantly sized payload) to transmit, use multipart/form-data. Otherwise, use application/x-www-form-urlencoded. The MIME types you mention are the two Content-Type headers for HTTP POST requests that user-agents (browsers) must support. The purpose of both of those types of requests is to send a list of name/value pairs to the server. Depending on the type and amount of data being transmitted, one of the methods will be more efficient than the other. - https://stackoverflow.com/questions/4007969/application-x-www-form-urlencoded-or-multipart-form-data

## Database

### Database > SQL (Structured Query Language)

## Javascript

### JavaScript > Patterns

** Promisifying **
> This technique is a way to be able to use a classic JavaScript function that takes a callback, and have it return a promise
```
const getFile = (fileName) => {
  return new Promise((resolve, reject) => {
    fs.readFile(fileName, (err, data) => {
      if (err) {
        reject(err)
        return
      }
      resolve(data)
    })
  })
}
```
Definition and code from https://nodejs.dev/learn/understanding-javascript-promises

** Promise Chaining**
```
const one = () => {
  return new Promise((resolve, reject) => {
    return setTimeout(() => {
      console.log('num in one is ', 1);
      resolve(1);
    }, 1000);
  })
}

const two = (num) => {
  return new Promise((resolve, reject) => {
    return setTimeout(() => {
      console.log('num in two is ', num + 1);
      resolve(num + 1);
    }, 1000);
  })
}

const three = (num) => {
  return new Promise((resolve, reject) => {
    return setTimeout(() => {
      console.log('num in three is ', num + 1);
      resolve(num + 1);
    }, 1000);
  })
}

one()
  .then(two) 
  .then(three)
  .then(data => console.log('completed returning', data));
```
Outputs
```
num in one is  1
num in two is  2
num in three is  3
completed returning 3
```

**Guard Pattern**
> Replace Nested Conditional with Guard Clauses -https://refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html
From:
```javascript
function getPayAmount() {
  let result;
  if (isDead)
    result = deadAmount();
  else {
    if (isSeparated)
      result = separatedAmount();
    else {
      if (isRetired)
        result = retiredAmount();
      else
        result = normalPayAmount();
    }
  }
  return result;
}
```
To:
```javascript
function getPayAmount() {
  if (isDead) return deadAmount();
  if (isSeparated) return separatedAmount();
  if (isRetired) return retiredAmount();
  return normalPayAmount();
}
```
- code from https://refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html

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

**promise**
> Essentially, a promise is a returned object to which you attach callbacks, instead of passing callbacks into a function. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises

> A promise must be in one of three states: pending, fulfilled, or rejected. - https://promisesaplus.com/

Once a promise has been called, it will start in a pending state. This means that the calling function continues executing, while the promise is pending until it resolves, giving the calling function whatever data was being requested. The created promise will eventually end in a resolved state, or in a rejected state, calling the respective callback functions (passed to then and catch) upon finishing. Using resolve and reject, we can communicate back to the caller what the resulting promise state was, and what to do with it. - https://nodejs.dev/learn/understanding-javascript-promises


** UnhandledPromiseRejectionWarning **
This means that a promise you called rejected, but there was no catch used to handle the error. Add a catch after the offending then to handle this properly. - https://nodejs.dev/learn/understanding-javascript-promises


**Promise.all**
```javascript
const foo = [
  new Promise((resolve, reject) => setTimeout(resolve, 1, '🥝')),
  new Promise((resolve, reject) => setTimeout(resolve, 1, '🍓')),
  new Promise((resolve, reject) => setTimeout(resolve, 1, '🍍')),
  new Promise((resolve, reject) => setTimeout(resolve, 1, '🍇'))
];

Promise.all(foo)
  .then(console.log)
  .catch(console.log);
  
>> [ '🥝', '🍓', '🍍', '🍇' ]
```

**Synchronous Loop**

A loop that waits between iterations
```
const waityLoop = async () => { 
 const rows = [1, 2, 3, 4, 5];
  for (const row of rows) {
    await waity(row);
  }
  console.log('done');
}

const waity = (row) => {
  return new Promise((resolve, reject) => {
    return setTimeout(() => {
      console.log(row);
      resolve();
    }, 1000);
  });
}

waityLoop();

>> 1
>> 2
>> 3
>> 4
>> 5
>> done
```


** async **

Prepending the async keyword to any function means that the function will return a promise. Even if it's not doing so explicitly, it will internally make it return a promise.
```
const aFunction = async () => {
  return 'test'
}

aFunction().then(alert) // This will alert 'test'
```
and it's the same as:
```
const aFunction = () => {
  return Promise.resolve('test')
}

aFunction().then(alert) // This will alert 'test'
```
- Definition and code from https://nodejs.dev/learn/modern-asynchronous-javascript-with-async-and-await

This

**const**
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
> The static keyword defines a static method for a class. Static methods aren't called on instances of the class. Instead, they're called on the class itself. These are often utility functions, such as functions to create or clone objects. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static

```javascript
class ClassWithStaticMethod {
  static staticMethod() {
    return 'static method has been called.';
  }
}

console.log(ClassWithStaticMethod.staticMethod());
>> expected output: "static method has been called.
```
- code from https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static


Example Class

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

**npm install --save-dev**
npm install --save-dev mocha
> --save-dev instead of --save; this tells npm to list this package in the development dependencies instead of the runtime dependencies. This will reduce the number of dependencies the project has when we deploy live instances of the website. - s4

**npm install --save**
npm install --save express
> If you specify the --save flag, it will update the package.json file - s4

**npm semver**
> NPM demands that its packages follow a schema called semantic versioning, which encodes some information about which versions are compatible (don’t break the old interface) in the version number. A semantic version consists of three numbers, separated by periods, such as 2.3.0. Every time new functionality is added, the middle number has to be incremented. Every time compatibility is broken, so that existing code that uses the package might not work with the new version, the first number has to be incremented. - https://eloquentjavascript.net/20_node.html

Tilde Ranges ~1.2.3 ~1.2 ~1
Allows patch-level changes if a minor version is specified on the comparator. Allows minor-level changes if not.
~1.2.3 := >=1.2.3 <1.(2+1).0 := >=1.2.3 <1.3.0

Caret Ranges ^1.2.3 ^0.2.5 ^0.0.4
Allows changes that do not modify the left-most non-zero digit in the [major, minor, patch] tuple. In other words, this allows patch and minor updates for versions 1.0.0 and above, patch updates for versions
- https://docs.npmjs.com/cli/v7/using-npm/semver#caret-ranges-123-025-004

**package-lock.json**
>The goal of package-lock.json file is to keep track of the exact version of every package that is installed so that a product is 100% reproducible in the same way even if packages are updated by their maintainers. The package-lock.json sets your currently installed version of each package in stone, and npm will use those exact versions when running npm install. The package-lock.json file needs to be committed to your Git repository, so it can be fetched by other people, if the project is public or you have collaborators, or if you use Git as a source for deployments. - https://nodejs.dev/learn/the-package-lock-json-file

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

### JavaScript > Node > Libraries > assert
> An assertion describes what the result of a computation is expected to look like and throws an exception if those expectations aren’t correct. - s5

**equal**
```javascript
assert.equal(7 + 1, 8);

>> undefined

assert.equal(7 + 1, 6);

>> AssertionError [ERR_ASSERTION]: 8 == 6
```


### JavaScript > Node > Libraries > process

**env**
> The process.env global variable is injected by the Node at runtime for your application to use and it represents the state of the system environment your application is in when it starts. For example, if the system has a PATH variable set, this will be made accessible to you through process.env.PATH which you can use to check where binaries are located and make external calls to them if required. - https://codeburst.io/process-env-what-it-is-and-why-when-how-to-use-it-effectively-505d0b2831e7
Can be called from the terminal:
```terminal
PORT=8626 NODE_ENV=development node server.js
```
or from a .env file using the dotenv npm package.

** on **

```
process.on('exit', (code) => {
  console.log(`About to exit with code: ${code}`);
});

> About to exit with code: 0
```

** exit codes**
> Node.js will normally exit with a 0 status code when no more async operations are pending. 
> 1 Uncaught Fatal Exception: There was an uncaught exception, and it was not handled by a domain or an 'uncaughtException' event handler. - https://nodejs.org/api/process.html#process_exit_codes

**nextTick()**
>  which defers the execution of a function until the next pass of the event loop. Its functioning is very simple; it takes a callback as an argument and pushes it to the top of the event queue, in front of any pending I/O event, and returns immediately. The callback will then be invoked as soon as the event loop runs again. - s1

> Calling setTimeout(() => {}, 0) will execute the function at the end of next tick, much later than when using nextTick() which prioritizes the call and executes it just before the beginning of the next tick. Use nextTick() when you want to make sure that in the next event loop iteration that code is already executed. - https://nodejs.dev/learn/understanding-process-nexttick

> We guarantee that a callback is invoked asynchronously by deferring its execution using process.nextTick(). - s1
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
  res.statusCode = 200
  res.setHeader('Content-Type', 'text/plain')
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

**req (http.IncomingMessage) and res (http.ServerResponse)**
Whenever a new request is received, the request event is called, providing two objects: a request (an http.IncomingMessage object) and a response (an http.ServerResponse object). Those 2 objects are essential to handle the HTTP call. The first provides the request details. In this simple example, this is not used, but you could access the request headers and request data. The second is used to return data to the caller. In this case with:
```
res.statusCode = 200
```
we set the statusCode property to 200, to indicate a successful response.
- https://nodejs.dev/learn


> code from https://blog.risingstack.com/your-first-node-js-http-server/


### JavaScript > Node > Libraries > error
1. Standard JavaScript errors such as <EvalError>, <SyntaxError>, <RangeError>, <ReferenceError>, <TypeError>, and <URIError>.


2. System errors triggered by underlying operating system constraints such as attempting to open a file that does not exist or attempting to send data over a closed socket.


3. User-specified errors triggered by application code.


4. AssertionErrors are a special class of error that can be triggered when Node.js detects an exceptional logic violation that should never occur. These are raised typically by the assert module.

- https://nodejs.org/api/errors.html#errors_errors


**error.stack**

shows the call stack when the error occurred

```javascript
function h(z) {
  const error = new Error();
  console.log(error.stack);
}
function g(y) {
  h(y + 1);
}
function f(x) {
  g(x + 1);
}
f(3);

>>Error
    at h (evalmachine.<anonymous>:2:17)
    at g (evalmachine.<anonymous>:6:3)
    at f (evalmachine.<anonymous>:9:3)
    at evalmachine.<anonymous>:11:1
    at Script.runInContext (vm.js:133:20)
    at Object.runInContext (vm.js:311:6)
    at evaluate (/run_dir/repl.js:133:14)
    at ReadStream.<anonymous> (/run_dir/repl.js:116:5)
    at ReadStream.emit (events.js:198:13)
    at addChunk (_stream_readable.js:288:12) 
```
- code from s5

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

**initial use case**
> Creating web services is what Node.js was made for, and that's still the dominant use case for it. - s4

> Node was initially conceived for the purpose of making asynchronous programming easy and convenient. - s7

**event-driven programming**
> The core philosophy behind Node is that of event-driven programming. What that means for you, the programmer, is that you have to understand what events are available to you and how to respond to them. Many people are introduced to event-driven programming by implementing a user interface: the user clicks on something, and you handle the “click event.” - s3

**the app is the web server**
> If you’ve ever built a static HTML website before, or are coming from a PHP or ASP background, you’re probably used to the idea of the web server (Apache or IIS, for example) serving your static files so that a browser can view them over the network. Node offers a different paradigm than that of a traditional web server: the app that you write is the web server. Node simply provides the framework for you to build a web server.- s3

**Asynchronous vs. Synchronous**
> A JavaScript program is (practically) always broken up into two or more chunks, where the first chunk runs now and the next chunk runs later, in response to an event. Even though the program is executed chunk-by-chunk, all of them share the same access to the program scope and state, so each modification to state is made on top of the previous state. Whenever there are events to run, the event loop runs until the queue is empty. Each iteration of the event loop is a "tick." User interaction, IO, and timers enqueue events on the event queue. At any given moment, only one event can be processed from the queue at a time. While an event is executing, it can directly or indirectly cause one or more subsequent events. Concurrency is when two or more chains of events interleave over time, such that from a high-level perspective, they appear to be running simultaneously (even though at any given moment only one event is being processed). - s6

 ** Single-Threaded**   
    
> The Node.js JavaScript code runs on a single thread. There is just one thing happening at a time. This is a limitation that's actually very helpful, as it simplifies a lot how you program without worrying about concurrency issues. You just need to pay attention to how you write your code and avoid anything that could block the thread, like synchronous network calls or infinite loops. - https://nodejs.dev/learn/the-nodejs-event-loop

> In its most basic form, JavaScript is a synchronous, blocking, single-threaded language, in which only one operation can be in progress at a time. - https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing    
    
> If we're running an operation that takes time however, like querying a database and using the results to populate templates, it is better to push this off the main thread and complete the task asynchronously - https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing

** Blocking the Thread **
    
Any JavaScript code that takes too long to return back control to the event loop will block the execution of any JavaScript code in the page, even block the UI thread, and the user cannot click around, scroll the page, and so on. Almost all the I/O primitives in JavaScript are non-blocking. Network requests, filesystem operations, and so on. Being blocking is the exception, and this is why JavaScript is based so much on callbacks, and more recently on promises and async/await. - https://nodejs.dev/learn/the-nodejs-event-loop

* An example of synchronous blocking code, adapted from s5
```HTML
<!doctype html>
<html>
<body>
    <a id="block" href="">Block incrementing for 5 seconds</a>
    <div id="counter">0</div>
    <button onclick="buttonClick()">Click to increment</button>
    <script>
        var clickCounter = 0;
        
        function buttonClick() {
          clickCounter += 1;
          document.getElementById("counter").innerHTML = clickCounter;
        }
         
        document.getElementById('block').addEventListener('click', onClick);
        
        function onClick(event) {
          event.preventDefault();
          sleep();   
        }
        
        function sleep(milliseconds) {
          var start = Date.now();
          while ((Date.now() - start) < 5000);
        }
    </script>
</body>
</html>
```
> If you click the first button and then quickly click the second one, you'll see that the alert does not appear until the circles have finished being rendered. The first operation blocks the second one until it has finished running. Why is this? The answer is because JavaScript, generally speaking, is single threaded. - https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Concepts

* An example of an asynchronous function
```javascript
const https = require('https');
const URL = 'https://jsonplaceholder.typicode.com/todos/1';

console.log('A');
https.get(URL, (resp) => {
  let data = '';
  resp.on('data', (chunk) => {
    data += chunk;
  });
  resp.on('end', () => {
    console.log('B');
  });
}).on("error", (err) => {
  console.log("Error: " + err.message);
});
console.log('C');

>> A
>> C
>> B
```

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
new event from the queue to be processed. - s3

### Javascript > Node > Features

**__dirname and __filename**
>  __filename and __dirname are used to get the filename and directory name of the currently executing file. - https://www.geeksforgeeks.org/difference-between-__dirname-and-in-node-js/

```
console.log("__dirname:    ", __dirname);
console.log("filename: ", __filename);
> __dirname:     /Users/mwaechter/Desktop/express_test
> filename:  /Users/mwaechter/Desktop/express_test/app.js
```
- code from https://www.geeksforgeeks.org/difference-between-__dirname-and-in-node-js/
    
> \_\_dirname will resolve to the directory the executing script resides in. So if your script resides in /home/sites/app.js, \_\_dirname will resolve to /home/sites. It’s a good idea to use this handy global whenever possible. Failing to do so can cause hard-to-diagnose errors if you run your app from a different directory. - s3
```javascript
fs.readFile(__dirname + '/cat.txt', function(err, data) {
  if (err) {
    console.log(err)
  } else {
     console.log(data)
  }
```
    
 
### Javascript > Node > Express
> To serve static files such as images, CSS files, and JavaScript files, use the express.static built-in middleware function in Express. - https://expressjs.com/en/starter/static-files.html
    
```
app.use(express.static(path.join(__dirname, 'public')));
{Add a file called hello_world.jpeg to public/images}
$ npm start
{Navigate to http://localhost:3000/images/hello_world.jpeg in your browser. The image will be displayed}
```
    

### Javascript > Vanilla

### Javascript > Vanilla > Concepts

**naming conventions**
```txt
In general, JavaScript uses camel case, except for constants.

Lowercase:
    Functions, variables: myFunction
    Methods: obj.myMethod

Uppercase:
    Classes: MyClass
    Constants: MY_CONSTANT
    Constants are also often written in camel case: myConstant
```
- s5

**Statement**
> A statement is a piece of code that can be executed and performs some kind of action. For example, if is a statement. One more example of a statement: a function declaration. - s5

**Function Declaration**
```javascript
function add(x, y) {
  return x + y;
}
```

**Expression**
> An expression is any valid unit of code that resolves to a value. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators

>  let myStr = (myBool ? 'Yes' : 'No'); The operator _?_:_ used between the parentheses is called the ternary operator. It is the expression version of the if statement. - s5

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

**encodeURIComponent**
> ... characters such as /, :, and # that serve to separate the various components of a URI, are replaced with one or more hexadecimal escape sequences. https://www.oreilly.com/library/view/javascript-the-definitive/9781449393854/rn01re84.html

> Use encodeURIComponent on user-entered fields from forms POST'd to the server. This will encode "&" symbols that may inadvertently be generated during data entry for special HTML entities or other characters that require encoding/decoding. For example, if a user writes "Jack & Jill", the text may get encoded as "Jack &amp; Jill". Without encodeURIComponent the ampersand could be interpretted on the server as the start of a new field and jeopardize the integrity of the data. > https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent
```javascript
const nicknames = encodeURIComponent('Jack + Jill');
let url = 'https://www.example.com?nicknames='
url += nicknames;

>> 'https://www.example.com?nicknames=Jack%20%2B%20Jill'
```

**setTimeOut**
Can be used to simulate an asynchronous event

> It's important to note that setTimeout(..) doesn't put your callback on the event loop queue. What it does is set up a timer; when the timer expires, the environment places your callback into the event loop, such that some future tick will pick it up and execute it. - s6

```javascript
setTimeout(function(){
  console.log('I waited'), 1000);
}
>> I waited
```

> Takes n parameters. The first is a callback, the second is the wait period until the callback is executed.  The next n paramters are parameters that are passed into the callback when it executes.
```javascript
function test(cb) {
  setTimeout(cb, 2000, 'cats')
}

test(console.log);

>> cats
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

 ** .prototype **
 > So what exactly is prototype in JavaScript? Well, simply put, every function in JavaScript has a prototype property that references an object. Anticlimactic, right? Test it out for yourself. Again, prototype is just a property that every function in JavaScript has and, as we saw above, it allows us to share methods across all instances of a function.  - https://ui.dev/beginners-guide-to-javascript-prototype/
    
    
** Object.create **
> Object.create. Simply put, Object.create allows you to create an object which will delegate to another object on failed lookups.
```
const parent = {
  name: 'Stacey',
  age: 35,
  heritage: 'Irish'
}

const child = Object.create(parent)
child.name = 'Ryan'
child.age = 7

console.log(child.name) // Ryan
console.log(child.age) // 7
console.log(child.heritage) // Irish
```
- Definition and Code from https://ui.dev/beginners-guide-to-javascript-prototype/
    
    
    
    
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

