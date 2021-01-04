# Apache JMeter

## What can I do with it?

Apache JMeter may be used to <u>test performance</u> both on ==static and dynamic resources, Web dynamic applications.==

It can be used to <u>simulate a heavy load</u> on a server, group of servers, network or object <u>to test its strength</u> or <u>to analyze overall performance</u> *under different load types*.

Apache JMeter features include:

* Ability to load and performance test many different applications/server/protocol types:

* Full featured Test IDE that allows fast <u>Test Plan recording</u> (from Browsers or native applications), <u>building and debugging</u>.

* CLI mode to load test from any Java compatible OS

* A complete and ready to present dynamic HTML report

* Easy correlation through ability to extract data from most popular response formats, HTML, JSON, XML or any textual format

* Complete portablility and 100% Java purity.

* Full **multi-threading** framework allows concurrent sampling by many threads and simultaneous sampling of different functions by separate thread groups.

* Caching and offline analysis/replaying of test results

* Highly Extensible core:

  * Pluggable Samplers allow unlimited testing capabilities.

  * Scriptable Samplers 

  * Several load statistics may be chosen with pluggable timers.

  * Data analysis and <u>visualization plugins</u> allow great extensibility as well as personalization.

  * Functions can be used to provide dynamic input to a test or provide data manipulation.

    可以使用函数来给测试提供动态输入或者控制数据

## How do I do it?

## JMeter is not a browser

JMeter is not a browser, it works at protocol level. As for as web-services and remote services are concerned, JMeter looks like a browser (or rather, multiple browsers); however JMeter does not perform all the actions suported by browsers. In particular, JMeter does not execute the Javascript found in HTML pages. Nor does it render the HTML pages as a browser does (it’s possible to view the response as HTML etc., but <u>the timings are not included in any samplers, and only one sample in one thread is ever displayed at a time</u>).

## Tuto

# User’s Manual

## 1. Getting Started

### 1.0 Overview

When using JMeter you will usually follow this process:

#### 1.0.1 Test plan building

To do that, you will run JMeter in GUI Mode

Then you can either choose to record the application from a browser, or native application. You can use for that the menu <u>File -> Templates… -> Recording</u>

Note you can also manually build your plan. Ensure you read this documentation to understand major concepts.

You will also debug it using one of these options:

* Run ➡️ Start no pauses
* Run ➡️ Start
* Validate on Thread Group

and View Results Tree renderers or Testers (CSS/JQUERY, JSON, Regexp, XPath).

Ensure you follow best-practices when building your Test Plan.

#### 1.0.2 Load Test running

Once your Test Plan is ready, you can start your Load Test. The first step is to configure the injectors that will run JMeter, this as for any other Load Testing tool includes:

* Correct machine sizing in terms of CPU, memory, and network
* OS Tuning
* Java setup: Ensure you install the latest version of Java supported by JMeter
* **Increase the Java Heap size**. By default JMeter runs with a heap of 1 GB, this might not be enough for your test and depends on your test plan and number of threads you want to run

Once everything is ready, you will use CLI mode to run it for the Load Test.

Using CLI mode, you can generate a CSV (or XML) file containing results and have JMeter generate an HTML report at end of Load Test. JMeter will by default provide a summary of load test while it’s running. You can also have real-time results during your test using Backend Listener.

#### 1.0.3 Load Test analysis

Once your Load Test is finished, you can use the HTML report to analyze your load test.

#### 1.0.4 Let’s start

The easiest way to begin using JMeter is to first download the latest production release and install it. The release contains all of the files you need to build and run most types of tests, e.g. Web (HTTP/HTTPS), FTP, JDBC, LDAP, Java, JUnit and more.

If you want to perform JDBC testing, then you will, of course, need the appropriate JDBC driver from your vendor. JMeter does not come with any JDBC drivers.

Next, start JMeter and go through the Building a Test Plan section of the User Guide to familiarize yourself with JMeter basics.

