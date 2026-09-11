---
title: 'How Oracle Bugged Me ..'
author: "Jasdeep Singh"
date: Thu, 14 Jun 2007 13:59:27 +0000
slug: 'how-oracle-bugged-me'
draft: false
excerpt: "Describes fixing an Oracle ORA-12519 listener error by increasing the PROCESSES setting via ALTER SYSTEM."
categories: ['Programming']
---

ORA-12519, TNS:no appropriate service handler found

was the error i was getting whenever i ran my application deployed on Jboss and Oracle 10g XE as database server. I used every trick in my tiny brain ,varying from using DBCP connection pooling,Container managed Connection pooling, Setting the no. of connection to very high value.. etc. etc... But this error was inevitable . I was going nuts ,googled around for this thousand times... But luckily i found an [blog post](http://it.newinstance.it/2007/06/01/ora-12519-tnsno-appropriate-service-handler-found/) with the same problem. Here are the guy's thoughts on this (Same as mine are): _I used to hate Oracle Database (and other Oracle products too) because of it is much more complicated / heavyweight / slow / buggy and full of useless and sometime harmful stuff than needed. Also when you install you can’t remove it without leaving tons of zombie files around, breaking your JVM/Apache/Windows/etc. After an Oracle installation, your system will never be as before. And hey, have you ever seen an “universal installer” more pathetic than the oracle one?_ what i got was that it was not problem at the connection pooling end . There was a bug in oracle which caused this , and issuing the following command at SQL command line will fix it (after restarting the listener): `“ALTER SYSTEM SET PROCESSES=150 SCOPE=SPFILE;”.`.. hmm thats it it worked for me.. Thanx Google and [Mr.Luigi](http://it.newinstance.it/author/luigi/) (Guy who wrote that blog post)...

_Crossposted from [https://jasdeepsingh.wordpress.com/2007/06/14/how-oracle-bugged-me/](https://jasdeepsingh.wordpress.com/2007/06/14/how-oracle-bugged-me/)_

---
### Comments:
#### [Luigi](http://www.newinstance.it "luigi.viggiano@newinstance.it") - <time datetime="2007-06-15 07:48:30">Jun 5, 2007</time>

You are welcome! :)
<hr />
#### [Export Table To Spread Sheet with Oracle.. &laquo; /home/jasdeep](http://jasdeepsingh.wordpress.com/2007/07/20/export-table-to-spread-sheet-with-oracle/ "") - <time datetime="2007-07-20 12:21:57">Jul 5, 2007</time>

\[...\] July 20, 2007 Posted by ਜਸਦੀਪ in Oracle, Script. trackback I used to hate oracle due to this .. I hated its bulkyness and hype… Money it makes with DBA certifications… Quite \[...\]
<hr />
#### [Michael]( "ferbermichael@yahoo.de") - <time datetime="2008-01-02 09:03:21">Jan 3, 2008</time>

Thanks for that workaround. Helped my like a charm.
<hr />
#### [ਜਸਦੀਪ](http://jasdeepsingh.wordpress.com/ "jsbhangra@gmail.com") - <time datetime="2008-01-02 09:29:02">Jan 3, 2008</time>

My Pleasure Michael.. I was helped by Mr Luigi. on this ... and one Above all Google..
<hr />
