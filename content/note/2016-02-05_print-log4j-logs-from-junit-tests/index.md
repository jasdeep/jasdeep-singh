---
title: 'Print log4j logs from jUnit tests'
author: "Jasdeep Singh"
date: Fri, 05 Feb 2016 07:28:15 +0000
slug: 'print-log4j-logs-from-junit-tests'
draft: false
excerpt: "A short code snippet showing how to configure log4j to print logs to the console during JUnit test runs."
categories: ['Programming']
---

```
static {
    Logger rootLogger = Logger.getRootLogger();
    rootLogger.setLevel(Level.INFO);
    rootLogger.addAppender(new ConsoleAppender(
            new PatternLayout("%-6r \[%p\] %c - %m%n")));
}
```

_Crossposted from [https://jasdeepsingh.wordpress.com/2016/02/05/print-log4j-logs-from-junit-tests/](https://jasdeepsingh.wordpress.com/2016/02/05/print-log4j-logs-from-junit-tests/)_