Finally, go through the appropriate section on how to build a specific type of Test Plan. For example, if you are interested in testing a Web application, then see the section Building a Web Test Plan.

Once you are comfortable with building and running JMeter Test Plans, you can look into the various configuration elements(timers, listeners, assertions, and others) which give you more control over your Test Plans.

### 1.1 Requirements

JMeter requires that your computing environment meets some minimum requirements.

#### 1.1.1 Java Version

> JMeter is compatible with Java 8 or higher. We highly advise you to install latest minor version of your major version for security and performance reasons.

Because JMeter uses only standard Java APIs, please do not file bug reports if your JRE fails to run JMeter because of JRE implementation issues.

> Although you can use a JRE, it is better to install a JDK as for recording of HTTPS, JMeter needs `keytool` utility from JDK.

#### 1.1.2 Operating Systems

JMeter is a 100% Java application and should run correctly on any system that has a compliant Java implementation.

Operating systems tested with JMeter can be viewed on JMeter wiki.

Even if your OS is not listed on the wiki page, JMeter should run on it provided that JVM is compliant.

### 1.2 Optional

If you plan on doing JMeter development, then you will need one or more optional packages listed below.

### 1.3 Installation

We recommend that most users run the latest release.

To install a release build, simply unzip the zip/tar file into the directory where you want JMeter to be installed. Provided that you have a JRE/JDK correctly installed and the JAVA_HOME environment variable set, there is nothing more for you to do.

>  There can be problems (especially with client-server mode) if the directory path contains any spaces.
>
> 如果安装目录的路径含有空格的话, 会有问题(特别是在client-server 模式下)

The installation directory structure should look something like this (where X.Y is version number):

```shell
apache-jmeter-X.Y
apache-jmeter-X.Y/bin
apache-jmeter-X.Y/docs
apache-jmeter-X.Y/extras
apache-jmeter-X.Y/lib/
apache-jmeter-X.Y/lib/ext
apache-jmeter-X.Y/lib/junit
apache-jmeter-X.Y/licenses
apache-jmeter-X.Y/printable_docs
```

You can rename the parent directory (i.e. apache-jmeter-X.Y) if you want, but do not change any of the sub-directory names.

### 1.4 Running JMeter

To run JMeter, run the jmeter.bat (for Win) or jmeter (for Unix) file. These files are found in the `bin` directory. After a short time, the JMeter GUI should appear.

There are some additional scripts in the <u>bin</u> directory that you may find useful. Windows script files (the .CMD files require Win2K or later):

> jmeter.bat

​		run JMeter (in GUI mode by default)

> jmeterw.cmd

​		run JMeter without the windows shell console (in GUI mode by default)

> jmeter-n.cmd

​		drop a JMX file on this to run a CLI mode test

> jmeter-n-r.cmd

​		drop a JMX file on this to run a CLI mode test remotely

> jmeter-t.cmd

​		drop a JMX file on this to load it in GUI mode

> jmeter-server.bat

​		start JMeter in server mode

> mirror-server.cmd

​		runs the JMeter Mirror Server in CLI mode

> shutdown.cmd

​		Run the shutdown client to stop a CLI mode instance gracefully

> stoptest.cmd

​		Run the Shutdown client to stop a CLI mode instance abruptly

> The special name `LAST` can be used with `jmeter-n.cmd`, `jmeter-t.cmd` and `jmeter-n-r.cmd` and means the last test plan that was run interactively

There are a few environment variables, that can be used to customize the JVM settings for JMeter. An easy way to set those is by creating a file named `setenv.bat` in the bin directory. Such a file could look like:

```shell
rem This is the content of bin\setenv.bat
rem it will be called by bin\jmeter.bat

set JVM_ARGS = -Xms1024m -Xmx1024m -Dproname=value
```

The `JVM_ARGS` can be used to override JVM settings in the `jmeter.bat` script and will get set when starting JMeter, e.g.:

```shell
jmeter -t test.jmx ...
```

 The following environment variables can be defined:

> DDRAW

​		JVM options to influence usage of direct draw, e.g. `-Dsun.java2d.ddscale=true`. Default is empty.

> GC_ALGO

​		JVM garbage collector options. Defaults to `-XX:+UseG1GC -XX:MaxGCPauseMillis=250 -XX:G1ReservePercent=20`

> HEAP

​		JVM memory settings used when starting JMeter. Defaults to `-Xms1g -Xmx1g -XX:MaxMetaspaceSize=256m`

> JMETER_BIN

​		JMeter bin directory (must end in \\). Value will have been guessed, when `setenv.bat` is called.

> JMETER_COMPLETE_ARGS

​		If set indicates, that `JVM_ARGS` and `JMETER_OPTS` are to be used, only. All other options like HEAP and GC_ALGO will be ignored. Default is empty.

> JMETER_HOME

​		installation directory. Will be guessed from location of jmeter.bat

> JMETER_LANGUAGE

​		Java runtime options to specify used language. Defaults to: `-Duser.language="en" -Duser.region="EN"`

> JM_LAUNCH

​		Name of the java executable, like `java.exe` (default) or `javaw.exe`

> JVM_ARGS

​		Java options to be used when starting JMeter. These will be added last to the java command. Default is empty

Un*x script files; should work on most Linux/Unix systems:

> jmeter

​		run JMeter (in GUI mode by default). Defines some JVM settings which may not work for all JVMs.

> jmeter-server

​		start JMeter in server mode (calls jmeter script with appropriate parameters)

> jmeter.sh

​		very basic JMeter script (You may need to adapt JVM options like memory settings).

> mirror-server.sh

​		runs the JMeter Mirror Server in CLI mode

> shutdown.sh

​		Run the Shutdown client to stop a CLI mode instance gracefully

> stoptest.sh

​		Run the Shutdown client to stop a CLI mode 

#### 1.4.1 JMeter’s Classpath

JMeter automatically finds classes from jars in the following directories:



#### 1.4.2 Create Test Plan from Template



#### 1.4.3 Using JMeter behind a proxy

#### 1.4.4 CLI Mode(Command Line mode was called NON GUI mode)

#### 1.4.5 Server Mode

#### 1.4.6 Overriding Properties Via The Command Line

#### 1.4.7 Logging and error messages

#### 1.4.8 Full list of command-line options

#### 1.4.9 CLI mode shutdown

### 1.5 Configuring JMeter



## 2. Building a Test Plan

Adding and Removing Elements

### 2.1 Adding and Removing Elements



### 2.2 Loading and Saving Elements



### 2.3 Configuring Tree Elements



### 2.4 Saving the Test Plan



### 2.5 Running a Test Plan



### 2.6 Stopping a Test



### 2.7 Error reporting



## 3. Elements of a Test Plan

### 3.0 Test Plan



### 3.1 Thread Group



### 3.2 Controllers



#### 3.2.1 Samplers



#### 3.2.2 Logic Controllers



#### 3.2.3 Test Fragments



### 3.3 Listeners



### 3.4 Timers



### 3.5 Assertions



### 3.6 Configuration Elements



### 3.7 Pre-Processor Elements



### 3.8 Post-Processor Elements



### 3.9 Execution order



### 3.10 Scoping Rules



### 3.11 Properties and Variables



### 3.12 Using Variables to parameterize tests



## 4. Building a Web Test Plan

### 4.1 Adding Users



### 4.2 Adding Default HTTP Request Properties



### 4.3 Adding Cookie Support



### 4.4 Adding HTTP Requests



### 4.5 Adding a Listener to View Store the Test Results



### 4.6 Logging in to a web-site



### 4.7 choose the same user or different users



## 5. Building an Advanced Web Test Plan

### 5.1 Handling User Sessions With URL Rewriting



### 5.2 Using a Header Manager



