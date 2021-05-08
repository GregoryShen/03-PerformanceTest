# Apache JMeter

## What can I do with it?

Apache JMeter may be used to <u>test performance</u> both on **static** and **dynamic resources**, **Web dynamic applications**.

It can be used to <u>simulate a heavy load</u> on a server, group of servers, network or object <u>to test its strength</u> or <u>to analyze overall performance</u> *under different load types*.

Apache JMeter features include:

* Ability to load and performance test many different applications/server/protocol types:

* Full featured Test IDE that allows fast <u>Test Plan recording</u> (from Browsers or native applications), <u>building and debugging</u>.

* CLI mode to load test from any Java compatible OS

* A complete and ready to present dynamic HTML report

* Easy correlation through ability to extract data from most popular response formats, HTML, JSON, XML or any textual format

* Complete portability and 100% Java purity.

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

JMeter is not a browser, it works at protocol level. As for as web-services and remote services are concerned, JMeter looks like a browser (or rather, multiple browsers); however JMeter does not perform all the actions supported by browsers. In particular, JMeter does not execute the JavaScript found in HTML pages. Nor does it render the HTML pages as a browser does (it’s possible to view the response as HTML etc., but <u>the timings are not included in any samplers, and only one sample in one thread is ever displayed at a time</u>).

## Tutorials

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

Once your Test Plan is ready, you can start your Load Test. **The first step is to configure the injectors that will run JMeter**, this as for any other Load Testing tool includes:

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

To run JMeter, run the <u>jmeter.bat</u> (for Win) or <u>jmeter</u> (for Unix) file. These files are found in the `bin` directory. After a short time, the JMeter GUI should appear.

There are some additional scripts in the <u>bin</u> directory that you may find useful. Windows script files (the .CMD files require Win2K or later):

> ==jmeter.bat==

​		run JMeter (in GUI mode by default)

> ==jmeterw.cmd==

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

> ==jmeter==

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

#### 1.4.1 JMeter’ s Classpath

JMeter automatically finds classes from jars in the following directories:

> JMETER_HOME/lib

​		used for utility jars

> JMETER_HOME/lib/ext

​		used for JMeter components and plugins

If you have developed new JMeter components, then you should jar them and copy the jar into JMeter’ s `lib/ext` directory. JMeter will automatically find JMeter components in any jars found here. Do not use lib/ext for utility jars or dependency jars used by the plugins; it is only intended for JMeter components and plugins.

If you don’t want to put JMeter plugin jars in the `lib/ext` directory, then define the properly `search_paths` in `jmeter.properties`.

Utility and dependency jars (libraries etc) can be placed in the `lib` directory.

If you don’t want to put such jars in the lib directory, then define the properly `user.classpath` or plugin_dependency_paths in `jmeter.properties`. See below for an explanation of the differences.

Other jars (such as JDBC, JMS implementations and any other support libraries needed by the JMeter code) should be placed in the lib directory - not the lib/ext directory, or added to `user.classpath`.

> JMeter will only find .jar files, not .zip

You can also install utility Jar files in `$JAVA_HOME/jre/lib/ext`, or you can set the property `user.classpath` in `jmeter.properties`

Note that setting the `CLASSPATH` environment variable will have no effect. This is because JMeter is started with `“java -jar”`, and the java command silently ignores the `CLASSPATH` variable, and the `-classpath/-cp` options when `-jar` is used.

> This occurs with all Java programs, not just JMeter.

#### 1.4.2 Create Test Plan from Template

You have the ability to create a new Test Plan from existing template.

To do so you use the menu File → Templates … or Templates icon:

A popup appears, you can then choose a template among the list:

Some templates may need parameters input from the user. For these ones, after a click on the create button, a new window will appear as follow:

When you are done with parameters, click on the <u>Validate</u> button and the template will be created.

A documentation for each template explains what to do once test plan is created from template.

#### 1.4.3 Using JMeter behind a proxy



#### 1.4.4 CLI Mode(Command Line mode was called NON GUI mode)

For load testing, you must run JMeter in this mode (without the GUI) to get the optimal results from it. To do so, use the following command options:

`-n`

​		==This specifies JMeter is to run in cli mode==

`-t`

​		==[name of JMX file that contains the Test Plan]==

`-l`

​		[name of JTL file to log sample results to]

> What are JTL files?
>
> ​		JMeter can create text files containing the results of a test run.
>
> ​		These are normally called JTL files, as that is the default extension - but any extension can be used.
>
> Types of JTL file
>
> There are currently two types of JTL file:
>
> 	1. XML
> 	2. CSV (with and without header)
>
> The XML files can contain more types of information, but are considerably larger.
>
> more info: https://cwiki.apache.org/confluence/display/JMETER/JtlFiles

`-j`

​		[name of JMeter run log file]

`-r`

​		Run the test in the servers specified by the JMeter property “remote_hosts”

`-R`

​		[list of remote servers] Run the test in the specified remote servers

`-g`

​		[path to CSV file] generate report dashboard only

`-e`

​		==generate report dashboard after load test==

`-o`

​		output folder where to generate the report dashboard after load test. Folder must not exist or be empty

The script also lets you specify the optional firewall/proxy server information:

`-H`

​		[proxy server hostname or ip address]

`-P`

​		[proxy server port]

Example

```shell
jmeter -n -t my_test.jmx -l log.jtl -H my.proxy.server -P 8000
```

If the property `jmeterengine.stopfail.system.exit` is set to `true` (default is `false`), then JMeter will invoke `System.exit(1)` if it cannot stop all threads. Normally this is not necessary.

#### 1.4.5 Server Mode

For <u>distributed testing</u>, run JMeter in server mode on the remote node(s), and then control the server(s) from   the GUI. You can also use CLI mode to run remote tests. To start the server(s), run `jmeter-server[.bat]` on each server host.

The script also lets you specify the optional firewall/proxy server information.

`-H`

​		[proxy server hostname or ip address]

`-P`

​		[proxy server port]

Example:

```shell
jmeter-server -H my.proxy.server -P 8000
```

If you want the server to exit after a single test has been run, then define the JMeter property

`server.exitaftertest=true`.

To run the test from the client in CLI mode, use the following command:

```shell
jmeter -n -t testplan.jmx -r [-Gprop=val] [-Gglobal.properties] [-X]
```

where:

`-G`

​		is used to define JMeter properties to be set in the servers

`-X`

​		means exit the servers at the end of the test

`-Rserver1, server2`

​		can be used instead of `-r` to provide a list of servers to start. Overrides `remote_hosts`, but does not define the property.

If the property `jmeterengine.remote.system.exit` is set to `true` (default is `false`), then JMeter will invoke `System.exit(0)` after stopping RMI at the end of a test. Normally this is not necessary.

#### 1.4.6 Overriding Properties Via The Command Line



#### 1.4.7 Logging and error messages

> Since 3.2, JMeter logging is not configured through properties files(s) such as `jmeter.properties` any more, but it is configured through a <u>Apache Log4j 2</u> configuration file (`log4j2.xml` in the directory from which JMeter was launched, by default) instead. Also, every code including JMeter and plugins MUST use SLF4J library to leave logs since 3.2

Here is an example `log4j2.xml` file which defines two log appenders and loggers for each category.

```xml
<Configuration status="WARN" packages="org.apache.jmeter.gui.logging">
	
    <Appenders>
    	<!-- The main log file appender to jmeter.log in the directory from which JMeter was launched, by default. -->
        <File name="jmeter-log" fileName="${sys:jmeter.logfile:-jmeter.log}" append="false">
        	<PatternLayout>
            	<pattern>%d %p %c{1.}: %m%n</pattern>
            </PatternLayout>
        </File>
        
        <!-- Log appender for GUI log Viewer. See below. -->
        <GuiLogEvent name="gui-log-event">
            <PatternLayout>
            	<pattern>%d %p %c{1.}: %m%n</pattern>
            </PatternLayout>
        </GuiLogEvent>
    </Appenders>
    
    <Loggers>
    	
        <!-- Root logger -->
        <Root level="info">
        	<AppenderRef ref="jmeter-log" />
            <AppenderRef ref="gui-log-event" />
        </Root>
        
        <!-- SNIP -->
        
    </Loggers>
</Configuration>
```





#### 1.4.8 Full list of command-line options

Invoking JMeter as “jmeter -?” will print a list of all the command-line options. These are shown below.

```bash
--?
	print command line options and exit
-h, --help
	print usage information and exit
-v, --version
	print the version information and exit
-p, --propfile <argument>
	the jmeter property file to use

```



Note: the JMeter log file name is formatted as a SimpleDateFormat(applied to the current date) if it contains paired single quotes. e.g. `jmeter_'yyyyMMddHHmmss'.log`

If the special name `LAST` is used for the `-t`, `-j` or `-l` flags, then JMeter takes that to mean last test plan that was run in interactive mode.

#### 1.4.9 CLI mode shutdown

Prior to version 2.5.1, JMeter invoked `System.exit()` when a CLI mode test completed. This caused problems for applications that invoke JMeter directly, so JMeter no longer invokes `System.exit()` for a normal test completion[^2]. JMeter will exit all the non-daemon threads it starts, but it is possible that some non-daemon threads may still remain; these will prevent the JVM from exiting. To detect this situation, JMeter starts a new daemon thread just before it exits. This daemon thread waits a short while; if it returns from the wait, then clearly the JVM has not been able to exit, and the thread prints a message to say why.

The property `jmeter.exit.check.pause` can be used to override the default pause of 2000 ms(2 secs). If set to 0, then JMeter does not start the daemon thread.

### 1.5 Configuring JMeter

If you wish to modify the properties with which JMeter runs you need to either modify the `user.properties` in the `/bin` directory or create your own copy of the `jmeter.properties` and specify it in the command line.

> Note: You can define additional JMeter properties in the file defined by the JMeter property `user.properties` which has the default value `user.properties`. The file will be automatically loaded if it is found in the current directory or if it is found in the JMeter bin directory. Similarly, `system.properties` is used to update system properties.

| Attribute               | Description                                                  | Required |
| ----------------------- | ------------------------------------------------------------ | -------- |
| ssl.provider            | You can specify the class for your SSL implementation if you don’t want to use the built-in Java implantation. | No       |
| xml.parser              | You can specify an implementation as your XML parser. The default value is : `org.apache.xerces.parsers.SAXParser` | No       |
| remote_hosts            | Comma-delimited list of remote JMeter hosts(or host:port if required). If you are running JMeter in a distributed environment, list the machines where you have JMeter remote servers running. This will allow you to control those servers from this machine’s GUI | No       |
| not_in_menu             |                                                              |          |
| search_paths            |                                                              |          |
| user.classpath          |                                                              |          |
| plugin_dependency_paths |                                                              |          |
| user.properties         | Name of file containing additional JMeter properties. These are added after the initial property file, but before the `-q` and `-J` options are processed. | No       |
| system.properties       | Name of file containing additional system properties. These are added before the `-S` and `-D` options are processed. | No       |

The command line options and properties files are processed in the following order:

1. `-p propfile`
2. `jmeter.properties`(or the file from the `-p` option) is then loaded
3. `-j logfile`
4. Logging is initialised
5. `user.properties` is loaded
6. `system.properties` is loaded
7. all other command-line options are processed

See also the comments in the `jmeter.properties`, `user.properties` and `system.properties` files for further information on other settings you can change.

## 2. Building a Test Plan

A test plan describes a series of steps JMeter will execute when run. <u>A complete test plan will consist of one or more Thread Groups, logic controllers, sample generating controllers, listeners, timers, assertions, and configuration elements.</u>

一个完整的测试计划应当包含一个或多个线程组, 逻辑控制器, 生成取样的控制器, 监听器, timers, 断言和配置元件.

### 2.1 Adding and Removing Elements

Adding elements to a test plan can be done by right-clicking on an element in the tree, and choosing a new element from the “add” list. Alternatively, <u>elements can be loaded from file and added by choosing the “merge” or “open” option</u>.

To remove an element, make sure the element is selected, right-click on the element, and choose the “remove” option.

### 2.2 Loading and Saving Elements

To load an element from file, right click on the existing tree elements to which you want to add the loaded element, and select the “merge” option. Choose the file where your elements are saved. JMeter will merge the elements into the tree.

To save tree elements, right click on an element and choose the “Save Selection As …” option. JMeter will save the element selected, plus all child elements beneath it. In this way, you can save test tree fragments and individual elements for later use.

### 2.3 Configuring Tree Elements

Any element in the test tree will present controls in JMeter’ s right-hand frame. These controls allow you to configure the behavior of that particular test element. What can be configured for an element depends on what type of element it is.

> The Test Tree itself can be manipulated by dragging and dropping components around the test tree.

### 2.4 Saving the Test Plan

Although it is not required, we recommend that you save the Test Plan to a file before running it. To save the Test Plan, select “save” or “save Test Plan As…” from the File menu (with the latest release, it is no longer necessary to select the Test Plan element first).

> JMeter allows you to save the entire Test Plan tree or only a portion of it. To save only the elements located in a particular “branch” of the Test Plan tree, select the Test Plan element in the tree from which to start the “branch”, and then click your right mouse button to access the “<u>Save Selection As …</u>” menu item. Alternatively, select the appropriate Test Plan element and then select “<u>Save Selection As …</u>” from the Edit menu.

### 2.5 Running a Test Plan

To run your test plan, choose “Start”(`Control` + `r`) from the “Run” menu item. When JMeter is running, it shows a small green box at the right hand end of the section just under the menu bar. You can also check the “Run” menu. If “Start” is disabled, and “Stop” is enabled, then JMeter is running your test plan (or, at least, it thinks it is).

The numbers to the left of the green box are the number of active threads/total number of threads. These only apply to a locally run test; they do not include any threads started on remote systems when using client-server mode.

> Using GUI mode as described here should only be used when debugging your Test Plan. To run the real load test, use CLI mode.

### 2.6 Stopping a Test

There are two types of stop command available from the menu:

* `Stop`(`Control`+`.`) - stops the threads immediately if possible. Many samplers are Interruptible which means that active samples can be terminated early. The stop command will check that all threads have stopped within the default timeout, which is 5000 ms = 5 seconds. [This can be changed using the JMeter property `jmeterengine.threadstop.wait`] if the threads have not stopped, then a message is displayed. The Stop command can be retried, but if it fails, then it is necessary to exit JMeter to clean up.
* `Shutdown`(`Control` + `,`) - requests the threads to stop at the end of any current work. Will not interrupt any active samples. The modal shutdown dialog box will remain active until all threads have stopped.

If Shutdown is taking too long. Close the Shutdown dialog box and select Run/Stop, or just press `Control` + `.`.

