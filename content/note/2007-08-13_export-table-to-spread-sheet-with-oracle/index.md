---
title: 'Export Table To Spread Sheet with Oracle..'
author: "Jasdeep Singh"
date: Fri, 20 Jul 2007 12:21:49 +0000
slug: 'export-table-to-spread-sheet-with-oracle'
draft: false
excerpt: "Shares SQL*Plus spool scripts for exporting Oracle database tables to Excel spreadsheets, including a multi-table shell script."
categories: ['Programming']
---

I used to hate oracle due to [this](http://jasdeepsingh.wordpress.com/2007/06/14/how-oracle-bugged-me/) .. I hated its bulkyness and hype... Money it makes with DBA certifications... Quite Similar to Microsoft's strategies...

But as i have to work on Oracle, So i have to dig more , Though i have not reached some cgood performance measure to tune Oracle.. Except altering process size .. I have been working on stored procedures, and quite curious excited about using them...

Now moving the title topic .. as i was digging up for performance tuning .. Could not get much support through.. Thats why DBA's are paid much.. \[:)\]

I found this little sql script to export Table to a Spreadsheet document...and found that there is something in Oracle thats why Oracle is much hyped.. Its a powerful database...

It goes like this `set feed off markup html on spool on spool c:\mytable.xls select * from mytable; spool off set markup html off spool off`

If You are beginner like me .. Write this script with your favourite editor..and save it as filename.sql Go To Command line /Shell Change directory to the location of script u saved.. Run "sqlplus" prompt for me it was "sqlplus /nolog" as i am using Open Suse 10.2 .. after logging in : type `@filename` .. and it will export the spreadsheet to the location you mention .. In this cae to the same directory....

I got this from [Amardeep s blog](http://amardeepsidhu.blogspot.com/2007/06/spool-to-xls-file.html)..He got it somewhere from Oracle Forums...

If You want Read multiple table.. Then here is the script (Not for windows though ) : `cat list.txt | while read a do echo "spooling $a" sqlplus username/password@string <<EOF set feed off markup html on spool on spool /home/oracle/$a.xls select * from $a; spool off set markup html off spool off EOF done`

I got it from [here](http://amardeepsidhu.blogspot.com/2007/06/shell-script-to-spool-no-of-tables-into_26.html)

Have fun with Oracle ... If some one can give me help on performance tuning most welcome ... I am stuck with it...

_Crossposted from [https://jasdeepsingh.wordpress.com/2007/07/20/export-table-to-spread-sheet-with-oracle/](https://jasdeepsingh.wordpress.com/2007/07/20/export-table-to-spread-sheet-with-oracle/)_

---
### Comments:
#### [Sidhu](http://amardeepsidhu.blogspot.com "amardeepsidhu@gmail.com") - <time datetime="2007-08-13 17:12:45">Aug 1, 2007</time>

Jasdeep About the script to spool multiple tables, you wrote that "For Windows though" instead of "Not for Windows though" :) Sidhu
<hr />
#### [ਜਸਦੀਪ](http://jasdeepsingh.wordpress.com/ "jsbhangra@gmail.com") - <time datetime="2007-08-13 18:03:29">Aug 1, 2007</time>

expert comments accepted sir, i have changed it :)
<hr />
