---
title: 'Logging is in, System.out.println() is passe..'
author: "Jasdeep Singh"
date: Fri, 08 Jun 2007 14:29:51 +0000
slug: 'logging-is-in-systemoutprintln-is-passe'
draft: false
excerpt: "Explains switching from System.out.println debugging to log4j for configurable, file-based Java logging, including setup within JBoss."
categories: ['Programming']
---

I read somewhere in a technical book , "Writing Code without logging is like Driving in the fog without switching the lights "

As a beginner we use System.out.println() to print messages in Server log, that is pretty efficient for debugging purposes .But the problem with System.out.println()is that it is not descriptive .If we want to know which file is generating the message we have to identify our self, and moreover we are not able to generate separate log files

[log4j](http://logging.apache.org/log4j/docs/) mechanism is the answer to all these limitations. We can configure it to work as Console appender (like System.out.println()) and as a separate log file. Working with it is quite simple ,What we have to do is to just [download log4j](http://logging.apache.org/site/binindex.cgi) jar , set this in your application. write a sample log4j.properties file add it to WEB-INF/classes . `log4j.rootLogger=debug, stdout, R log4j.appender.stdout=org.apache.log4j.ConsoleAppender log4j.appender.stdout.layout=org.apache.log4j.PatternLayout log4j.appender.stdout.layout.ConversionPattern=%5p [%t] (%F:%L) - %m%n log4j.appender.R=org.apache.log4j.RollingFileAppender log4j.appender.R.File=example.log log4j.appender.R.MaxFileSize=100KB log4j.appender.R.MaxBackupIndex=1 log4j.appender.R.layout=org.apache.log4j.PatternLayout log4j.appender.R.layout.ConversionPattern=%p %t %c - %m%n`

hmm.. thats it now use it in place of System.out.println() ,just you have to instantiate a logger object .. as shown below :

`import org.apache.log4j.Logger; public class Test { static Logger logger = Logger.getLogger(Test.class); public void doIt() { logger.info("Info Logger!"); logger.debug("Debug Logger!"); logger.error("Error logger!"); } }`

Thats it.. we can specify multiple logging level i.e. INFO,DEBUG,WARN,ERROR,FATAL etc... that is the further you dig the more you get... if you want dig , check this [cool link](http://www.vipan.com/htdocs/log4jhelp.html).

The there is rolling file appender that is we can generate log file ,hourly , daily , weekly or monthly, that too very easily..

Hmmm ... Then i tried it for my appliaction wich is deployed on [JBoss](http://www.jboss.com/) server ..

But it gave errors saying that "OnlyOnceFileAppender Error" blah blah... that was due to the fact that jboss uses log4j internaly for logging... and i can't overload jboss logger with another..

So what i did i configured the jboss logging for my use .. and it was as smooth sailing afterwards .... what i did , went to `JBOSS_HOME/server/default/conf` and there was the file log4j.xml ... to configure it for my application what i had to do was to add one appender and one category element in log4j.xml .. look at this [jboss wiki](http://wiki.jboss.org/wiki/Wiki.jsp?page=ConfigureLogging) .. it tells the story what i did actually , i added following appender for my application in log4j.xml

One more thing i added was the category for appender... [Read This](http://wiki.apache.org/logging-log4j/Log4jXmlFormat) to Configure log4j.xml ..

Thats all ,get going with this logging and kick System.out.println() out of your code...

_Crossposted from [https://jasdeepsingh.wordpress.com/2007/06/08/logging-is-in-systemoutprintln-is-passe/](https://jasdeepsingh.wordpress.com/2007/06/08/logging-is-in-systemoutprintln-is-passe/)_