When running JMeter in CLI mode, there is no Menu, and JMeter does not react to keystrokes such as `Control` + `.`. So JMeter CLI mode will listen for commands on a specific port(default 4445, see the JMeter property `jmeterengine.nongui.port`). JMeter supports automatic choice of an alternate port if the default port is being used (for example by another JMeter instance). In this case, JMeter will try the next higher port, continuing until it reaches the JMeter property `jmeterengine.nongui.maxport` which defaults to 4455. If `maxport` is less than or equal to `port`, port scanning will not take place.

The chosen port is displayed in the console window.

The commands currently supported are:

* `Shutdown` - graceful shutdown
* `StopTestNow` - immediate shutdown

These commands can be sent by using the `shutdown[.cnd|.sh]` or `stoptest[.cmd|.sh]` script respectively. The scripts are to be found in the JMeter <u>bin</u> directory. The commands will only be accepted if the script is run from the same host.

### 2.7 Error reporting

JMeter reports warnings and errors to the `jmeter.log` file, as well as some information on the test run itself. JMeter shows the number of warnings/errors found in `jmeter.log` file next to the warning icon (triangle) at the right hand end of its window. Click on the warning icon to show the `jmeter.log` file at the bottom of JMeter’ s window. Just occasionally there may be some errors that JMeter is unable to trap and log; there will appear on the command console. If a test is not behaving as you expect, please check the log file in case any errors have been reported (e.g. perhaps a syntax error in a function call).

Sampling errors(e.g. HTTP 404 - file not found) are not normally reported in the log file. Instead these are stored as attributes of the sample result. The status of a sample result can be seen in the various different Listeners.

## 3. Elements of a Test Plan

This section describes the different parts of a test plan.

A minimal test will consist of the Test Plan, a Thread Group and one more or more Samplers.

### 3.0 Test Plan

The Test Plan object has a checkbox called “<u>Functional Testing</u>”. If selected, it will cause JMeter to record the data returned from the server for each sample. If you have selected a file in your test listeners, this data will be written to file. This  can be useful if you are doing a small run to ensure that JMeter is configured correctly, and that your server is returning the expected results. The consequence is that the file will grow huge quickly, and JMeter’ s performance will suffer. This option should be off if you are doing stress-testing (it is off by default).

If you are not recording the data to file, this option makes no difference.

You can also use the <u>Configuration</u> button on a listener to decide what fields to save.

### 3.1 Thread Group

Thread group elements are the beginning points of any test plan. All controllers and samplers must be under a thread group. Other elements, e.g. Listeners, may be placed directly under the test plan, in which case they will apply to all the thread groups. As the name implies, the thread group element controls the number of threads JMeter will use to execute your test. The controls for a thread group allow you to:

* Set the number of threads
* Set the ramp-up period
* Set the number of times to execute the test

Each thread will execute the test plan in its entirety and completely independently of other test threads. Multiple threads are used to simulate concurrent connections to your server application.

The ramp-up period tells JMeter how long to take to “ramp-up” to the full number of threads chosen. If 10 threads are used, and the ramp-up period is 100 seconds, then JMeter will take 100s seconds to get all 10 threads up and running. Each thread will start 10 (100/10) seconds after the previous thread was begun. If there are 30 threads and a ramp-up period of 120 seconds, then each successive thread will be delayed by 4 seconds.

Ramp-up needs to be long enough to avoid too large work-load at the start of a test, and short enough that the last threads start running before the first ones finish(unless one wants that  to happen).

Start with Ramp-up = number of threads and adjust up or down as needed.

By default, the thread group is configured to loop once through its elements.

Thread group also provides a **scheduler**. Click the checkbox at the bottom of the Thread Group panel to enable/disable extra fields in which you can enter the duration of test, the startup delay, the start and end times of the run. You can configure <u>Duration (seconds)</u> and <u>Startup Delay (seconds)</u> to control the duration of each thread group and the after how much seconds it starts. When the test is started, JMeter will wait <u>Startup Delay (seconds)</u> before starting the Threads of the Thread Group and run for the configured <u>Duration (seconds)</u> time. Note those 2 options override the <u>Start time</u> and <u>End time</u>.

Alternatively (although not recommended as not very flexible) you can use the two other fields <u>Start time</u> and <u>End time</u>. When the test is started, JMeter will wait if necessary until the start-time has been reached. At the end of each cycle, JMeter checks if the end-time has been reached, and if so, the run is stopped, otherwise the test is allowed to continue until the iteration limit is reached.

### 3.2 Controllers

JMeter has two types of Controllers: Samplers and Logical Controllers. These drive the processing of a test.

Samplers tell JMeter to send requests to a server. For example, add an HTTP Request Sampler if you want JMeter to send an HTTP request. You can also customize a request by adding one or more Configuration Elements to a Sampler. For more information, see Samplers.

Logical Controllers let you customize the logic that JMeter uses to decide when to send requests. For example, you can add an Interleave Logic Controller to alternate between two HTTP Request Samplers. For more information, see Logical Controllers.

#### 3.2.1 Samplers

Samplers tell JMeter to send requests to a server and wait for a response. They are processed in the order they appear in the tree. Controllers can be used to modify the number of repetitions of a sampler.

JMeter samplers include:

* FTP Request
* HTTP Request(can be used for SOAP or REST Webservice also)
* JDBC Request
* Java object request
* JMS request
* JUnit Test request
* LDAP Request
* Mail request
* OS Process request
* TCP request

Each samplers has several properties you can set. You can further customize a sampler by adding one or more Configuration Elements to the Test Plan.

If you are going to send multiple requests of the same type (for example, HTTP request) to the same server, consider using a Defaults Configuration Element. Each controller has one or more Defaults elements.

Remember to add a Listener to your test plan to view and/or store the results of your requests to disk.

If you are interested in having JMeter perform basic validation on the response of your request, add an Assertion to the sampler. For example, in stress testing a web application, the server may return a successful “HTTP Response” code, but the page may have errors on it or may be missing sections. You could add assertions to check for certain HTML tags, common error strings, and so on. JMeter lets you create these assertions using regular expressions.

#### 3.2.2 Logic Controllers

Logic Controllers let you customize the logic that JMeter uses to decide when to send requests. Logic Controllers can change the order of requests coming from their child elements. They can modify the requests themselves, cause JMeter to repeat requests, etc.

To understand the effect of Logic Controllers on a test plan, consider the following test tree:

* Test Plan
	* Thread Group
		* Once Only Controller
			* Login Request(an HTTP Request)
		* Load Search Page(HTTP Sampler)
		* Interleave Controller
			* Search “A” (HTTP Sampler)
			* Search “B” (HTTP Sampler)
			* HTTP default request (Configuration Element)
		* HTTP default request (Configuration Element)
		* Cookie Manager(Configuration Element)

The first thing about this test is that the login request will be executed only the first time through. Subsequent iterations will skip it. This is due to the effects of the Once Only Controller.

After the login, the next Sampler loads the search page (imagine a web application where the user logs in, and then goes to a search page to do a search). This is just a simple request, not filtered through any Logic Controller.

After loading the search page, we want to do a search. Actually, we want to do two different searches. However, we want to re-load the search page itself between each search. We could do this by having 4 simple HTTP request elements (load search, search “A”, load search, search “B”). Instead, we use the Interleave Controller which passes on one child request each time through the test. It keeps the ordering (i.e. it doesn’t pass one on at random, but “remembers” its place) of its child elements. Interleaving 2 child requests may be overkill, but there could easily have been 8, or 20 child requests.

Note the HTTP Request Defaults that belongs to the Interleave Controller. Imagine that “Search A” and “Search B” share the same PATH info (an HTTP request specification includes domain, port, method, protocol, path, and arguments, plus other optional items). This makes sense - both are search requests, hitting the same back-end search engine (a servlet or cgi-script, let’ say). Rather than configure both HTTP Samplers with the same information in their PATH field, we can abstract that information out to a single Configuration Element. When the interleave Controller “passes on” requests from “Search A” or “Search B”, it will fill in the blanks with values from the HTTP default request Configuration Element. So, we leave the PATH field blank for those requests, and put that information into the Configuration Element. In this case, this is a minor benefit at best, but it demonstrates that feature.

The next element in the tree is another HTTP default request, this time added to the Thread Group itself. The Thread Group has a built-in Logic Controller, and thus, it uses this Configuration Element exactly as described above. It fills in the blanks of any Request that passes through. It is extremely useful in web testing to leave the DOMAIN field blank in all your HTTP Sampler elements, and instead, put that information into an HTTP default request element, added to the Thread Group. By doing so, you can test your application on a different server simply by changing one field in your Test Plan. Otherwise, you’d have to edit each and every Sampler.

The last element is a HTTP Cookie Manger. A Cookie Manager should be added to all web tests - otherwise JMeter will ignore cookies. By adding it at the Thread Group level, we ensure that all HTTP requests will share the same cookies.

Logic Controllers can be combines to achieve various results. See the list of built-in Logic Controllers.

#### 3.2.3 Test Fragments

The Test Fragment element is a special type of controller that exists on the Test Plan tree at the same level as the Thread Group element. It is distinguished from a Thread Group in that it is not executed unless it is referenced by either a <u>Module Controller</u> or an <u>Include Controller</u>.

This element is purely for code re-use within Test Plans

### 3.3 Listeners

Listeners provide access to the information JMeter gathers about the test cases while JMeter runs. The <u>Graph Results</u> listener plots the response times on a graph. The “View Results Tree” Listeners shows details of sampler requests and responses, and can display basic HTML and XML representations of the response. Other listeners provide summary or aggregation information.

 Additionally, listeners can direct the data to a file for later use. Every listener in JMeter provides a field to indicate the file to store data to. There is also a Configuration button which can be used to choose which fields to save, and whether to use CSV or XML format.

> Note that all listeners save the same data; the only difference is in the way the data is presented on the screen.

Listeners can be added anywhere in the test, including directly under the test plan. They will collect data only from elements at or below their level.

There are several listeners that come with JMeter.

### 3.4 Timers

By default, a JMeter thread executes samplers in sequence without pausing. We recommend that you specify a delay by adding one of the available timers to your Thread Group. If you do not add a delay, JMeter could overwhelm your server my making too many requests in a very short amount of time.

A timer will cause JMeter to delay a certain amount of time before each sampler which is in its scope.

If you choose to add more than one timer to a Thread Group, JMeter takes the sum of the timers and pauses for that amount of time before executing the samplers to which the timers apply. Timers can be added as children of samplers or controllers in order to restrict the samplers to which they are applied.

To provide a pause at a single place in a test plan, one can use the Flow Control Action Sampler.

### 3.5 Assertions

Assertions allow you to assert facts about responses received from the server being tested. Using an assertion, you can essentially “test” that your application is returning the results you expect it to.

For instance, you can assert that the response to a query will contain some particular text. The text you specify can be a Perl-style regular expression, and you can indicate that the response is to contain the text, or that it should match the whole response.

You can add an assertion to any Sampler. For example, you can add an assertion to a HTTP Request that checks for the text, “</HTML>”. JMeter will then check that the text is present in the HTTP response. If JMeter cannot find the text, then it will mark this as a failed requeset.

> Note that assertions apply to all samplers which are in their scope. To restrict an assertion to a single sampler, add the assertion as a child of the sampler.

To view assertion results, add an Assertion Listener to the Thread Group. Failed Assertions will also show up in the Tree View and Table Listeners, and will count towards the error % age for example in the Aggregate and Summary reports.

### 3.6 Configuration Elements

A configuration element works closely with a Sampler. Although it doe not send requests (except for <u>HTTP(s) Test Script Recorder</u>), it can add to or modify requests.

A configuration element is accessible from only inside the tree branch where you place the element. For example, if you place an HTTP Cookie Manager inside a Simple Logic Controller, the Cookie Manger will only be accessible to HTTP Request Controllers you place inside the Simple Logic Controller. The Cookie Manager is accessible to the HTTP requests “Web Page 1” and “Web Page 2”, but not “Web Page 3”.

Also, a configuration element inside a tree branch has higher precedence than the same element in a “parent” branch. For example, we defined two HTTP Request Defaults elements, “Web Defaults 1” and “Web Defaults 2”. Since we placed  “Web Defaults 1” inside a Loop Controller, only “Web Page 2” can access it. The other HTTP requests will use “Web Defaults 2”, since we placed it in the Thread Group (the “parent” of all other branches).

> The <u>User Defined Variables</u> Configuration element is different. It is processed at the start of a test, no matter where it is placed. For simplicity, it is suggested that the element is placed only at the start of a Thread Group.

### 3.7 Pre-Processor Elements

A Pre-Processor executes some action prior to a Sampler Request being made. If a Pre-Processor is attached to a Sampler element, then it will execute just prior to that sampler element running. A Pre-Processor is most often used to modify the settings of a Sample Request just before it runs, or to update variables that aren’t extracted from response text. See the <u>scoping rules</u> for more details on when Pre-Processors are executed.

### 3.8 Post-Processor Elements

A Post-Processor executes some action after a Sampler Request has been made. If a Post-Processor is attached to a Sampler element, then it will execute just after that sampler element runs. A Post-Processor is most often used to process the response data, often to extract values from it. See the scoping rules for more details on when Post-Processors are executed.

### 3.9 Execution order

0. Configuration elements
1. Pre-Processors
2. Timers
3. Sampler
4. Post-Processors(unless SampleResult is null)
5. Assertions (unless SampleResult is null)
6. Listeners (unless SampleResult is null)

> Please note that Timers, Assertions, Pre- and Post-Processors are only processed if there is a sampler to which they apply. Logic Controllers and Samplers are processed in the order in which they appear in the tree. Other test elements are processed according to the scope in which they are found, and the type of test element.  [Within a type, elements are processed in the order in which they appear in the tree].

For example, in the following test plan:

* Controller
	* Post-Processor 1
	* Sampler 1
	* Sampler 2
	* Timer 1
	* Assertion 1
	* Pre-Processor 1
	* Timer 2
	* Post-Processor 2

The order of execution would be:

```shell
Pre-Processor 1
Timer 1
Timer 2
Sampler 1
Post-Processor 1
Post-Processor 2
Assertion 1

Pre-Processor 1
Timer 1
Timer 2
Sampler 2
Post-Processor 1
Post-Processor 2
Assertion 1
```

### 3.10 Scoping Rules

The JMeter test tree contains elements that are both hierarchical and ordered. Some elements in the test trees are strictly hierarchical (Listeners, Config Elements, Post-Processors, Pre-Processors, Assertions, Timers), and some are primarily ordered (controllers, samplers). When you create your test plan, you will create an ordered list of sample request (via Samplers) that represent a set of steps to be executed. These requests are often organized within controllers that are also ordered. Given the following test tree:

