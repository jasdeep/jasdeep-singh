---
title: 'My Shell history'
author: "Jasdeep Singh"
date: Fri, 11 Apr 2008 06:16:37 +0000
slug: 'my-shell-history'
draft: false
excerpt: "Shares an awk one-liner that analyzes shell command history to humorously reveal procrastination habits."
categories: ['awk', 'Programming', 'Script', 'shell']
---

When i opened my Google reader this morning , cam across this little awk kiddie. So ran it for my ubuntu shell. It tells the story that i have not been doing anything worthy , only procrastinating

`history|awk '{a[$2]++ } END{for(i in a){print a[i] " " i}}' |sort -rn|head 84 cd 66 ls 43 sudo 15 python 10 django-admin.py 6 svn 6 ln 4 youtube-dl 4 pidgin 4 cd..`

The original script lies [here](http://www.dehora.net/journal/2008/04/10/that-looks-about-right/).

_Crossposted from [https://jasdeepsingh.wordpress.com/2008/04/11/my-shell-history/](https://jasdeepsingh.wordpress.com/2008/04/11/my-shell-history/)_

---
### Comments:
#### [Book Meme &laquo; /home/jasdeep](http://jasdeepsingh.wordpress.com/2008/11/14/book-meme/ "") - <time datetime="2008-11-14 05:45:58">Nov 5, 2008</time>

\[...\] 14, 2008 in PersonalTags: books, poetry After shell meme hit the blogging world some months back , its time for Book \[...\]
<hr />
