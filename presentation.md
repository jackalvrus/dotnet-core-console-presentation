## Easier Console Utilities in .NET Core

Jack Alvrus

---

### About Me

#### Jack Alvrus
* Full stack developer and occasional architect
* e-Commerce - CaptiveAire Systems

---

### ASP.NET Core

* Web applications and APIs
* Constructed using a host builder
* Includes several helpful features

---

![Web Project Code](images/CoreWebCode.png)

---

![Service Code](images/ServiceCode.png)

---

### Console Utility

Application that is invoked by a command line, performs an operation then terminates.

* Are supported by .NET Core
* Not as well supported as web applications
* Template does not include helpful features
* Challenging to use services created for web applications

---

![Console Code](images/ConsoleCode.png)

---

### Implementation Options

* Manually implement required features
* Adapt parts of web application ecosystem

---

### Basic Example Using Host Builder

---

![That was easy](https://media.makeameme.org/created/well-that-was-2e0h1n.jpg)

---

### What's Missing?

* Application lifecycle management
  * Ctrl+C to trigger CancellationToken
* Command line parsing
  * Multiple operations per utility
  * Command parameters
* Typed configuration
* Environment (development, staging, production)

---

### Application Lifecycle

We already built the host, can we just run it?<br/><br/>
No, doesn't work.

---

### Host Requirements

* Register a hosted service
* Handle differences in lifecycle between web application and console utility

---

### Console Utility Lifecycle

![Sequence Diagram](images/ConsoleUtilSeq.png)

---

### Web Application Lifecycle

![Sequence Diagram](images/WebAppSeq.png)

---

### Command Line Parsing

* Use a command line parsing NuGet package
* Use the built-in configuration features
  * The command line is a standard configuration source

<div style="height:1em"></div>
<div style="text-align:left;font-size:smaller;font-style:italic">
There are five basic alternative formats for arguments:<br/>
key1=value1<br/>
--key2=value2<br/>
/key3=value3<br/>
--key4 value4<br/>
/key5 value5.
</div>

---

### Typed Config and Environment

Web applications access `IConfiguration` and `IHostEnvironment` through the `Startup` class

![Web App Startup](images/StartupCode.png)

---

### Advanced Example

* Run the host
* Cancellation token
* Multiple operations per utility
* Command parameters
* Typed configuration
* Environment

---

### More Things to Consider

* Command line part 2
  * Validation
  * Strongly-typed configuration
* Output via Console or ILogger?
* Application vs. Utility
  * Single hosted service
  * IHostApplicationLifetime to implement exit/quit command

---

### Fin

Questions / Comments
