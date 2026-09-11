---
title: 'Print to console without using semi colon'
author: "Jasdeep Singh"
date: Thu, 24 Apr 2008 13:27:50 +0000
slug: 'print-to-console-without-using-semi-colon'
draft: false
excerpt: "A Java programming trick for printing to the console without using a semicolon, by exploiting an if-statement expression."
categories: ['Programming']
---

One of my friend asked : "How can one write to console without using semi colon in Java ?". I tried many work-arounds . Even Googling did net help much .

I thought i should raise an exception some how thats it some thing will be written on the console. Naa , its did not work well.

Then a stupid workaround was to enable the verbose argument , thats it every class loaded in the JVM is traces on console.

The some how i tried real tricks to print my name on console ,

This is what i got,

```
 `public class Test {

 public static void main(String a[]){

 if ( System.out.append("jasdeep") instanceof Object ){` 

 `}
         }
  }` 
You might be wondering , why i did not use _System.out.println()_ . Because it does not return anything , So it can not be compared in if block.

_Crossposted from [https://jasdeepsingh.wordpress.com/2008/04/24/print-to-console-without-using-semi-colon/](https://jasdeepsingh.wordpress.com/2008/04/24/print-to-console-without-using-semi-colon/)_


```
---
### Comments:
#### [Renegade Eye](http://advant.blogspot.com "MrMarvin2000@juno.com") - <time datetime="2008-04-24 19:43:42">Apr 4, 2008</time>

I returned the favor and linked back to this blog. It is alphabetical under /.
<hr />
#### [Jasdeep](http://jasdeepsingh.wordpress.com/ "jsbhangra@gmail.com") - <time datetime="2008-04-25 02:54:06">Apr 5, 2008</time>

Its my Pleasure , to be on Renegade Eye blogroll
<hr />
#### [herbal colon cleanse](http://www.detoxreviews.com "dannie3@hotmail.com") - <time datetime="2008-08-09 07:38:48">Aug 6, 2008</time>

i get it now.. thanks! -Anne
<hr />
#### [Rolland](http://www.xfire.com/blog/karadunaway/4442014/ "rollandwilber@gawab.com") - <time datetime="2012-11-16 08:54:22">Nov 5, 2012</time>

I know this if off topic but I'm looking into starting my own blog and was curious what all is required to get set up? I'm assuming having a blog like yours would cost a pretty penny? I'm not very web savvy so I'm not 100% positive. Any tips or advice would be greatly appreciated. Appreciate it
<hr />
#### [Jasdeep](http://jasdeepsingh.wordpress.com/ "jsbhangra@gmail.com") - <time datetime="2012-11-16 09:01:28">Nov 5, 2012</time>

Rolland, On the contrary, Having a blog like mine would not cost you a single penny. just go to [wordpress.com](http://wordpress.com), Sign up and start writing your posts. It's just like email, just that your ever email is public. Regards, Jasdeep
<hr />
#### [puracleansereview.com](http://blogs.albawaba.com/kasha94f/104868/2013/02/11/590410-how-beneficial-is-a-pure-colon-cleanse "ricky.hargrave@gmail.com") - <time datetime="2013-02-19 22:01:38">Feb 2, 2013</time>

Thanks to my father who stated to me about this blog, this website is actually remarkable.
<hr />