Building a Database Test Plan

## 13. Remote Testing

### 13.1 Setting up SSL

### 13.2 Doing it Manually

### 13.3 Tips

### 13.4 Using a different port

### 13.5 Using a different sample sender

### 13.6 Dealing with nodes that failed starting

### 13.7 Using a security-manager



## 14. Dashboard Report

### 14.1 Overview



### 14.2 Configuring Dashboard Generation

#### 14.2.1 Requirements

##### 14.2.1.1 Filtering Configuration



##### 14.2.1.2 Save Service configuration



##### 14.2.1.3 Transaction Controller configuration



#### 14.2.2 General settings



#### 14.2.3 Graph settings

##### 14.2.3.1 General properties



##### 14.2.3.2 Specific properties



#### 14.2.4 Export settings

##### 14.2.4.1 General properties



##### 14.2.4.2 Specific properties



##### 14.2.4.3 Graph properties



##### 14.2.4.4 Filtering mechanisms



#### 14.2.5 Sample configuration

### 14.3 Generating reports

#### 14.3.1 Generation from an existing sample CSV log file



#### 14.3.2 Generation after load test



#### 14.3.3 Generation using GUI Tools menu



### 14.4 Default graphs



### 14.5 Generating customs graphs over time



### 14.6 Want to improve Report Dashboard?



Real time Results

## 16. Best Practices

### 16.1 Always use latest version of JMeter



### 16.2 Use the correct Number of Threads



### 16.3 Where to Put the Cookie Manager



### 16.4 Where to Put the Authorization Manager



### 16.5 Using the HTTP(S) Test Script Recorder



### 16.6 User variables



### 16.7 Reducing resource requirements



### 16.8 BeanShell server



### 16.9 BeanShell scripting



#### 16.9.1 Overview



#### 16.9.2 Sharing Variables



### 16.10 Developing script functions in Groovy or Jexl3 etc.

### 16.11 Parameterizing tests

### 16.12 JSR223 Elements

### 16.13 Sharing variables between threads and thread groups



### 16.14 managing properties



### 16.15 Deprecated elements



## 17. Help! My boss wants me to load test our web app!

This is a fairly open-ended proposition. There are a number of questions to be asked first, and additionally a number of resources that will be needed. You will need some hardware to run the benchmarks/load-tests from. A number of tools will prove useful. There are a number of products to consider. And finally, why is Java a good choice to implement a load-testing/Benchmarking product.

### Questions to ask

What is our anticipated average number of users (normal load)?

What is our anticipated peak number of users?

When is a good time to load-test our application (i.e. off-hours or week-ends), bearing in mind that this may very well crash one or more of our servers?

Does our application have state? If so, how does our application manage it(cookies, session-rewriting, or some other method)?

What is the testing intended to achieve?

### Resources

The following resources will prove very helpful. Bear in mind that if you cannot locate these resources, you will become these resources. As you already have your work cut out for you, it is worth knowing who the following people are, so that you can ask them for help if you need it.

#### Network

Who knows our network topology? If you run into any firewall or proxy issues, this will become very important. A well, a private testing network (which will therefore have very low network latency) would be a very nice thing. Knowing who can set one up for you (if you feel that this is necessary) will be very useful. If the application doesn’t scale as expected, who can add additional hardware?

#### Application

Who knows how our application functions? The normal sequence is 

* test(low-volume - can we benchmark our application?)
* benchmark ( the average number of users)
* load-test  (the maximum number of users)
* test destructively (what is our hard limit?)

The test process may progress from black-box testing to white-box testing (the difference is that the first requires no knowledge of the application while the second requires some knowledge of the application). It is not uncommon to discover problems with the application during this process, so be prepared to defend your work.

###  What platform should I use to run the benchmarks/load-tests?

This should be a widely-used piece of hardware, with a standard (i.e. vanilla) software installation. Remember, if you publish your results, the fist thing your clients will do is hire a graduate student to verify them. You might as well make it as easy for this person as you possibly can.