JMeter test tree中包含的元素都是分级且有序的。有些元素，比如Listener, Config, Post-Processors, Pre

* Test Plan
	* Thread Group
		* one
		* Simple Controller
			* Two
			* Three
		* Four

The order of requests will be, One, Two, Three, Four.

Some controllers affect the order of their subelements, and you can read about these specific controllers in the component reference.

Other elements are hierarchical. An Assertion, for instance, is hierarchical in the test tree. If its parent is a request, then it is applied to that request. If its parent is a Controller, then it affects all requests that are descendants of that Controller. In the following test tree:

* Test Plan
	* Thread Group
		* One
			* Assertion #1
		* Simple Controller
			* Two
			* Three
			* Assertion #2
		* Four

Assertion #1 is applied only to Request One, while Assertion #2 is applied to Requests Two and Three.

Another example, this time using Timers:

* Test Plan
	* Thread Group
		* One
		* Simple Controller
			* Two
			* Timer #1
			* Three
				* Assertion #1
			* Simple Controller
				* Four
		* Five
		* Timer #2

In this example, the requests are named to reflect the order in which they will be executed. Timer #1 will apply to Requests Two, Three, and Four (notice how order is irrelevant for hierarchical elements). Assertion #1 will apply only to Request Three. Timer #2 will affect all the requests.

Hopefully these examples make it clear how configuration (hierarchical) elements are applied. If you imagine each Request being passed up the tree branches, to its parent, then to its parent’s parent, etc., and each time collecting all the configuration elements of that parent, then you will see how it works.

> The Configuration elements Header Manager, Cookie Manager and Authorization manager are treated differently from the Configuration Default elements. The settings from the Configuration Default elements are merged into a set of values that the Sampler has access to. However, the settings from the Managers are not merged. If more than one Manager is in the scope of a Sampler, only one Manager is used, but there is currently no way to specify which is used.

### 3.11 Properties and Variables

JMeter properties are defined in `jmeter.properties` .

Properties are global to jmeter, and are mostly used to define some of the defaults JMeter uses. For example the property `remote_hosts` defines the servers that JMeter will try to run remotely. Properties can be referenced in test plans - but cannot be used for thread-specific values.

JMeter *variables* are local to each thread. The values may be the same for each thread, or they may be different.

If a variable is updated by a thread, only the thread copy of the variable is changed. For example the Regular Expression Extractor Post-Processor will set its variables according to the sample that its thread has read, and these can be used later by the same thread. For details of how to reference variables and functions, see Functions and Variables

Note that the values defined by the <u>Test Plan</u> and the <u>User Defined Variables</u> configuration element are made available to the whole test plan at startup. If the same variable is defined by multiple UDV elements, then the last one takes effect. Once a thread has started, the initial set of variables is copied to each thread. Other elements such as the <u>User Parameters</u> Pre-Processor or <u>Regular Expression Extractor</u> Post-Processor may be used to redefine the same variables (or create new ones). These redefinitions only apply to the current thread.

The `setProperty` function can be used to define a JMeter property. These are global to the test plan, so can be used to pass information between threads - should that be needed.

> Both variables and properties are case-sensitive.

### 3.12 Using Variables to parameterize tests

Variables don’t have to vary - they can be defined once, and if left alone, will not change value. So you can use them as short-hand for expressions that appear frequently in a test plan. Or for items which are constant during a run, but which may vary between runs. For example, the name of a host, or the number of threads in a thread group.

When deciding how to structure a Test Plan, make a note of which items are constant for the run, but which may change between runs. Decide on some variable names for these - perhaps use a naming convention such as prefixing them with `C_` or `K_` or using uppercase only to distinguish them from variables that need to change during the test. Also consider which items need to be local to a thread - for example counters or values extracted with the Regular Expression Post-Processor. You may wish to use a different naming convention for these.

For example, you might define the following on the Test Plan:

```shell
HOST			www.example.com
THREADS			10
LOOPS			20
```

You can refer to these in the test plan as `${HOST}` `${THREADS}` etc. if you later want to change the host, just change the value of the HOST variable. This works fine for small numbers of tests, but becomes tedious when testing lots of different combinations. One solution is to use a property to define the value of the variables, for example:

```shell
HOST			${__p(host,www.example.com)}
THREADS			${__P(threads,10)}
LOOPS			${__P(loops,20)}
```

You can then change some or all of the values on the command-line as follows:

```shell
jmeter ... -Jhost=www3.example.org -Jloops=13
```

## 4. Building a Web Test Plan

In this section, you will learn how to create a basic <u>Test Plan</u> to test a Web site. You will create five users that send requests to two pages on the JMeter Website. Also, you will tell the users to run their tests twice. So, the total number of requests is (5 users) x (2 requests) x (repeat 2 times) = 20 HTTP requests. To construct the Test Plan, you will use the following elements: <u>Thread Group</u>, <u>HTTP Request</u>, <u>HTTP Request Defaults</u>, and <u>Graph Results</u>.

### 4.1 Adding Users

The first step you want to do with every JMeter Test Plan is add a <u>Thread Group</u> element. ==The Thread Group tells JMeter <u>the number of users you want to simulate</u>, <u>how often the users should send requests</u>, and <u>how many requests they should send</u>.==

线程组会告诉JMeter你想要模拟的用户数，用户发送请求的频率，以及最终一共发送多少请求。

Go ahead and add the ThreadGroup element by first selecting the Test Plan, clicking your right mouse button to get the Add menu, and then select Add -> ThreadGroup.

You should now see the Thread Group element under Test Plan. If you do not see the element, then “expand” the Test Plan tree by clicking on the Test Plan element.

Next, you need to modify the default properties. Select the Thread Group element in the tree, if you have not already selected it. You should now see the Thread Group Control Panel in the right section of the JMeter window.

