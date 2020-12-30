# User’s Manual

## 1. Getting Started

### 1.0 Overview

When using JMeter you will usually follow this process:

#### 1.0.1 Test plan building

To do that, you will run JMeter in GUI Mode

Then you can either choose to record the application from a browser, or native application. You can use for that the menu File -> Templates… -> Recording

Note you can 

#### 1.0.2 Load Test running

#### 1.0.3 Load Test analysis

#### 1.0.4 Let’s start

### 1.1 Requirements

#### 1.1.1 Java Version

#### 1.1.2 Operating Systems

### 1.2 Optional

#### 1.2.1 Java Compiler

#### 1.2.2 SAX XML Parser

#### 1.2.3 Email Support

#### 1.2.4 SSL Encryption

#### 1.2.5 JDBC Driver

#### 1.2.6 JMS client

#### 1.2.7 Libraries for ActiveMQJMS

### 1.3 Installation

### 1.4 Running JMeter

#### 1.4.1 JMeter’s Classpath

#### 1.4.2 Create Test Plan from Template

#### 1.4.3 Using JMeter behind a proxy

#### 1.4.4 CLI Mode(Command Line mode was called NON GUI mode)

#### 1.4.5 Server Mode

#### 1.4.6 Overriding Properties Via The Command Line

#### 1.4.7 Logging and error messages

#### 1.4.8 Full list of command-line options

#### 1.4.9 CLI mode shutdown

### 1.5 Configuraing JMeter



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

### 3.2 COntrollers

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

### 3.12 Using Variables to parameterise tests



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

##### 14.2.1.2 Save Service configuraion

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

#### 14.3.1 Gerneration from an existing sample CSV log file

#### 14.3.2 Generation after load test

#### 14.3.3 Generation using GUI Tools menu

### 14.4 Default graphs

### 14.5 Generating customs graphs over time

### 14.6 Want to improve Report Dashborad?



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

#### 

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

Who knows our network topology? If you run into any firewall or proxy isssues, this will become very important. A well, a private testing network (which will therefore have very low network latency) would be a very nice thing. Knowing who can set one up for you (if you feel that this is necessary) will be very useful. If the application doesn’t scale as expected, who can add additional hardware?

#### Application

Who knows how our application functions? The normal sequence is 

* test(low-volume - can we benchmark our application?)
* benchmark ( the average number of users)
* load-test  (the maximum number of users)
* test destructively (what is our hard limit?)

The test process may progress from black-box testing to white-box testing (the difference is that the first requires no knowledge of the application while the second requires some knowledge of the application). It is not uncommon to discover problems with the application during this process, so be prepared to defend your work.

###  What platform should I use to run the benchmarks/load-tests?

This should be a widely-used piece of hardware, with a standard (i.e. vanilla) software installation. Remember, if you publish your results, the fist thing your clients will do is hire a gradute student to verify them. You might as well make it as easy for this person as you possibly can.

For Windows, Windows XP Perfessional should be a minimum (the others do not multi-thread past 50-60 connections, and you probably anticipate more users than that).

Good free platforms include the linuxes, the BSDs, and Solaris Intel. If you have a little more money, there are commercial linuxes. This may be worth it if you need the support.

For non-Windows platforms, investigate “`ulimit -n unlimited`” with a view to including it in your user account startup scripts(`.bashrc` or `.cshrc` scripts for the testing account).

Also note that some Linux/Unix editions are intended for server use. These generally have minimal or no GUI support. Such OSes should be OK for running JMeter in CLI mode, but JMeter GUI mode probably won’t work unless you install a minimal GUI environment.

As you progress to larger-scale benchmarks/load-tests, this platform will become the limiting factor. So it’s worth using the best hardware and software that you have available. Remember to include the hardware/software configuration in your published benchmarks.

When you need a lot of machines or want to test the network latency, Cloud can help you. JMeter can easily be installed on Cloud instances as it runs on nearly any architecture available in the cloud. JMeter is also supported within Commercial Cloud PAAS if you don’t want to manage it yourself.

Don’t forget JMeter batch (CLI) mode. This mode should be used during load testing for many reasons:

* If you have a powerful server that supports Java but perhaps does not have a fast graphics implementation, or where you need to login remotely.
* Batch (CLI) mode can reduce the network traffic compared with using a remote display or client-server mode.
* Java AWT Thread used for GUI mode can alter injection behaviour by blocking sometimes

The batch log file can then be loaded into JMeter on a workstation for analysis, or you can use CSV output and import the data into a spreadsheet.

> Remember GUI mode is for Script creation and debugging, not for load testing

### Tools

The following tools will prove useful. It is definitely worthwhile to become familiar with them. This should include trying them out, and reading the appropriate documentation (man-pages, info-files, application — help messages, and any supplied documentation).

#### ping

This can be used to establish whether or not you can reach your target site. Options can be specified so that ‘ping’ provides the same type of route reporting as ’traceroute’

#### nslookup/dig

While the user will normally use a human-readable internet address, you may wish to avoid the overhead of DNS lookups when performing benchmarking/load-testing. These can be used to determine the unique address (dotted quad) of your target site.

#### traceroute

If you cannot “ping” your target site, this may be used to determine the problem (possibly a firewall or proxy). It can also be used to estimate the overall network latency (running locally should give the lowest possible network latency - remember that your users will be running over a possibly busy internet). Generally, the fewer hops the better.

### How can I enhance JMeter?

There a lof ot open-source and commercial providers who provide JMeter plugins or other resources for use with JMeter.

Some of these are listed on the JMeter Wiki. They are listed unser several categories:

* JMeterPlugins - plugins for extending JMeter
* JMeterAddons - addons for use with JMeter, e.g. plugins for browsers, Maven and Jenkins.
* JMeterServices - 3rd party services, e.g. cloud-based JMeter

Note that appearance of these on the Wiki does not imply any endorsement by the Apache JMeter project.

### Why Java?

Why not Perl or C?

Well, Perl might be a very good choice except that the Benchmark package seems to give fairly fuzzy results. Also, simulating multiple users with Perl is a tricky proposition (multiple connections can be simualted by forking many processes from a shell script, but these will not be threads, they will be processes). However, the Perl community is very large. If you find that someone has already written something that seems useful, this could be a very good solution.

C, of course, is a very good choice(check out the Apache ab tool). But be prepared to write all of the custom networking, threading, and state management code that you will need to benchmark you application.

Java gives you (for free) the custom networking, theading, and state management code that you will need to benchmark your application. Java is aware of HTTP, FTP, and HTTPS - as well as RMI, IIOP, and JDBC (not to mention cookies, URL-encoding, and URL-rewriting). In addition Java gives you automatic garbage-collection, and byte-code level security.



