For Windows, Windows XP Professional should be a minimum (the others do not multi-thread past 50-60 connections, and you probably anticipate more users than that).

Good free platforms include the linuxes, the BSDs, and Solaris Intel. If you have a little more money, there are commercial linuxes. This may be worth it if you need the support.

For non-Windows platforms, investigate “`ulimit -n unlimited`” with a view to including it in your user account startup scripts(`.bashrc` or `.cshrc` scripts for the testing account).

Also note that some Linux/Unix editions are intended for server use. These generally have minimal or no GUI support. Such OSes should be OK for running JMeter in CLI mode, but JMeter GUI mode probably won’t work unless you install a minimal GUI environment.

As you progress to larger-scale benchmarks/load-tests, this platform will become the limiting factor. So it’s worth using the best hardware and software that you have available. Remember to include the hardware/software configuration in your published benchmarks.

When you need a lot of machines or want to test the network latency, Cloud can help you. JMeter can easily be installed on Cloud instances as it runs on nearly any architecture available in the cloud. JMeter is also supported within Commercial Cloud PAAS if you don’t want to manage it yourself.

Don’t forget JMeter batch (CLI) mode. This mode should be used during load testing for many reasons:

* If you have a powerful server that supports Java but perhaps does not have a fast graphics implementation, or where you need to login remotely.
* Batch (CLI) mode can reduce the network traffic compared with using a remote display or client-server mode.
* Java AWT Thread used for GUI mode can alter injection behavior by blocking sometimes

The batch log file can then be loaded into JMeter on a workstation for analysis, or you can use CSV output and import the data into a spreadsheet.

> Remember GUI mode is for Script creation and debugging, not for load testing

### Tools

The following tools will prove useful. It is definitely worthwhile to become familiar with them. This should include trying them out, and reading the appropriate documentation (man-pages, info-files, application — help messages, and any supplied documentation).

#### ping

This can be used to establish whether or not you can reach your target site. Options can be specified so that ‘ping’ provides the same type of route reporting as ’traceroute’

#### nslookup/dig

While the user will normally use a human-readable Internet address, you may wish to avoid the overhead of DNS lookups when performing benchmarking/load-testing. These can be used to determine the unique address (dotted quad) of your target site.

#### traceroute

If you cannot “ping” your target site, this may be used to determine the problem (possibly a firewall or proxy). It can also be used to estimate the overall network latency (running locally should give the lowest possible network latency - remember that your users will be running over a possibly busy Internet). Generally, the fewer hops the better.

### How can I enhance JMeter?

There a lot of open-source and commercial providers who provide JMeter plugins or other resources for use with JMeter.

Some of these are listed on the JMeter Wiki. They are listed under several categories:

* JMeterPlugins - plugins for extending JMeter
* JMeterAddons - addons for use with JMeter, e.g. plugins for browsers, Maven and Jenkins.
* JMeterServices - 3rd party services, e.g. cloud-based JMeter

Note that appearance of these on the Wiki does not imply any endorsement by the Apache JMeter project.

### Why Java?

Why not Perl or C?

Well, Perl might be a very good choice except that the Benchmark package seems to give fairly fuzzy results. Also, simulating multiple users with Perl is a tricky proposition (multiple connections can be simulated by forking many processes from a shell script, but these will not be threads, they will be processes). However, the Perl community is very large. If you find that someone has already written something that seems useful, this could be a very good solution.

C, of course, is a very good choice(check out the Apache ab tool). But be prepared to write all of the custom networking, threading, and state management code that you will need to benchmark you application.

Java gives you (for free) the custom networking, threading, and state management code that you will need to benchmark your application. Java is aware of HTTP, FTP, and HTTPS - as well as RMI, IIOP, and JDBC (not to mention cookies, URL-encoding, and URL-rewriting). In addition Java gives you automatic garbage-collection, and byte-code level security.



