![](https://jmeter.apache.org/images/screenshots/webtest/threadgroup.png)

Starting by providing a more descriptive name for our Thread Group. In the name field, enter JMeter Users.

Next, increase the number of users (called threads) to 5

In the next field, the Ramp-Up Period, leave the default value of 1 seconds. This property tells JMeter how long to delay between starting each other. For example, if you enter a Ramp-Up Period of 5 seconds, JMeter will finish starting all of your users by the end of the 5 seconds. So, if we have 5 users and a 5 second Ramp-Up Period, then the delay between starting users would be 1 second (5 users / 5 seconds = 1 user per second). ==If you set the value to 0, then JMeter will immediately start all of your users.==

Finally enter a value of 2 in the Loop Count field. This property tells JMeter how many times to repeat your test. If you enter a loop count value of 1, then JMeter will run your test only once. To have JMeter repeatedly  run our Test Plan, select the Forever checkbox.

> In most applications, you have to manually accept changes you make in a Control Panel. However, in JMeter, the Control Panel automatically accepts your changes as you make them. If you change the name of an element, the tree will be updated with the new text after you leave the Control Panel (for example, when selecting another tree element).

See Figure 4.2 for the completed JMeter Users Thread Group.

![](https://jmeter.apache.org/images/screenshots/webtest/threadgroup2.png)

### 4.2 Adding Default HTTP Request Properties

Now that we have defined our users, it is time to define the tasks that they will be performing. In this section, you will specify the default settings for your HTTP requests. And then, in section 4.3 , you will add HTTP Request elements which use some of the default settings you specified here.

Begin by selecting the JMeter Users(Thread Group) element. Click your right mouse button to get the Add menu, and then select Add -> Config Element -> HTTP Request Defaults. Then select this new element to view its Control Panel

Like most JMeter elements, the HTTP Request Defaults Control Panel has a name field that you can modify. In this example, leave this field with the default value.

Skip to the next field, which is the Web Server’s Server Name/IP. For the Test Plan that you are building, all HTTP requests will be sent to the same Web server, `jmeter.apache.org`. Enter this domain name into the field. This is the only field that we will specify a default, so leave the remaining fields with their default values.

> The HTTP Request Defaults element does not tell JMeter to send an HTTP request. It simply defines the default values that the HTTP Request elements use.

![](https://jmeter.apache.org/images/screenshots/webtest/http-defaults2.png)



### 4.3 Adding Cookie Support

Nearly all web testing should use cookie support, unless your application specifically doesn’t use cookies. To add cookie support, simply add an HTTP Cookie Manager to each Thread Group in your test plan. This will ensure that each thread gets its own cookies, but shared across all HTTP Request objects.

几乎所有的Web测试都应该使用cookie支持, 除非你的应用指明不使用cookie. 使用cookie支持的方法是: 在每个线程组里都添加一个HTTP Cookie Manager. 这样每个线程就能有自己的cookies, 而且每个HTTP 请求都可以共享cookies.

### 4.4 Adding HTTP Requests

> JMeter sends requests in the order that they appear in the tree.
>
> JMeter 是根据请求在树中出现的顺序来发送的.

### 4.5 Adding a Listener to View Store the Test Results

The final element you need to add to your Test Plan is a Listener. This element is responsible for storing all of the results of your HTTP requests in a file and presenting a visual model of the data.

最后需要添加到Test Plan的元件是监听器. 这个元件负责把所有HTTP请求的返回结果存储到文件中, 并且把结果按模型的方式展示出来.

Select the JMeter Users element and add Graph Results listener

### 4.6 Logging in to a web-site

It’s not the case here, but some websites require you to login before permitting you to perform certain actions. In a web-browser, the login will be shown as a form for the user name and password, and a button to submit the form. The button generates a POST request, passing the values of the form items as parameters.

To do this in JMeter, add a HTTP Request, and set the method to POST. You’ll need to know the names of the fields used by the form, and the target page. These can be found out by inspecting the code of the login page. [If this is difficult to do, you can use the <u>JMeter Proxy Recorder</u> to record the login sequence.] ==Set the path to the target of the submit button==. Click the Add button twice and enter the username and password details. Sometimes the login form contains additional hidden fields. These will need to be added as well.

登录页面的路径要设为提交按钮的路径.如果提交表单还有其他隐藏字段的话, 也需要加上.

### 4.7 choose the same user or different users

When creating a Test Plan, on each Thread Group iteration, we can choose to simulate the same user running multiple iterations, or different users running one iteration. You can configure this behavior on Thread Group element, and have HTTP Cache Manager, HTTP Cookie Manager, HTTP Authorization Manager controlled by this setting.

当创建一个Test Plan时, 在每个Thread Group循环的时候, 我们可以选择同一批用户反复循环, 还是不同用户跑一个循环. 

## 5. Building an Advanced Web Test Plan

### 5.1 Handling User Sessions With URL Rewriting

If your web application uses URL rewriting rather than cookies to save session information, then you’ll need to do a bit of extra work to test your site.

To respond correctly to URL rewriting, JMeter needs to parse the HTML received from the server and retrieve the unique session ID. Use the appropriate <u>HTTP URL Re-writing Modifier</u> to accomplish this. Simply enter the name of your session ID parameter into the modifier, and it will find it and add it to each request. If the request already has a value, it will be replaced. If “Cache Session id?” is checked, then the last found session id will be saved, and will be used if the previous HTTP sample does not contain a session id.

### 5.2 Using a Header Manager

The <u>HTTP Header Manager</u> lets you customize what information JMeter sends in the HTTP request header. This header includes properties like “User-Agent”, “Pragma”, “Referer”, etc.

The <u>HTTP Header Manager</u>, like the <u>HTTP Cookie Manager</u>, should probably be added at the Thread Group level, unless for some reason you wish to specify different headers for the different <u>HTTP Request</u> objects in your test.

Building a Database Test Plan

## 12. Introduction to listeners

A listener is a component that shows the results of the samples. The results can be shown in a tree, tables, graphs or simply written to a log file. To view the contents of a response from any given sampler, add either of the Listeners “View Results Tree” or “View Results in table” to a test plan. To view the response time graphically, add graph results. The listeners section of the components page has full descriptions of all the listeners.

监听器是一个展示取样器结果的元件. 取样结果可以是一棵树, 表格, 图案或者直接写入到一个日志文件中. 

> Different listeners display the response information in different ways. However, they all write the same raw data to the output file - if one is specified.

The “Configure” button can be used to specify which fields to write to the file, and whether to write it as CSV or XML. CSV files are much smaller than XML files, so use CSV if you are generating lots of samples.

The file name can be specified using either a relative or an absolute path name. Relative paths are resolved relative to the current working directory (which defaults to the bin/ directory). JMeter also supports paths relative to the directory containing the current test plan (JMX file). If the path name begins with “~/” (or whatever is in the `jmeter.save.saveservice.base_prefix` JMeter property), then the path is assumed to be relative to the JMX file location.

If you only wish to record certain samples, add the Listener as a child of the sampler. Or you can use a Simple Controller to group a set of samplers, and add the Listener to that. The same filename can be used by multiple samplers - but make sure they all use the same configuration!

### 12.1 Default Configuration

The default items to be saved can be defined in the `jmeter.properties` (or `user.properties`) file. The properties are used as the initial settings for the Listener Config pop-up, and are also used for the log file specified by the `-l` command-line flag (commonly used for CLI mode test runs).

To change the default format, find the following line in `jmeter.properties`:

```shell
jmeter.save.saveservice.output_format=
```

The information to be saved is configurable. For maximum information, choose “xml” as the format and specify “Functional Test Mode” on the Test Plan element. If this box is not checked, the default saved data includes a time stamp (the number of milliseconds since midnight, January 1, 1970 UTC), the data type, the thread name, the label, the response time, message, and code, and a success indicator. If checked, all information, including the full response data will be logged.

The following example indicates how to set properties to get a vertical bar(“|”) delimited format that will output results like:.

```properties
timeStamp|time|label|responseCode|threadName|dataType|success|failureMessage
02/06/03 08:21:42|1187|Home|200|Thread Group-1|text|true|
02/06/03 08:21:42|47|Login|200|Thread Group-1|text|false|Test Failed:
    expected to contain: password etc.
```

The corresponding `jmeter.properties` that need to be set are shown below. One oddity in this example is that the output_format is set to CSV, which typically indicates comma-separated values. However, the default_delimiter was set to be a vertical bar instead of a comma, so the CSV tag is a misnomer in this case. (Think of CSV as meaning character separated values)

```properties
jmeter.save.saveservice.output_format=csv
jmeter.save.saveservice.assertion_results_failure_message=true
jmeter.save.saveservice.default_delimiter=|
```

还有一些其他的设置...没抄

#### 12.1.1 Sample Variables

JMeter supports the `sample_variables` property to define a list of additional JMeter variables which are to be saved with each sample in the JTL files. The values are written to CSV files as additional columns, and as additional attributes in XML files. See above for an example.

#### 12.1.2 Sample Result Save Configuration

Listeners can be configured to save different items to the result log files(JTL) by using the Config popup as shown below. The defaults are defined as described in the Listener Default Configuration section above. Items with (CSV) after the name only apply to the CSV format; items with (XML) only apply to XML format. CSV format cannot currently be used to save any items that include line-breaks.

![](https://jmeter.apache.org/images/screenshots/sample_result_config.png)

Note that cookies, method and the query string are saved as part of the “Sampler Data” option.

### 12.2 CLI mode (batch) test runs

When running in CLI mode, the `-l` flag can be used to create a top-level listener for the test run. This is in addition to any Listener defined in the test plan. The configuration of this listener is controller by entries in the file `jmeter.properties` as described in the previous section.

This feature can be used to specify different data and log files for each test run, for example:

```shell
jmeter -n -t testplan.jmx -l testplan_01.jtl -j testplan_01.log
jmeter -n -t testplan.jmx -l testplan_02.jtl -j testplan_02.log
```

Note that ==JMeter logging messages are written to the file `jmeter.log` by default. This file is recreated each time, so if you want to keep the log files for each run, you will need to rename it using the `-j` option== as above.

JMeter supports variables in the log file name. If the filename contains paired single-quotes, then the name is processed as a `SimpleDateFormat` format applied to the current date, for example: `log_file='jmeter_'yyyyMMddHHmmss'.tmp’`. This can be used to generate a unique name for each test run.

### 12.3 Resource usage

> Listeners can user a lot of memory if there are a lot of samples.

Most of the listeners currently keep a copy of every sample they display, apart from:

* Simple Data Writer
* BeanShell/JSR223 Listener
* Mailer Visualizer
* Monitor Results
* Summary Report

The following Listeners no longer need to keep copies of every single sample. Instead, samples with the same elapsed time are aggregated. Less memory is now needed, especially if most samples only take a second or two at most.

* Aggregate Report
* Aggregate Graph

To minimize the amount of memory needed, use the Simple Data Writer, and use the CSV format.

### 12.4 CSV Log format

The CSV log format depends on which data items are selected in the configuration. Only the specified data items are recorded in the file. The order of appearance of columns is fixed, and is as follows:

* timeStamp - in milliseconds since 1/1/1970
* elapsed - in milliseconds
* label - sampler label
* responseCode - e.g. 200, 404
* responseMessage - e.g. OK
* threadName
* dataType - e.g. text
* success - true or false
* failureMessage - if any
* bytes - number of bytes in the sample
* sentBytes - number of bytes in the sample
* grpThreads - number of active threads in this thread group
* allThreads - total number of active threads in all groups
* URL
* Filename - if Save Response to File was used
* latency - time to first response
* connect - time to establish connection
* encoding
* SampleCount - number of samples (1, unless multiple samples are aggregated)
* ErrorCount - number of errors (0 or 1, unless multiple samples are aggregated)
* Hostname - where the sample was generated
* IdleTime - number of milliseconds of ‘Idle’ time (normally 0)
* Variables, if specified

### 12.5 XML Log format 2.1

The format of the updated XML (2.1) is as follows (line breaks will be different):

具体的图查看教程...目前看不懂

Note that the sample node name may be either “sample” or “httpSample”.

### 12.6 XML Log format 2.2

The format of the JTL files is identical for 2.2 and 2.1. Format 2.2 only affects JMX files.

### 12.7 Sample Attributes

The sample attributes have the following meaning:

| Attribute | Content                                                      |
| --------- | ------------------------------------------------------------ |
| by        | Bytes                                                        |
| sby       | Sent Bytes                                                   |
| de        | Data encoding                                                |
| dt        | Data type                                                    |
| ec        | Error count (0 or 1, unless multiple samples are aggregated) |
| hn        | Hostname where the sample was generated                      |
| it        | Idle Time = time not spent sampling (milliseconds) (generally 0) |
| lb        | Label                                                        |
| lt        | lantency = time to initial response (milliseconds) - not all samplers support this |
| ct        | Connect Time = time to establish the connection (milliseconds) - not all samplers support this |
| na        | Number of active threads for all thread groups               |
| ng        | Number of active threads in this group                       |
| rc        | Response Code (3.g. 200)                                     |
| rm        | Response Message (e.g. OK)                                   |
| s         | Success flag (true/false)                                    |
| sc        | Sample count (1, unless multiple samples are aggregated)     |
| t         | Elapsed time (milliseconds)                                  |
| tn        | Thread Name                                                  |
| ts        | timeStamp (milliseconds since midnight Jan 1, 1970 UTC)      |
| varname   | Value of he named variable                                   |

> JMeter allows additional variables to be saved with the test plan. Currently, the variables are saved as additional attributes. The test-plan variable name is used as the attribute name. See <u>Sample variables</u> for more information.

### 12.8 Saving response data

As shown above, the response data can be saved in the XML log file if required. However, this can make the file rather large, and the text has to be encoded so that it is still valid XML. Also, images cannot be included. Only sample responses with the type TEXT can be saved.

Another solution is to use the Post-Processor <u>Save Responses to a file</u>. This generates a new file for each sample, and saves the file name with the sample. The file name can then be included in the sample log output. The data will be retrieved from the file if necessary when the sample log file is reloaded.

### 12.9 Loading(reading) response data

To view an existing results file, you can use the File “Browse…” button to select a file. If necessary, just create a dummy test-plan with the appropriate Listener in it.

Results can be read from XML or CSV format files. When reading from CSV results files, the header (if present) is used to determine which fields were saved. <u>In order to interpret a header-less CSV file correctly, the appropriate JMeter properties must be set.</u>

> JMeter does not clear any current data before loading the new file thus allowing files to be merged. If you want to clear the current data, use the menu item: Run-> Clear(Ctrl+Shift+E) or Run->Clear All(Ctrl+E) before loading the file.

### 12.10 Saving Listener GUI data

JMeter is capable of saving any listener as a PNG file. To do so, select the listener in the left panel. Click Edit -> Save Node As Image. A file dialog will appear. Enter the desired name and save the listener.

The Listeners which generate output as tables can also be saved using Copy/Paste. Select the desired cells in the table, and use the OS Copy short-cut (normally Ctrl+C). The data will be saved to the clipboard, from where it can be pasted into another application, e.g. a spreadsheet or text editor.

## 13. Remote Testing

### 13.1 Setting up SSL

### 13.2 Doing it Manually

### 13.3 Tips

### 13.4 Using a different port

### 13.5 Using a different sample sender

### 13.6 Dealing with nodes that failed starting

### 13.7 Using a security-manager



## 14. Generating Report Dashboard

JMeter supports dashboard report generation to get graphs and statistics from a test plan.

This chapter describes how to configure and use the generator.

### 14.1 Overview

The dashboard generator is a modular extension of JMeter. Its default behavior is to read and process samples from CSV files to generate HTML files containing graph views. It can generate the report at end of a load test or on demand.

This report provides the following metrics:

* APDEX (Application Performance Index) table that computes for every transaction the APDEX based on configurable values for tolerated and satisfied thresholds
* A request summary graph showing the Success and failed requests (Transaction Controller Sample Results are not taken into account) percentage:
* A Statistics table providing in one table a summary of all metrics per transaction including 3 configurable percentiles:
* An error table providing a summary of all errors and their proportion in the total requests:
* A Top 5 Errors by Sampler table providing for every Sampler (excluding Transaction Controller by default) the top 5 Errors:
* Zoomable chart where you can check/uncheck every transaction to show/hide it for:
	* Response times Over Time (includes Transaction Controller Sample Results):
	
	* Response times Percentiles Over Time(successful responses only):
	
	* Active Threads Over Time:
	
	* Bytes throughput Over Time (Ignored Transaction Controller Sample Results):
	
	* Latencies Over Time(Includes Transaction Controller Sample Results):
	
	* Connect Time Over Time (Includes Transaction Controller Sample Results):
	
	* Hits per second (Ignores Transaction Controller Sample Results):
	
	* Response codes per second (Ignores Transaction Controller Sample Results):
	
	* Transactions per second (Includes Transaction Controller Sample Results):
	
	* Response Time vs Request per second (Ignores Transaction Controller Sample Results):
	
	* Latency vs Request per second (Ignores Transaction Controller Sample Results):
	
	* Response time Overview (Excludes Transaction Controller Sample Results):
	
	* Response times percentiles (Includes Transaction Controller Sample Results):
	
	* Times vs Threads (Includes Transaction Controller Sample Results):
	
	  > In distributed mode, this graph shows a horizontal axis the number of threads for 1 server. It’s a current limitation.
	
	* Response Time Distribution (Includes Transaction Controller Sample Results):

### 14.2 Configuring Dashboard Generation

Dashboard generation uses JMeter properties to customize the report. Some properties are used for general settings and others are used for a particular graph configuration or exporter configuration.

> All report generator properties can be found in file `reportgenerator.properties`. To customize these properties, you should copy them in `user.properties` file and modify them.

#### 14.2.1 Requirements

##### 14.2.1.1 Filtering Configuration

Ensure you set property `jmeter.reportgenerator.exporter.html.series_filter` to keep only the transactions you want in the report if you don’t want everything.

In the example below you must only modify `Search|Order`, keep the rest:

```properties
jmeter.reportgenerator.exporter.html.series_filter=^(Search|Order)(-success|-failure)?$
```

##### 14.2.1.2 Save Service configuration

To enable the generator to operate, the CSV file generated by JMeter must include certain required data which <u>are correct by default in the last live version</u> of JMeter.

If you modified those settings, check that your JMeter configuration follows these settings (these are the defaults):

```properties
jmeter.save.saveservice.bytes = true
# Only available with HttpClient4
# jmeter.save.saverservice.sent_bytes=true
jmete.save.saveservice/lable = true
...
```

##### 14.2.1.3 Transaction Controller configuration

事务控制器...目前还不知道是干嘛的..这个小标题先不写了.

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

The performance of JMeter is being constantly improved, so users are highly encouraged to use the most up to date version.

Ensure you always read changes list to be aware of new improvements and components. You should absolutely avoid using versions that are older than 3 versions before the last one.

### 16.2 Use the correct Number of Threads

Your hardware capabilities as well as the Test Plan design will both impact the number of threads you can effectively run with JMeter. The number will also depend on how fast your server is (a faster server makes JMeter work harder since it returns a response quicker). As with any Load Testing tool, if you don’t correctly size the number of threads, you will face the “<u>Coordinated Omission</u>[^4]” problem which can give you wrong or inaccurate results. If you need large-scale load testing, consider running multiple CLI JMeter instances on multiple machines using distributed mode (or not). When using distributed mode the result file is combined on the Controller node, if using multiple autonomous instances, the sample result files can be combined for subsequent analysis. For testing how JMeter performs on a given platform, the Java Test sampler can be used. It does not require any network access so can give some idea as to the maximum throughput achievable.

JMeter has an option to delay thread creation until the thread starts sampling, i.e. after any thread group delay and the ramp-up time for the thread itself. This allows for a very large total number of threads, provided that not too many are active concurrently.

### 16.3 Where to Put the Cookie Manager

See Building a Web Test for information.

### 16.4 Where to Put the Authorization Manager

See Building an Advanced Web Test for information.

### 16.5 Using the HTTP(S) Test Script Recorder

Refer to HTTP(S) Test Script Recorder for details on setting up the recorder. The most important thing to do is filter out all requests you aren’t interested in. For instance, there’s no point in recording image requests(JMeter can be instructed to download all images on a page). These will just clutter your test plan. Most likely, these is an extension all your files share, such as `.jsp`, `.asp`, `.php`, `.html` or the like. These you should “include” by entering “`.*\.jsp*`” as an “Include Pattern”.

### 16.6 User variables



### 16.7 Reducing resource requirements



### 16.8 BeanShell server



### 16.9 BeanShell scripting

> Since JMeter 3.1, we advise switching from BeanShell to JSR223 Test Elements, and switching from `__Beanshell` function to `__groovy` function.

#### 16.9.1 Overview

**Each BeanShell test element has its own copy of the interpreter (for each thread)**. If the test element is repeatedly called, e.g. within a loop, then the interpreter is retained between invocations unless the “`Reset bsh.Interpreter before each call`” option is selected.

Some long-running tests may cause the interpreter to use lots of memory; if this is the case try using the reset option.

you can test BeanShell scripts outside JMeter by using the command-line interpreter:

```bash
$ java -cp bsh-xxx.jar[;other jars as needed] bsh.Interpreter file.bsh [parameters]
```

or

```bash
$ java -cp bsh-xxx.jar bsh.Interpreter
bsh% source("file.bsh");
bsh% exit(); // or use EOF key (e.g. ^Z or ^D)
```

#### 16.9.2 Sharing Variables

Variables can be defined in startup (initialization) scripts. These will be retained across invocations of the test element, unless the reset option is used.

Scripts can also access JMeter variables using the `get()` and `put()` methods of the “vars” variable, for example:

```bash
vars.get("HOST")
vars.put("MSG", "Successful")
```

**The `get()` and `put()` methods only support variables with String values, but there are also `getObject()` and `putObject()` methods which can be used for arbitrary objects.** J<u>Meter variables are local to a thread, but can be used by all test elements (not just BeanShell).</u>

If you need to share variables between threads, then JMeter properties can be used:

```bash
import org.apache.jmeter.util.JMeterUtils;
String value = JMeterUtils.getPropDefault("name", "");
JMeterUtils.setProperty("name", "value");
```

The sample `.bshrc` files contain sample definitions of `getprop()` and `setprop()` methods.

Another possible method of sharing variables is to use the “`bsh.shared`” shared namespace. For example:

```java
if (bsh.shared.myObj == void){
	// not yet defined, so create it:
	myObj = new AnyObject();
}
bsh.shared.myObj.process()l
```

Rather than creating the object in the test element, it can be created in the startup file defined by the JMeter property “`beanshell.init.file`”. This is only processed once.

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

## 18. Component Reference

### 18.1 Samplers

#### HTTP Request

This sampler lets you send an HTTP/HTTPS request to a web server. <u>It also lets you control whether or not JMeter parses HTML files for images and other embedded resources and sends HTTP requests to retrieve them.</u> The following types of embedded resource are retrieved:

* images
* applets
* stylesheets(CSS) and resources referenced from those files
* external scripts
* frames, iframes
* background images(body, table, TD, TR)
* background sound

The default parser is `org.apache.jmeter.protocol.http.parser.LagartoBaseHtmlParser`. This can be changed by using the property “`htmlparser.className`” - see `jmeter.properties` for details.

If you are going to send multiple requests to the same web server, consider using an <u>HTTP Request Defaults</u>

Configuration Element so you do not have to enter the same information for each HTTP Request.

Or, instead of manually adding HTTP Requests, you may want to use <u>JMeter’ s HTTP(S) Test Script Recorder</u> to create them. This can save you time if you have a lot of HTTP requests or requests with many parameters.

There are three different test elements used to define the samplers:

* AJP/1.3 Sampler

  uses the Tomcat mod_jk protocol (allows testing of Tomcat in AJP mode without needing Apache httpd) The AJP Sampler does not support multiple file upload; only the first file will be used.

* HTTP Request

  This has an implementation drop-down box, which selects the HTTP protocol implementation to be used:

  ​	Java

  ​			uses the HTTP implementation provided by the JVM. This has some limitations in comparison with the HttpClient implementations - see below.

  ​	HTTPClient4

  ​			uses Apache HttpComponents HttpClient 4.x.

  ​	Blank Value

  ​			does not set implementation on HTTP Samplers, so relies on HTTP Request Defaults if present 

  ​			or on `jmeter.httpsampler` property defined in `jmeter.properties`

* GraphQL HTTP Request

  This is a GUI variation of the HTTP Request to provide more convenient UI elements to view or edit GraphQL <u>Query</u>, <u>Variables</u> and <u>Operation Name</u>, while converting them into HTTP Arguments automatically under the hood using the same sampler. This hides or customizes the following UI elements as they are less convenient for or irrelevant to GraphQL over HTTP/HTTPS requests:

  * <u>Method</u>: only POST and GET methods are available conforming the GraphQL over HTTP specification. POST method is selected by default.
  * <u>Parameters</u> and <u>Post Body</u> tabs: you may view or edit parameter content through Query, Variables and Operation Name UI elements instead.
  * <u>File Upload</u> tab: irrelevant to GraphQL queries.
  * <u>Embedded Resources from HTML files</u> section in the Advanced tab: irrelevant in GraphQL JSON responses.

The Java HTTP implementation has some limitations:

* There is no control over how connections are re-used. When a connection is released by JMeter, it may or may not be reused by the same thread.
* The API is best suited to single-threaded usage - various settings are defined via system properties, and therefore apply to all connections.
* No support of Kerberos authentication
* It does not support client based certificate testing with Keystore Config.
* Better control of Retry mechanism
* It does not support virtual hosts.
* It supports only the following methods: GET, POST, HEAD, OPTIONS, PUT, DELETE and TRACE
* Better control on DNS Caching with <u>DNS Cache Manager</u>

> Note: the FILE protocol is intended for testing purposes only. It is handled by the same code regardless of which HTTP Sampler is used.

If the request requires server or proxy login authorization (i.e. where a browser would create a pop-up dialog box), you will also have to add an <u>HTTP Authorization Manager</u> Configuration Element. For normal logins (i.e. where the user enters login information in a form), you will need to work out what the form submit button does, and create an HTTP request with the appropriate method (usually POST) and the appropriate parameters from the form definition. If the page uses HTTP, you can use the JMeter Proxy to capture the login sequence.

A separate SSL context is used for each thread. If you want to use a single SSL context (not the standard behavior of browsers), set the JMeter property:

```properties
https.sessioncontext.shared=true
```

By default, since version 5.0, the SSL context is retained during a Thread Group iteration and reset for each test iteration. If in your test plan the same user iterates multiple times, then you should set this to false.

```properties
httpclient.reset_state_on_thread_group_iteration=true
```

> Note: this does not apply to the Java HTTP implementation.

JMeter defaults to the SSL protocol level TLS. If the server needs a different level, e.g. SSLv3, change the JMeter property, for example:

```properties
https.default.protocol=SSLv3
```

JMeter also allows one to enable additional protocols, by changing the property `http.socket.protocols`.

If the request uses cookies, then you will also need an <u>HTTP Cookie Manager</u>. You can add either of these elements to the Thread Group or the HTTP Request. If you have more than one HTTP Request that needs authorizations or cookies, then add the elements to the Thread Group. That way, all HTTP Request controllers will share the same Authorization Manager and Cookie Manager elements.

If the request uses a technique called “URL Rewriting” to maintain sessions, then see section <u>6.1 Handling User Sessions With URL Rewriting</u> for additional configuration steps.

Parameters:

|                    Attribute                    | Description                                                  |                Required                 |
| :---------------------------------------------: | ------------------------------------------------------------ | :-------------------------------------: |
|                      Name                       | Descriptive name for this sampler that is shown in the tree  |                   No                    |
|                     Server                      | Domain name or IP address of the web server, e.g. www.exmaple.com. [==Do not include the `http://` prefix==.] Note: If the “Host” header is defined in a Header Manager, then this will be used as the virtual host name.  <u>Server is required, unless: it is provided by HTTP Request Defaults, or a full URL including scheme, host and port (`scheme://host:port`) is set in *Path* field</u> |                   No                    |
|                      Port                       | Port the web server is listening to. Default: 80             |                   No                    |
|                 Connect Timeout                 | Connection Timeout. Number of milliseconds to wait for a connection to open. |                   No                    |
|                Response Timeout                 | Response Timeout. Number of milliseconds to wait for a response. Note that this applies to each wait for a response. If the server response is sent in several chunks, the overall elapsed time may be longer than the timeout. A Duration Assertion can be used to detect responses that take too long to complete. |                   No                    |
|                 Server(*proxy*)                 | Hostname or IP address of a proxy server to perform request. [Do not include the http:// prefix.] |                   No                    |
|                      Port                       | Port the proxy server is listening to.                       | No, unless proxy hostname is specified. |
|                    Username                     | (Optional) username for proxy server                         |                   No                    |
|                    Password                     | (Optional) password for proxy server.(N.B.[^3] this is stored unencrypted in the test plan) |                   No                    |
|                 Implementation                  | `Java.HTTPClient4`. If not specified (and not defined by HTTP Request Defaults), the default depends on the value of the JMeter property `jmeter.httpsampler`, failing that, the HttpClient4 implementation is used. |                   No                    |
|                    Protocol                     | HTTP, HTTPS or FILE. Default: HTTP                           |                   No                    |
|                     Method                      | GET, POST, HEAD, TRACE, OPTIONS, PUT, DELETE, PATCH (not supported for JAVA implementation). With HttpClient4, the following methods related to WebDav are also allowed: COPY, LOCK, MKCOL, MOVE, PROPFIND, PROPPPATCH, UNLOCK, REPORT, MKCALENDAR, SEARCH.<br>More methods can be pre-defined for the HttpClient4 by using the JMeter property `httpsampler.user_defined_methods`. |                   Yes                   |
|                Content Encoding                 | Content encoding to be used (for POST, PUT, PATCH and FILE). This is the character encoding to be used, and ==is not related to the Content-Encoding HTTP header.== |                   No                    |
|             Redirect Automatically              | <u>Sets the underlying http protocol handler to automatically follow redirects, so they are not seen by JMeter</u>, and thus will not appear as samples. ==Should only be used for GET and HEAD requests==. The HttpClient sampler will reject attempts to use it for POST or PUT.<br>Warning: see below for information on cookie and header handling. |                   No                    |
|                Follow Redirects                 | ==This only has any effect if “<u>Redirect Automatically</u>” is not enabled.== If set, the JMeter sampler will check if the response is a redirect and follow it if so. <u>The initial redirect and further responses will appear as additional samples.</u> The URL and data fields of the parent sample will be taken from the final (non-redirected) sample, but the parent byte count and elapsed time include all samples. The latency is taken from the initial response. Note that the HttpClient sampler may log the following message:<br>“Redirect requested but followRedirects is disabled”<br>This can be ignored.<br>JMeter will collapse paths of the form ‘/../segment’ in both absolute and relative redirect URLs. For example http://host/one../two will be collapsed into http://host/two. If necessary, this behavior can be suppressed by setting the JMeter property `httpsampler.redirect.removeslashdotdot=false` |                   No                    |
|                  Use KeepAlive                  | JMeter sets the `Connection: keep-alive` header. ==This does not work properly with the default HTTP implementation, as connection re-use is not under user-control.== It does work with the Apache HttpComponents HttpClient implementations. |                   No                    |
|      Use multipart/form-data for HTTP POST      | Use a `multipart/form-data` or `application/x-www-form-urlencoded` post request |                   No                    |
|           Browser-compatible headers            | When using `multipart/form-data`, this suppresses the `Content-Type` and `Content-Transfer-Encoding` headers; only the `Content-Disposition` header is sent. |                   No                    |
|                      Path                       | The path to resource (for example, `/servlets/myServlet`). If the resource requires query string parameters, add them below in the “Send Parameters With the Request” section.<br> **As a special case, if the path starts with “`http://`” or “`https://`” then this is used as the full URL.**<br> In this case, the server, port and protocol fields are ignored; parameters are also ignored for GET and DELETE methods. Also please note that the path is not encoded - <u>apart from replacing spaces with %20</u> - so unsafe characters may need to be encoded to avoid errors such as `URISyntaxException`. |                   No                    |
|        Send Parameters With the Request         | The query string will be generated from the list of parameters you provide. Each parameter has a <u>name</u> and <u>value</u>, the options to <u>encode the parameter</u>, and an option to <u>include or exclude an equals sign</u> (==some applications don’t expect an equals sign when the value is the empty string==). The query string will be generated in the correct fashion, depending on the choice of “Method” you made (i.e. **if you chose GET or DELETE, the query string will be appended to the URL, if POST or PUT, then it will be sent separately**). Also, **if you are sending a file using a multipart form, the query string will be created using the multipart form specifications.** See below for some further info on parameter handling.<br/>Additionally, you can specify whether each parameter should be URL encoded. If you are not sure what this means, it is probably best to select it. If your values contain characters such as the following then encoding is usually required:<br/>*  ASCII Control Chars<br/>*  Non-ASCII characters<br/>*  Reserved characters: URLs use some characters for special use in defining their syntax. When these characters are not used in their special role inside a URL, they need to be encoded, example: `$` ,`&` ,`+` , `,` , `/`, `:`, `;`, `=`, `?`, `@`<br>* Unsafe characters: Some characters present the possibility of being misunderstood within URLs for various reasons. These characters should also always be encoded, example: 空格，`<`, `>`, `#`, `%`, … |                   No                    |
|                    File Path                    | Name of the file to send. If left blank, JMeter does not send a file, if filled in, JMeter automatically sends the request as a multipart form request.<br>If it is a POST or PUT or PATCH request and there is a single file whose ‘Parameter name’ attribute (below) is omitted, then the file is sent as the entire body of the request, i.e. no wrappers are added. This allows arbitrary bodies to be sent. This functionality is present for POST requests, and also for PUT requests. |                   No                    |
|                 Parameter name                  | Value of the “name” web request parameter.                   |                   No                    |
|                    MIME Type                    | MIME type (for example, `text/plain`). If it is a POST or PUT or PATCH request and either the “name” attribute are omitted or the request body is constructed from parameter values only, then the value of this field is used as the value of the `content-type` request header. |                   No                    |
| Retrieve All Embedded Resources from HTML Files | Tell JMeter to parse the HTML file and send HTTP/HTTPS requests for all images, Java applets, JavaScript files, CSSs, etc. referenced in the file. |                   No                    |
|           Save response as MD5 hash?            | If this is selected, then the response is not stored in the sample result. Instead, the 32 character MD5 hash of the data is calculated and stored instead. <u>This is intended for testing large amounts of data.</u> |                   No                    |
|                 URLs must match                 | If present, ==this must be a regular expression== that is used to match against any embedded URLs found. So if you only want to download embedded resources from http://example.invalid/, use the expression: `http://example\.invalid/.*` |                   No                    |
|               URLs must not match               | If present, this must be a regular expression that is used to filter out any embedded URLs found. So if you don’t want to download PNG or SVG files from any source, use the expression: `.*\.(?i:svg|png)` |                   No                    |
|               Use concurrent pool               | Use a pool of concurrent connections to get embedded resources |                   No                    |
|                      Size                       | Pool size for concurrent connections used to get embedded resources |                   No                    |
|               Source address type               | [Only for HTTP Request with HTTPClient implementation] To distinguish the source address value, select the type of these:<br>* Select IP/Hostname to use a specific IP address or a (local) hostname<br>* Select Device to pick the first available address for that interface which this may be either IPv4 or IPv6<br>* Select Device IPv4 to select the IPv4 address of the device name (like eth0, lo, em0, etc)<br>* Select Device IPv6 to select the IPv6 address of the device name (like eth0, lo, em0, etc) |                   No                    |
|              Source address field               | [Only for HTTP Request with HTTPClient implementation] This property is used to enable IP Spoofing. It overrides the default local IP address for this sample. The JMeter host must have multiple IP addresses (i.e. IP aliases, network interfaces, devices). The value can be a host name, IP address, or a network interface device such as “eth0” or “lo” or “wlan0”. If the property `httpclient.localaddress` is defined, that is used for all HttpClient requests. |                   No                    |

<u>When using *Automatic Redirection*, cookies are only sent for the initial URL.</u> This can cause **unexpected behavior for websites that redirect to a local server**. E.g. if www.example.com redirects to www.example.co.uk. In this case the server will probably return cookies for both URLs, but JMeter will only see the cookies for the last host, i.e. www.example.co.uk. If the next request in the test plan uses www.example.com, rather than www.example.co.uk, it will not get the correct cookies. Likewise, <u>Headers are sent for the initial request, and won’t be sent for the redirect.</u> This is generally only a problem for manually created test plans, as a test plan created using a recorder would continue from the redirected URL.

##### Parameter Handling

For the POST and PUT method, if there is no file to send, and the name(s) of the parameter(s) are omitted, then the body is created by concatenating all the value(s) of the parameters. Note that the values are concatenated without adding any end-of-line characters. These can be added by using the `__char()` function in the value fields. This allows arbitrary bodies to be sent. The values are encoded if the encoding flag is set. See also the MIME Type above how you can control the content-type request header that is sent.

For other methods, if the name of the parameter is missing, then the parameter is ignored. This allows the use of optional parameters defined by variables.

You have the option to switch to Body Data tab when a request has only unnamed parameters (or no parameters at all). This option is useful in the following cases (amongst others):

* GWT RPC HTTP Request
* JSON REST HTTP Request
* XML REST HTTP Request
* SOAP HTTP Request

Note that once you leave the Tree node, you cannot switch back to the parameter tab unless you clear the Body Data tab from its data.

In Body Data mode, each line will be sent with CRLF appended, apart from the last line. To send a CRLF after the last line of data, just ensure that there is an empty line following it. (This cannot be seen, except by noting whether the cursor can be placed on the subsequent line.)

##### Method Handling

The GET, DELETE, POST, PUT and PATCH request methods work similarly, except that as of 3.1, only POST method supports multipart requests or file upload. The PUT and PATCH method body must be provided as one of the following:

* define the body as a file with empty Parameter name field; in which case the MIME Type is used as the Content-Type
* define the body as parameter value(s) with no name
* use the Body Data tab

The GET, DELETE and POST methods have an additional way of passing parameters by using the Parameters tab. GET, DELETE, PUT and PATCH require a Content-Type. If not using a file, attach a Header Manager to the sampler and define the Content-Type there.

JMeter scan responses from embedded resources. It uses the property `HTTPResponse.parsers`, which is a list of parser ids, e.g. `htmlParser`, `cssParser` and `wmlParser`. For each id found, JMeter checks two further properties:

* `id.types` - a list of content types
* `id.className` - the parser to be used to extract the embedded resources

See `jmeter.properties` file for the details of the settings. If the `HTTPResponse.parser` property is not set, JMeter reverts to the previous behavior, i.e. only text/html responses will be scanned.

##### Emulating slow connections

##### Response size calculation

##### Retry handling

##### Note: Certificates does not conform to algorithm constraints

You may encounter the following error: 

```shell
java.security.cert.CertificateException: Certificates does not conform to algorithm constraints
```

if you run a HTTPS request on a website with a SSL certificate (itself or one of SSL certificates in its chain of trust) with a signature algorithm using MD2 (like `md2WithRSAEncryption`) or with a SSL certificate with a size lower than 1024 bits.

This error is related to increased security in Java 8.

To allow you to perform your HTTPS request, you can downgrade the security of your Java installation by editing the Java `jdk.certpath.disabledAlgorithms` property. Remove the MD2 value or the constraint on size, depending on your case. 

This property is in this file: `JAVA_HOME/jre/lib/security/java.security`

### 18.2 Logic Controllers

### 18.3 Listeners

#### Graph Results

> ==Graph Results MUST NOT BE USED during load test as it consumes a lot of resources (memory and CPU). Use it only for either <u>functional testing</u> or <u>during Test Plan debugging and Validation</u>.==

The Graph Results listener generates a simple graph that plots all sample times. Along the bottom of the graph, the current sample(black), the current average of all samples (blue), the current standard deviation (red), and the current throughput rate (green) are displayed in milliseconds.

The throughput number represents the actual number of requests/minute the server handled. This calculation includes any delays you added to your test and JMeter’ s own internal processing time. The advantage of doing the calculation like this is that this number represents something real - your server in fact handled that many requests per minute, and you can increase the number of threads and/or decrease the delays to discover your server’s maximum throughput. Whereas if you made calculations that factored out delays and JMeter’ s processing, it would be unclear what you could conclude from that number.

![](https://jmeter.apache.org/images/screenshots/graph_results.png)

The following table briefly describes the items on the graph. Further details on the precise meaning of the statistical terms can be found on the web - e.g. Wikipedia - or by consulting a book on statistics.

* Data - plot the actual data values
* Average - plot the Average
* Median - plot the Median(midway value)
* Deviation - plot the Standard Deviation (a measure of the variation)
* Throughput - plot the number of samples per unit of time

<u>The individual figures at the bottom of the display are the current values.</u> “==Latest Sample==” is the ==current elapsed sample time==, shown on the graph as “Data”.

The value displayed on the top left of graph is the max of 90^th^ percentile of response time.

#### View Results Tree

> ==View Results Tree MUST NOT BE USED during load test as it consumes a lot of resources (memory and CPU). Use it only for either functional testing or during Test Plan debugging and Validation.==

The View Results Tree shows a tree of all sample responses, allowing you to view the response for any sample. In addition to showing the response, you can see the time it took to get this response, and some response codes. Note that the Request panel only shows the headers added by JMeter. It does not show any headers (such as Host) that may be added by the HTTP protocol implementation.

「查看结果树」以树的形式展示了所有取样的响应结果, 你可以查看任何取样的响应结果. 除此之外, 你可以看到每个响应所花费的时间, 和响应状态码. 注意: Request 面板只展示JMeter添加的header, 不展示任何因为HTTP协议而添加的header(比如Host).

There are several ways to view the response, selectable by a drop-down box at the bottom of the left hand panel.

| Renderer | Description                                                  |
| -------- | ------------------------------------------------------------ |
| HTML     | The HTML view attempts to render the response as HTML. The rendered HTML is likely to compare poorly to the view one would get in any web browser; however, it does provide a quick approximation that is helpful for initial result evaluation. |
| JSON     | The JSON view will show the response in tree style (also handles JSON embedded in JavaScript) |
| Text     | The default Text view shows all of the text contained in the response. Note that <u>this will only work if the response ==`content-type` is considered to be text==. If the `content-type` begins with any of the following, it is considered as ==binary==</u>, otherwise it is considered to be text.<br>`image/`, `audio/`, `video/` |

Scroll automatically? option permit to have last node display in tree selection

> Starting with version 3.2 the number of entries in the View is restricted to the value of the property `view.results.tree.max_results` which defaults to 500 entries. The old behavior can be restored by setting the property to 0. Beware, that this might consume a lot of memory.

With Search option, most of the views also allow the displayed data to be searched; the result of the search will be high-lighted in the display above. For example the Control panel



#### Aggregate Report

The aggregate report creates a table row for each differently named request in your test. For each request, it totals the response information and provides request count, min, max, average, error rate, approximate throughput (request/second) and Kilobytes per second throughput. Once the test is done, the throughput is the actual through for the duration of the entire test.

The throughput is calculated from the point of view of the sampler target (e.g. the remote server in the case of HTTP samples). JMeter takes into account <u>the total time</u> over *which <u>the requests have been generated</u>*. <u>If other samplers and timers are in the same thread, these will increase the total time, and therefore reduce the throughput value.</u> So ==two identical samplers with different names will have half the throughput of two samplers with the same name.== <u>It is important to choose the sampler names correctly to get the best results from the Aggregate Report.</u> 

Calculation of the Median and 90% Line (90<sup>th</sup> percentile) values requires additional memory. JMeter now combines samples with the same elapsed time, so far less memory is used. However, for samples that take more than a few seconds, the probability is that fewer samples will have identical times, in which case more memory will be needed. Note <u>you can use this listener afterwards to reload a CSV or XML results file which is the recommended way to avoid performance impacts.</u> See the Summary Report for a similar Listener that does not store individual samples and so needs constant memory.

> Starting with JMeter 2.12, you can configure the 3 percentile values you want to compute, this can be done by setting properties:
>
> * `aggregate_rpt_pct1`: defaults to 90<sup>th</sup> percentile
> * `aggregate_rpt_pct2`: defaults to 95<sup>th</sup> percentile
> * `aggregate_rpt_pct3`: defaults to 99<sup>th</sup> percentile





#### Backend Listener



### 18.4 Configuration Elements

Configuration elements can be used to set up defaults and variables for later use by samplers. Note that ==these elements are processed at the start of the scope in which they are found, i.e. before any samplers in the same scope.==

#### CSV Data Set Config

CSV Data Set Config is used to <u>read lines from a file, and split them into variables</u>. It is easier to use than the `__CSVRead()` and `__StringFromFile()` functions. It is well suited to handling large numbers of variables, and is also useful for testing with “random” and unique values.

Generating unique random values at run-time is expensive in terms of CPU and memory, so just create the data in advance of the test. If necessary, the “random” data from the file can be used in conjunction with a run-time parameter to create different sets of values from each run - e.g. using concatenation - which is much cheaper than generating everything at run-time.

JMeter allows values to be quoted; this allows the value to contain a delimiter. If “allow quoted data” is enabled, a value may be enclosed in double-quotes. These are removed. To include double-quotes within a quoted field, use two double-quotes. For example:

```bash
1,"2,3","4,5" =>
1
2,3
4"5
```

JMeter supports CSV files which have a header line defining the column names. To enable this, leave the “Variable Names” field empty. The correct delimiter must be provided.

JMeter supports CSV files with quoted data that includes new-lines.

By default, the file is only opened once, and each thread will use a different line from the file. However the order in which lines are passed to threads depends on the order in which they execute, which may vary between iterations. Lines are read at the start of each test iteration. The file name and mode are resolved in the first iteration.

See the description of the Share mode below for additional options. If you want each thread to have its own set of values, then you will need to create a set of files, one for each thread. For example `test1.csv`, `test2.csv`, …, `testn.csv`. Use the filename `test${__threadNum}.csv` and set the “Sharing mode” to “Current thread”.

> CSV Dataset variables are defined at the start of each test iteration. As this is after configuration processing is completed, they cannot be used for some configuration items - such as JDBC Config - that  process their contents at configuration time. However the variables do work in the HTTP Auth Manager, as the username etc. are processed at run-time.

As a special case, the string `“\t”`(without quotes) in the delimiter field is treated as a Tab.

When the end of file (EOF) is reached, and the recycle option is true, reading starts again with the first line of the file.

If the recycle option is false, and stop Thread is false, then all the variables are set to `<EOF>` when the end of file is reached. This value can be changed by setting the JMeter property `csvdataset.eofstring`.

If the Recycle option is false, and Stop Thread is true, then reaching EOF will cause the thread to be stopped.

| Attribute                        | Description                                                  | Required |
| -------------------------------- | ------------------------------------------------------------ | -------- |
| Name                             | Descriptive name for this element that is shown in the tree. |          |
| Filename                         | Name of the file to be read. Relative file names are resolved with respect to the path of the active test plan. For distributed testing, the CSV file must be stored on the server host system in the correct relative directory to where the JMeter server is started. Absolute file names are also supported, but note they are unlikely to work in remote mode, unless the remote server has the same directory structure. If the same physical file is referenced in two different ways - e.g. `csvdata.txt` and `./csvdata.txt` - then these are treated as different files. If the OS does not distinguish between upper and lower case, `csvData.TXT` would also be opened separately. | Yes      |
| File Encoding                    | The encoding to be used to read the file, if not the platform default. | No       |
| Variable Names                   | List of variable names. The names must be separated by the delimiter character. They can be quoted using double-quotes. JMeter supports CSV header lines: if the variable name field empty, then the first line of the file is read and interpreted as the list of column names. | No       |
| Use first line as Variable Names | Ignore first line of CSV file, it will only be used if Variable Names is not empty, if Variable Names is empty the first line must contain the headers. | No       |
| Delimiter                        | Delimiter to be used to split the records in the file. If there are fewer values on the line than there are variables the remaining variables are not updated - so they will retain their previous value (if any). | Yes      |
| Allow quoted data?               | Should the CSV file allow values to be quoted? If enabled, then values can be enclosed in `“` - double-quote - allowing values to contain a delimiter. | Yes      |
| Recycle on EOF?                  | Should the file be re-read from the beginning on reaching EOF?(default is true) | Yes      |
| Stop thread on EOF?              | Should the thread be stopped on EOF, if Recycle is false?    | Yes      |
| Sharing mode                     | * All threads - (the default) the file is shared between all the threads.<br>* Current thread group - each file is opened once for each thread group in which the element appears<br>* Current thread - each file is opened separately for each thread<br>* Identifier - all threads sharing the same identifier share the same file. So for example if you have 4 thread groups, you could use a common id for two or more of the groups to share the file between the same thread numbers in different thread groups. | Yes      |

#### HTTP Authorization Manager

The Authorization Manager lets you <u>**specify one or more user logins for web pages** that are restricted using server authentication.</u> You see this type of authentication when you use your browser to access a restricted page, and your browser displays a login dialog box. <u>JMeter transmits the login information when it encounters this type of page.</u>

<u>The Authorization headers **may not be shown in the Tree View Listener “Request” tab**</u>. The Java implementation does ==pre-emptive authentication==, but it does not return the Authorization header when JMeter fetches the headers. The HttpComponents(HC 4.5.X) implementation defaults to pre-emptive since 3.2 and the header will be shown. To disable this, set the values as below, in which case authentication will only be performed in response to a challenge.

In the file `jmeter.properties` set `httpclient4.auth.preemptive=false`

> Note: the above settings only apply to the HttpClient sampler.

When looking for a match against a URL, JMeter checks each entry in turn, and stops when it finds the first match. Thus the most specific URLs should appear first in the list, followed by less specific ones. Duplicate URLs will be ignored. **If you want to use different usernames/passwords for different threads, you can use variables. These can be set up using a <u>CSV Data Set Config</u> Element.**

> If there is more than one Authorization Manager in the scope of a Sampler, there is currently no way to specify which one is to be used.

| Attribute                     | Description                                                  | Required |
| ----------------------------- | ------------------------------------------------------------ | -------- |
| Name                          | Descriptive name for this element that is shown in the tree. | No       |
| Clear auth on each iteration? | Used by Kerberos authentication. If checked, authentication will be done on each iteration of Main Thread Group loop even if it has already been done in a previous one. This is usually useful if each main thread group iteration represents behavior of one Virtual User. | Yes      |
| Base URL                      | A partial or complete URL that matches one or more HTTP Request URLs. As an example, say you specify a Base URL of “http://localhost/restricted/” with a Username of “jmeter” and a Password of “jmeter”. If you send an HTTP request to the URL “http://localhost/restricted/ant/myPage.html”, the Authorization Manager sends the login information for the user named, “jmeter”. | Yes      |
| Username                      | The username to authorize.                                   | yes      |
| Password                      | The password for the user. (N.B. this is stored unencrypted in the test plan) | Yes      |
| Domain                        | The domain to use for NTLM.                                  | No       |
| Realm                         | The realm to use for NTLM.                                   | No       |
| Mechanism                     | Type of authentication to perform. JMeter can perform different types of authentications based on used Http Samplers:<br>Java<br>      BASIC<br>HttpClient 4<br>      BASIC, DIGEST and Kerberos | No       |

> **The <u>Realm</u> only applies to the HttpClient sampler.**

Kerberos Configuration: 略

Controls:

* `Add` Button - Add an entry to the authorization table.
* `Delete` Button - Delete the currently selected table entry.
* `Load` Button - Load a previously saved authorization table and add the entries to the existing authorization table entires.
* `Save As` Button - Save the current authorization table to a file.

> When you save the Test Plan, JMeter automatically saves all of the authorization table entries - including any passwords, which are not encrypted.

##### Authorization Example

In this example, we created a Test Plan on a local server that sends three HTTP requests, two requiring a login and the other is open to everyone. See below to see the makeup of our Test Plan. On our server, we have a restricted directory named, “secret”, which contains two files, “`index.html`” and “`index2.html`”. 

![](https://jmeter.apache.org/images/screenshots/http-config/auth-manager-example1a.png)

We created a login id named, “kevin”, which has a password of “spot”. 

![](https://jmeter.apache.org/images/screenshots/http-config/auth-manager-example1b.png)

So, in our Authorization Manager, we created an entry for the restricted directory and a username and password. The two HTTP requests named “`SecretPage1`” and “`SecretPage2`” make requests to “`/secret/index.html`” and “`/secret/index2.html`”. The other HTTP request, named “`NoSecretPage`” makes a request to “`/index.html`”.

When we run the Test Plan, JMeter looks in the Authorization table for the URL it is requesting. If the Base URL matches the URL, then JMeter passes this information along with the request.

#### HTTP Cookie Manager

The Cookie Manager element has <u>**two functions**</u>:

**<u>First, it stores and sends cookies just like a web browser.</u>** <u>If you have an HTTP Request and the response contains a cookie, the Cookie Manager</u> ==automatically stores that cookie and will use it for all future requests to that particular website.== Each JMeter thread has its own “cookie storage area”. So, if you are testing a website that uses a cookie for storing session information, each JMeter thread will have its own session. Note that **such cookies do not appear on the Cookie Manager display, but they can be seen using the *<u>View Results Tree</u>* Listener**.

JMeter checks that received cookies are valid for the URL. This means that ==cross-domain cookies are not stored==. If you have bugged behavior or want Cross-Domain cookies to be used, define the JMeter property “`CookieManager.check.cookies=false`”

**Received Cookies can be stored as <u>JMeter thread variables</u>**. To save cookies as variables, define the property “`CookieManager.save.cookies=true`”. Also, cookies names are prefixed with “`COOKIE_`” before they are stored (this avoids accidental corruption of local variables). To revert to the original behavior, define the property “`CookieManager.name.prefix=`”(one or more spaces). If enabled, the value of a cookie with the name TEST can be referred to as `${COOKIE_TEST}`.

**<u>Second, you can manually add a cookie to the Cookie Manager. However, if you do this, ==the cookie will be shared by all JMeter threads==.</u>**

Note that such Cookies are created with an Expiration time far in the future.

Cookies with null values are ignored by default. This can be changed by setting the JMeter property: `CookieManager.delete_null_cookies=false`. Note that this also applies to manually defined cookies - any such cookies will be removed from the display when it is updated. Note also that t<u>he cookie name must be unique - if a second cookie is defined with the same name, it will replace the first</u>.

> **<u>If there is more than one Cookie Manager in the scope of a Sampler, there is currently no way to specify which one is to be used</u>**. Also, <u>**a cookie stored in one cookie manager is not available to any other manager**</u>, so use multiple Cookie Managers with care.

| Attribute                    | Description                                                  | Required                                            |
| ---------------------------- | ------------------------------------------------------------ | --------------------------------------------------- |
| Name                         | Descriptive name for this element that is shown in the tree  | No                                                  |
| Clear Cookies each Iteration | If selected, all server-defined cookies are cleared each time the main Thread Group loop is executed. Any cookie defined in the GUI are not cleared. | Yes                                                 |
| Cookie Policy                | The cookie policy that will be used to manage the cookies. “standard” is the default since 3.0, and should work in most cases. [Note: “`ignoreCookies`” is equivalent to omitting the CookieManager] | Yes                                                 |
| Implementation               | 5.4 现在已经没有这个选项了, 之前默认为 HC4CookieHandler(HttpClient 4.5.X API) | Yes                                                 |
| User-Defined Cookies         | This gives you the opportunity to use hardcoded cookies that will be used by all threads during the test execution. The “domain” is the hostname of the server (without http://); the port is currently ignored. | No (discouraged, unless you know what you’re doing) |
| Add Button                   | Add an entry to the cookie table                             | N/A                                                 |
| Delete Button                | Delete the currently selected table entry                    | N/A                                                 |
| Load Button                  | Load a previously saved cookie table and add the entries to the existing cookie table entries | N/A                                                 |
| Save As Button               | Save the current cookie table to a file (does not save any cookies extracted from HTTP Responses). | N/A                                                 |

#### HTTP Request Defaults

This element lets you <u>**set default values** that your HTTP Request controllers use</u>. For example, if you are creating a Test Plan with 25 HTTP Request Controllers and all of the requests are being sent to the same server, you could add a single HTTP Request Defaults element with the “Server Name or IP” field filled in. Then, when you add the 25 HTTP Request controllers, leave the “Server Name or IP” field empty. The controllers will inherit this field value from the HTTP Request Defaults element.

> All port values are treated equally; a sampler that does not specify a port will use the HTTP Request Defaults port, if one is provided.

HTTP Request Advanced config fields

| Attribute                                       | Description                                                  | Required                               |
| ----------------------------------------------- | ------------------------------------------------------------ | -------------------------------------- |
| Name                                            | Descriptive name for this element that is shown in the tree. | No                                     |
| Server                                          | Domain name or IP address of the web server. E.g. www.example.com. [Do not include the `http://` prefix] | No                                     |
| Port                                            | Port the web server is listening to.                         | No                                     |
| Connect Timeout                                 | Connection Timeout. Number of milliseconds to wait for a connection to open. | No                                     |
| Response Timeout                                | Response Timeout. Number of milliseconds to wait for a response. | No                                     |
| Implementation                                  | java, HttpClient4. If not specified the default depends on the value of JMeter property `jmeter.httpsampler`, failing that, the Java implementation is used. | No                                     |
| Protocol                                        | HTTP or HTTPS                                                | No                                     |
| Content encoding                                | The encoding to be used for the request.                     | No                                     |
| Path                                            | The path to resource(for example, `/servlets/myServlet`). If the response requires query string parameters, add them below in the “Send Parameters With the Request” section. Note that the path is the default for the full path, not a prefix to be applied to paths specified on the HTTP Request screens. | No                                     |
| Send Parameters With the Request                | The query string will be generated from the list of parameters you provide. Each parameter has a name and value. The query string will be generated in the correct fashion, depending on the choice of “Method” you made(i.e. if you chose GET, the query string will be appended to the URL, if POST, then it will be sent separately). Also, if you are sending a file using a multipart form, the query string will be created using the multipart form specifications. | No                                     |
| Server(proxy)                                   | Hostname or IP address of a proxy server to perform request.[Do not include the http:// prefix] | No                                     |
| Port                                            | Port the proxy server is listening to.                       | No, unless proxy hostname is specified |
| Username                                        | (Optional) username for proxy server.                        | No                                     |
| Password                                        | (Optional) password for proxy server. (N.B. this is stored unencrypted in the test plan) | No                                     |
| Retrieve All Embedded Resources from HTML Files | Tell JMeter to parse the HTML file and send HTTP/HTTPS requests for all images, Java applets, JavaScript files, CSSs, etc. referenced in the file. | No                                     |
| Use concurrent pool                             | Use a pool of concurrent connections to get embedded resources. | No                                     |
| Size                                            | Pool size for concurrent connections used to get embedded resources. | No                                     |
| URLs must match                                 | If present, this must be a regular expression that is used to match against any embedded URLs found. So if you only want to download embedded resources from `http://example.invalid/`, use the expression: `http://example\.invalid/.*` | No                                     |
| URLs must not match                             | If present, this must be a regular expression that is used to filter out any embedded URLs found. So if you don’t want to download PNG or SVG files from any source, use the expression: `.*\.(?i:svg|png)` | No                                     |

Note: radio buttons only have two states - on or off. This makes it impossible to override settings consistently - does off mean off, or does it mean use the current default? JMeter uses the latter (otherwise defaults would not work at all). So if the button is off, then a later element can set it on, but if the button is on, a later element cannot set it off.

#### HTTP Header Manager

The Header Manager lets you add or override HTTP request headers.

<u>JMeter now supports multiple Header Managers.</u> **The header entries are merged to form the list for the sampler.** If an entry to be merged matches an existing header name, it replaces the previous entry. This allows one to set up a default set of headers, and apply adjustments to particular samplers. Note that an empty value for a header does not remove an existing header, it justs replace its value.

| Attribute      | Description                                                  | Required                                  |
| -------------- | ------------------------------------------------------------ | ----------------------------------------- |
| Name           | Descriptive name for this element that is shown in the tree. | No                                        |
| Name(Header)   | Name of the request header. Two common request headers you may want to experiment with are “User-Agent” and “Referer”. | No(You should have at least one, however) |
| Value          | Request header value.                                        | No(You should have at least one, however) |
| Add Button     | Add an entry to the header table.                            | N/A                                       |
| Delete Button  | Delete the currently selected table entry.                   | N/A                                       |
| Load Button    | Load a previously saved header table and add the entries to the existing header table entries. | N/A                                       |
| Save As Button | Save the current header table to a file.                     | N/A                                       |

##### Header Manager example

In this example, we created a Test Plan that tells JMeter to override the default “User-Agent” request header and use a particular Internet Explorer agent string instead.

![](https://jmeter.apache.org/images/screenshots/http-config/header-manager-example1a.png)

![](https://jmeter.apache.org/images/screenshots/http-config/header-manager-example1b.png)



#### User Defined Variables

The User Defined Variables element lets you define an **initial set of variables**, just as in the Test Plan.

> Note that all the UDV elements in a test plan - no matter where they are - are processed at the start.

So you cannot reference variables which are defined as part of a test run, e.g. in a Post-Processor.

UDVs should not be used with functions that generate different results each time they are called. Only the result of the first function call will be saved in the variable. However, UDVs can be used with functions such as `__P()`, for example:

```shell
HOST		${__P(host,localhost)}
```

which would define the variable “HOST” to have the value of the JMeter property “host”, defaulting to “localhost” if not defined.

For defining variables during a test run, see User Parameters. UDVs are processed in the order they appear in the Plan, from top to bottom.

For simplicity, it is suggested that UDVs are placed only at the start of a Thread Group(or perhaps under the Test Plan itself).

Once the Test Plan and all UDVs have been processed, the resulting set of variables is copied to each thread to provide the initial set of variables.

If a runtime element such as a User Parameters Pre-Processor or Regular Expression Extractor defines a variable with the same name as one of the UDV variables, then this will replace the initial value, and all other test elements in the thread will see the updated value.

> If you have more than one Thread Group, make sure you use different names for different values, as UDVs are shared between Thread Groups. Also, the variables are not available for use until after the element has been processed, so you cannot reference variables that are defined in the same element. You can reference variables defined in earlier UDVs or on the Test Plan.

| Attribute              | Description                                                  | Required |
| ---------------------- | ------------------------------------------------------------ | -------- |
| Name                   | Descriptive name for this element that is shown in the tree. |          |
| User Defined Variables | Variable name/value pairs. The string under the “Name” column is what you’ll need to place inside the brackets in `${...}` constructs to use the variables later on. The whole `${...}` will then be replaced by the string in the “Value” column. |          |

#### Random Variable

The Random Variables Config Element is used to generate random numeric strings and store them in variable for use later. It’s simpler than using User Defined Variables together with the `__Random()` function.

The output variable is constructed by using the random number generator, and then the resulting number is formatted using the format string. The number is calculated using the formula `minimun+Random.nextInt(maximum-minimum+1)`. `Random.nextInt()` requires a positive integer. This means that maximum-minimum - i.e. the range - must be less than 2147483647, however the minimum and maximum values can be any long values so long as the range is OK.

> As the random value is evaluated at the start of each iteration, it is probably not a good idea to use a variable other than a property as a value for the minimum or maximum. It would be zero on the first iteration.

| Attribute         | Description                                                  | Required |
| ----------------- | ------------------------------------------------------------ | -------- |
| Name              | Descriptive name for this element that is shown in the tree. | Yes      |
| Variable Name     | The name of the variable in which to store the random string. | Yes      |
| Format String     | The `java.text.DecimalFormat` format string to be used. For example “000” which will generate numbers with at least 3 digits, or “USER_000” which will generate output of the form USER_nnn. If not specified, the default is to generate the number using `Long.toString()` | No       |
| Minimum Value     | The minimum value (long) of the generated random number.     | Yes      |
| Maximum Value     | The maximum value (long) of the generated random number.     | Yes      |
| Random Seed       | The seed for the random number generator. If you use the same seed value with Per Thread set to true, you will get the same value for each Thread as per Random class. If no seed is set, Default constructor of Random will be used. | No       |
| Per Thread(User)? | If False, the generator is shared between all threads in the thread group. If True, then each thread has its own random generator. | Yes      |

### 18.5 Assertions

Assertions are used to perform additional checks on samples,and are processed after every sampler in the same scope.  To ensure that Assertion is applied only to a particular sampler, add it as a child of the sampler.

> Note: <u>Unless documented otherwise, ==Assertions are not applied to sub-samples(child samples)== - **only to the parent sample**.</u> In the case of JSR223 and BeanShell Assertions, the script can retrieve sub-samples using the method `prev.getSubResults()` which returns an array of SampleResults. The array will be empty if there are none.

Assertions can be applied to either the main sample, the sub-samples or both. The default is to apply the assertion to the main sample only. If the Assertion supports this option, then there will be an entry on the GUI which looks like the following:

![](https://jmeter.apache.org/images/screenshots/assertion/assertionscopevar.png)

If a sub-sampler fails and the main sample is successful, then the main sample will be set to failed status and an Assertion Result will be added. If the JMeter variable option is used, it is assumed to relate to the main sample, and any failure will be applied to the main sample only.

> The variable `JMeterThread.last_sample_ok` is updated to “true” or “false” after all assertions for a sampler have been run.

#### Response Assertion

The response assertion control panel lets you add pattern strings to be compared against various fields of the request or response. The pattern strings are:

* Contains, Matches: Perl5-style regular expressions
* Equals, Substring: plain text, case-sensitive



### 18.6 Timers



### 18.7 Pre Processors

#### HTTP URL Re-writing Modifier

This modifier works similarly to the HTML Link Parser, except it has a specific purpose for which it is easier to use than the HTML Link Parser, and more efficient. For <u>web applications that ==use URL Re-writing to store session ids instead of cookies==, this element can be ==attached at the ThreadGroup level==, much like the HTTP Cookie Manager.</u> Simply give it the name of the session id parameter, and it will find it on the page and add the argument to every request of that ThreadGroup.

Alternatively, this modifier can be attached to select requests and it will modify only them. Clever users will even determine that this modifier can be used to grab values that elude the HTML Link Parser.

| Attribute                                 | Description                                                  | Required |
| ----------------------------------------- | ------------------------------------------------------------ | -------- |
| Name                                      | Descriptive name given to this element in the test tree.     | No       |
| Session Argument Name                     | The name of the parameter to grab from previous response. This modifier will find the parameter anywhere it exists on the page, and grab the value assigned to it, whether it’s in an HREF or a form. | Yes      |
| Path Extension                            | Some web apps rewrite URLs by appending a semi-colon plus the session id parameter. Check this box if that is so. | No       |
| Do not use equals in path extension       | Some web apps rewrite URLs without using an “=” sign between the parameter name and value (such as Intershop Enfinity) | No       |
| Do not use questionmark in path extension | Prevents the query string to end up in the path extension(such as Intershop Enfinity). | No       |
| Cache Session Id?                         | Should the value of the session Id be saved for later use when the session Id is not present? | Yes      |
| URL Encode                                | URL Encode value when writing parameter                      | No       |



####  User Parameters

Allows the user to <u>==specify values for **User Variables**== specific to[^1] individual threads</u>.

<u>User Variables</u> can also be specified in the Test Plan but <u>not specific to individual threads.</u> This panel allows you to specify a series of values for any User Variable. For each thread, the variable will be assigned one of the values from the series in sequence. If there are more threads than values, the values get re-used. For example, this can be used to assign a distinct user id to be used by each thread. User variables can be referenced in any field of any JMeter Component.

The variable is specified by clicking the Add Variable button in the bottom of the panel and filling in the Variable name in the ’Name:’ column. To add a new value to the series, click the ‘Add User’ button and fill in the desired value in the newly added column.

Values can be accessed in ay test component in the same thread group, using the function syntax: `${variable}`.

See also the CSV Data Set Config element, which is more suitable for large numbers of parameters.

| Attribute                 | Description                                                  | Required |
| ------------------------- | ------------------------------------------------------------ | -------- |
| Name                      | Descriptive name for this element that is shown in the tree. |          |
| Update Once Per Iteration | A flag to indicate whether the User Parameters element should update its variables only once per iteration. If you embed functions into the UP, then you may need greater control over how often the values of the variables are updated. Keep this box checked to ensure the values are updated each time through the UP ’s parent controller. Uncheck the box, and the UP will update the parameters for every sample request made within its scope. | Yes      |

#### BeanShell PreProcessor

The BeanShell PreProcessor allows arbitrary code to be applied before taking a sample.

The test element supports the `ThreadListener` and `TestListener` methods. These should be defined in the initialization file. See the file `BeanShellListeners.bshrc` for example definitions.

| Attribute                                | Description                                                  | Required                            |
| ---------------------------------------- | ------------------------------------------------------------ | ----------------------------------- |
| Name                                     | Descriptive name for this element that is shown in the tree. <u>The name is stored in the script variable `Labe1`</u> | No                                  |
| Reset `bsh.Interpreter` before each call | If this option is selected, then the interpreter will be recreated for each sample. This may be necessary for some long running scripts. For further information, see Best Practices - BeanShell scripting. | Yes                                 |
| Parameters                               | Parameters to pass to the BeanShell script. The parameters are stored in the following variables:<br>* `Parameters` - string containing the parameters as a single variable<br>* `bsh.args` - String array containing parameters, split on white-space | No                                  |
| Script file                              | A file containing the BeanShell script to run. The file name is stored in the script variable `FileName` | No                                  |
| Script                                   | The BeanShell script. The return value is ignored.           | Yes(unless script file is provided) |

Before invoking the script, some variables are set up in the BeanShell interpreter:

* log - (Logger) - can be used to write to the log file

* ctx - (JMeterContext) - gives access to the context

* vars - (JMeterVariables) - gives read/write access to variables:

  ```bash
  vars.get(key);
  vars.put(key,val);
  vars.putObject("OBJ1",new Object());
  ```

* props - (JMeterProperties - class `java.util.Properties`) - e.g. `props.get("START.HMS");` `props.put("PROP1", "1234");`

* prev - (SampleResult) - gives access to the previous SampleResult(if any)

* sampler - (Sampler) - gives access to the current sampler

For details of all the methods available on each of the above variables, please check the javadoc

If the property `beanshell.preprocessor.init` is defined, this is used to load an initialization file, which can be used to define methods etc. for use in the BeanShell script.

### 18.8 Post-Processors

As the name suggests, Post-Processors are applied after samplers. Note that <u>they are applied to all the samplers in the same scope, so to ==ensure that a post-processor is applied only to a particular sampler==, **add it as a child of the sampler**.</u>

> Note: Unless documented otherwise, Post-Processors are not applied to sub-samples(child samples) - only to the parent sample. In the case of JSR223 and BeanShell post-processors, the script can retrieve sub-samples using the method `prev.getSubResults()` which returns an array of SampleResults. The array will be empty if there are none.

Post-processors are run before Assertions, so they do not have access to any Assertion Results, nor will the sample status reflect the results of any Assertions. If you require access to Assertion Results, try using a Listener instead. Also note that the variable `JMeterThread.last_sample_ok` is set to “true” or “false” after all Assertions have been run.

#### XPath Extractor

This test element allows the user to extract value(s) from structured response - XML or (X)HTML - using XPath query language.

> Since JMeter 5.0, you should use XPath2 Extractor as it provides better and easier namespace management, better performances and support for XPath 2.0

| Attribute                                             | Description                                                  | Required                |
| ----------------------------------------------------- | ------------------------------------------------------------ | ----------------------- |
| Name                                                  | Descriptive name for this element that is shown in the tree. | No                      |
| Apply to                                              | This is for use with samplers that can generate sub-samples, e.g. HTTP Sampler with embedded resources, Mail Reader or samples generated by the Transaction Controller.<br>* Main sample only - only applies to the main sample<br>* Sub-samples only - only applies to the sub-samples<br>* Main sample and sub-samples - applies to both.<br>* JMeter Variable Name to use - extraction is to be applied to the contents of the named variable<br>Xpath matching is applied to all qualifying samples in turn, and all the matching results will be returned. | Yes                     |
| Use Tidy(tolerant parser)                             | If checked use Tidy to parse HTML response into XHTML.<br>* “Use Tidy” should be checked on for HTML response. Such response is converted to valid XHTML(XML compatible HTML) using Tidy<br>* “Use Tidy” should be unchecked for both XHTML or XML response(for example RSS)<br>For HTML, CSS Selector Extractor is the correct and performing solution. Don’t use XPath for HTML extractions. | Yes                     |
| Quiet                                                 | Sets the Tidy Quiet flag                                     | If Tidy is selected     |
| Report Errors                                         | If a Tidy error occurs, then set the Assertion accordingly   | If Tidy is selected     |
| Show warnings                                         | Sets the Tidy showWarnings option                            | If Tidy is selected     |
| Use Namespaces                                        | If checked, then the XML parser will use namespace resolution.(see note below on NAMESPACE) Note that **<u>currently only namespaces declared on the ==root element== will be recognized</u>**. See below for user-definition of additional workspace names. | If Tidy is not selected |
| Validate XML                                          | Check the document against its schema.                       | If Tidy is not selected |
| Ignore Whitespace                                     | Ignore Element Whitespace.                                   | If Tidy is not selected |
| Fetch External DTDs                                   | If selected, external DTDs are fetched.                      | If Tidy is not selected |
| Return entire XPath fragment instead of text content? | If selected, the fragment will be returned rather than the text content. For example `\\title` would return `<title>Apache JMeter</title>` rather than “`Apache JMeter`”. In this case, `//title/text()` would return “`Apache JMeter`”. | Yes                     |
| Name of created variable                              | The name of the JMeter variable in which to store the result. | Yes                     |
| XPath Query                                           | Element query in XPath language. Can <u>return **more than one** match</u>. | Yes                     |
| Match No. (0 for Random)                              | If the XPath Path query leads to many results, you can choose which one(s) to extract as Variables:<br>* 0: means random<br>* -1: means extract all results (default value), they will be named as `<variable name>_N` (where N goes from 1 to Number of results)<br>* X: means extract the X<sup>th</sup> result. If this X<sup>th</sup> is greater than number of matches, then nothing is returned. Default value will be used | No                      |
| Default Value                                         | Default value returned when no match found. It is also returned if the node has no value and the fragment option is not selected. |                         |

To  allow for use in a <u>ForEach Controller</u>,  the following variables are set on return:

* `refName` - set to first (or only) match; if no match, then set to default
* `refName_matchNr` - set to number of matches (may be 0)
* `refName_n` - n=1,2,3, etc. Set to the 1<sup>st</sup> , 2<sup>nd</sup>, 3<sup>rd</sup> match etc.

> Note: The next `refName_n` variable is set to `null` - e.g. if there are 2 matches, then `refName_3` is set to `null`, and if there are no matches, then `refName_1` is set to null.

XPath is query language targeted primarily for XSLT transformations. However it is useful as generic query language for structured data too. See XPath Reference or XPath specification for more information. Here are few examples:

`/html/head/title`

​			extracts title element from HTML response

`/book/page[2]`

​			extracts 2<sup>nd</sup> page from a book

`/book/page`

​			extracts all pages from a book

`//form[@name='countryForm']//select[@name='country']/option[text()='Czech Republic']/@value`

​			extracts value attribute of option element that match text ‘Czech Republic’ inside of select element with name attribute ‘country’ inside of form with name attribute `‘countryForm`’

> When “Use Tidy” is checked on - resulting XML document may slightly differ from original HTML response:
>
> * All elements and attribute names are converted to lowercase
> * Tidy attempts to correct improperly nested elements. For example - original (incorrect) `ul/font/li` becomes correct `ul/li/font`

> NAMESPACES
>
> As a work-round for namespace limitations of the Xalan XPath parser(implementation on which JMeter is based) you need to :
>
> * provide a Properties file (if for example your file is named `namespaces.properties`) which contains mappings for the namespace prefixes:
>
> 	```properties
> 	prefix1=http\://foo.apache.org
> 	prefix2=http\://toto.apache.org
> 	...
> 	```
>
> * reference this file in `user.properties` file using the property:
>
> 	```properties
> 	xpath.namespace.config=namespaces.properties
> 	```
>
> ```xquery
> //mynamespace:tagname
> //*[local-name()='tagname' and namespace-uri()='uri-for-namespace']
> ```

#### BeanShell PostProcessor

The BeanShell PreProcessor allows arbitrary code to be applied after taking a sample.

<u>BeanShell Post-Processor **no longer ignores samples with zero-length result data**.</u>

The test element supports the `ThreadListener` and `TestListener` methods. These should be defined in the initialization file. See the file `BeanShellListeners.bshrc` for example definitions.

| Attribute                                | Description                                                  | Required                            |
| ---------------------------------------- | ------------------------------------------------------------ | ----------------------------------- |
| Name                                     | Descriptive name for this element that is shown in the tree. The name is stored in the script variable `Label` | No                                  |
| Reset `bsh.Interpreter` before each call | If this option is selected, then the interpreter will be recreated for each sample. This may be necessary for some long running scripts. | Yes                                 |
| Parameters                               | Parameters to pass to the BeanShell script. The parameters are stored in the following variables:<br>* `Parameters` - string containing the parameters as a single variable<br>* `bsh.args` -  String array containing parameters, split on white-space | No                                  |
| Script file                              | A file containing the BeanShell script to run. The filename is stored in the script variable `FileName` | No                                  |
| Script                                   | The BeanShell script. The return value is ignored.           | Yes(unless script file is provided) |

The following BeanShell variables are set up for use by the script:

* log - (Logger) - can be used to write to the log file

* ctx - (JMeterContext) - gives access to the context

* vars - (JMeterVariables) - gives read/write access to variables:

	```bash
	vars.get(key);
	vars.put(key, val);
	vars.putObject("OBJ1", new Object());
	```

* props - (JMeterProperties - class `java.util.Properties`) - e.g. `props.get("START.HMS");` `props.put("PROP1", "1234");`

* prev -  (SampleResult) - gives access to the previous SampleResult

* data - (byte []) - gives access to the current sample data

If the property `beanshell.postprocessor.init` is defined, this is used to load an initialization file, which can be used to define methods etc. for use in the BeanShell script.

#### JSON Extractor

The JSON PostProcessor enables you extract data from JSON responses using JSON-PATH syntax. This post processor is very similar to Regular expression extractor. It must be placed as a child of HTTP Sampler or any other sampler that has responses. It will allow you to extract in a very easy way text content.

| Attribute                 | Description                                                  | Required |
| ------------------------- | ------------------------------------------------------------ | -------- |
| Name                      | Descriptive name for this element that is shown in the tree. | No       |
| Name of created variables | Semi-colon separated names of variables that will contain the results of JSON-PATH expressions (must match number of JSON-PATH expressions) | Yes      |
| JSON Path Expressions     | Semi-colon separated JSON-PATH expressions (must match number of variables) | Yes      |
| Match No. (0 for Random)  | If the JSON Path query leads to many results, you can choose which one(s) to extract as Variables:<br>* 0: means random(Default Value)<br>* -1: means extract all results, they will be named as `<variable name>_N` (where N goes from 1 to Number of results)<br>* X: means extract the X<sup>th</sup> result. If this X<sup>th</sup> is greater than number of matches, then nothing is returned. Default value will be used | No       |
| Compute concatenation var | If many results are found, plugin will concatenate them using ‘,’ separator and store it in var named `<variable name>_ALL` | No       |
| Default Values            | Semi-colon separated default values if JSON-PATH expressions do not return any result(must match number of variables) | No       |

### 18.9 Miscellaneous Features

#### Test Plan

The Test Plan is where the overall settings for a test are specified.

Static variables can be defined for values that are repeated throughout a test, such as server names.

#### Thread Group



#### WorkBench

#### HTTP(S) Test Script Recorder

##### HTTPS recording and certificates

##### Installing the JMeter CA certificate for HTTPS recording

###### Installing the certificate in Firefox

###### Installing the certificate in Chrome or Internet Explorer

###### Installing the certificate in Opera

##### Recording and redirects

##### Includes and Excludes

##### Capturing binary POST data

##### Adding timers

##### Where Do Samples Get Recorded?

##### Handling of HTTP Request Defaults

##### User Defined Variable replacement

##### How can I record the server’s responses too?

##### Associating requests with responses

##### Cookie Manager

##### Authorization Manager

##### Uploading files

##### Recording HTTP Based Non Textual Protocols not natively available in JMeter

#### Debug Sampler

The Debug Sampler generates a sample containing the values of all JMeter variables and/or properties.

The values can be seen in the <u>View Results Tree</u> Listener Response Data pane.



#### Test Fragment



#### setUp Thread Group

#### tearDown Thread Group









[^1]: specific to something: *formal* limited to or affecting only one particular thing
[^2]: Some fatal errors may still invoke `System.exit()`

[^3]:  a Latin phrase (or its abbreviation) used to indicate that special attention should be paid to something

[^4]: 协调遗漏问题，可参考[七层网络性能基准测试中的协调遗漏问题--Coordinated Omission](https://blog.csdn.net/minxihou/article/details/97318121)和[性能测试工具的 Coordinated Omission 问题](https://www.jianshu.com/p/bfb2b0f50edd)

