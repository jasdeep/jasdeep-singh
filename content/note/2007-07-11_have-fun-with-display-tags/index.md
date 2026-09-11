---
title: 'Have Fun With Display Tags'
author: "Jasdeep Singh"
date: Wed, 11 Jul 2007 20:26:25 +0000
slug: 'have-fun-with-display-tags'
draft: false
excerpt: "Introduces using the Display Tags library to add pagination to JSP pages instead of writing custom pagination logic."
categories: ['Programming']
---

Most of the time we get large chunk of data on a view page say there are more then 20 records to be shown , which makes it untidy and scrolling.. So there are many solutions to this problem, that is we have to implement pagination in our code . first solution is to develop your own programming logic for pagination, its good bid if you are a proud geek .. and you make your own way... But i opted for second option that is to look for an already available solution on the web and i found it easily ... [Display Tags](http://displaytag.sourceforge.net/11/) is my bet fo pagination...

they are very easy to use with JSP/Servlets application , provided you send arraylist of the Java Beans you populate to view records... Look at this [tut](http://displaytag.sourceforge.net/10/tut_basic.html) . Its makes your jsp code neat and gives you a paged output...

You may find an issue if you are using struts ,as the case with me... that is you are unable to next output page.. for that there is [support](http://displaytag.sourceforge.net/10/faq.html#action) provided by them.

Just download the display tag jar and use in you web app .. have fun with pagination...

_Crossposted from [https://jasdeepsingh.wordpress.com/2007/07/11/have-fun-with-display-tags/](https://jasdeepsingh.wordpress.com/2007/07/11/have-fun-with-display-tags/)_