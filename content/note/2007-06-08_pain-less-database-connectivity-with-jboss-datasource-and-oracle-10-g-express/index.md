---
title: 'Pain-Less Database Connectivity with Jboss datasource and Oracle 10 g express'
author: "Jasdeep Singh"
date: Sat, 19 May 2007 09:48:43 +0000
slug: 'pain-less-database-connectivity-with-jboss-datasource-and-oracle-10-g-express'
draft: false
excerpt: "A step-by-step guide to configuring a JBoss datasource to connect to Oracle 10g Express Edition."
categories: ['Programming']
---

It will be pain less for you guys as i beared the pain configuring my application to connect to database with jboss datasource . so here are the steps for that : I used JBoss version 4.0.5 and Oracle 10g express edition . both are downloadable freely from internet Then i found the suitable driver for me as i was using java version 1.5 so i downloaded thin driver ojdbc.jar . Then i googled and followed some suitable links :

1\. Copied the thin oracle driver (ojdbc14.jar) in server\\default\\lib directory of JBOSS\_HOME.

2\. Copied the oracle-ds.xml file from docs\\examples\\jca directory of JBOSS\_HOME to server\\default\\deploy of JBOSS\_HOME. Configured it for my use "oracleDS" is the name for my datasource , its type matching OracleXE was also defined by (explained later) which reads as: `<datasources> <local-tx-datasource> <jndi-name>oracleDS</jndi-name> <connection-url>jdbc:oracle:thin:@localhost:1521:XE</connection-url> <driver-class>oracle.jdbc.driver.OracleDriver</driver-class> <user-name>hr</user-name> <password>hr</password> <exception-sorter-class-name>org.jboss.resource.adapter.jdbc.vendor.OracleExceptionSorter</exception-sorter-class-name> <metadata> <type-mapping>OracleXE</type-mapping> </metadata> </local-tx-datasource> </datasources>`

3.Changed to server\\default\\conf of JBOSS\_HOME and edited standardjaws.xml for my use. added the following entry on the top under jaws element . `<datasource>java:/oracleDS</datasource> <type-mapping>OracleXE</type-mapping>` the type defination of OracleXE is not provided by default , i simply copied the type defination of Oracle8 and renamed it a OracleXE. (may be its not professional approach but there was no other alternative ) It works fine.

4.Edited standardjbosscmp-jdbc.xml and added `<datasource>java:/oracleDS</datasource>` again defined the type matching here as in third step.

5.Edited login-config.xml ,added OracleDb realm as following :

`<application-policy name="OracleDbRealm" > <authentication> <login-module flag="required" code="org.jboss.resource.security.ConfiguredIdentityLoginModule" > <module-option name="principal" >sa</module-option> <module-option name="userName" >sa</module-option> <module-option name="password" /> <module-option name="managedConnectionFactoryName" >jboss.jca:service=LocalTxCM,name=oracleDS</module-option> </login-module> </authentication> </application-policy>` Thats it JBoss is ready ,

Now add the code like this in your jsp file

`InitialContext ctx = new InitialContext(); DataSource ds = (DataSource)ctx.lookup("java:oracleDS"); Connection con = ds.getConnection();`

and you can do it.

There is another way for connecting to data source which is :

I faced many problem in connecting and had to take help from [JBoss forums Link](http://www.jboss.com/index.html?module=bb&op=viewtopic&p=4046767#4046767) [](http://www.jboss.com/index.html?module=bb&op=viewtopic&p=4046767#4046767) , it realy helped.

Thats it restart JBoss server and have fun.

_Crossposted from [https://jasdeepsingh.wordpress.com/2007/05/19/pain-less-database-connectivity-with-jboss-datasource-and-oracle-10-g-express/](https://jasdeepsingh.wordpress.com/2007/05/19/pain-less-database-connectivity-with-jboss-datasource-and-oracle-10-g-express/)_

---
### Comments:
#### [amardeep]( "tanwar.amar@gmail.com") - <time datetime="2007-12-01 11:18:55">Dec 6, 2007</time>

jasdeep, i want to connect to remote database. having ip say 111.111.111.111 . while making connection wid oracle, i used the connection string jdbc:oracle:thin@ip:1521(port of oracle listener):SID user pwd. wen i used this string. it gives an error. please help me out thanx in advance..
<hr />
