---
title: 'When Synchrozation Fails in Java'
author: "Jasdeep Singh"
date: Mon, 21 Apr 2008 10:46:25 +0000
slug: 'when-synchrozation-fails-in-java'
draft: false
excerpt: "Explains how Collections.synchronizedList can still throw thread-safety exceptions under multiple threads, and how block-level synchronization fixes it."
categories: ['Programming', 'synchronisation', 'threads']
---

My blog title goes like "Ramblings about workplace, java, python, linux and web " . But my recent posts were distracted from this tagline. The frank answer to this is I was procrastinating. It is not i have not been learning much. I have learnt a lot of new things professionally but could not get them together to share my learning on the blog.

I was surfing the web to dig deep into Java, When i came across this [great post](http://rayfd.wordpress.com/2007/11/11/when-a-synchronized-class-isnt-threadsafe/) by [Curious Schemer](http://rayfd.wordpress.com/).

Mr Ray deliberately explains things in the post that we are rhetorically asked to use ArrayList over Vector for better performance . If we need to make it thread safe. We do it this way : `List list = Collections.synchronizedList(new ArrayList());` But it does not solves the purpose. The thread safety breaks if we do something like this : `final List list = Collections.synchronizedList(new ArrayList()); final int nThreads = 1; ExecutorService es = Executors.newFixedThreadPool(nThreads); for (int i = 0; i < nThreads; i++) {   es.execute(new Runnable() {   public void run() {   while(true) {   try {   list.clear();   list.add("888");   list.remove(0);   } catch(IndexOutOfBoundsException ioobe) {   ioobe.printStackTrace();   }   }   }   }); }`

> As long nThreads is 1, everything runs just fine. However, increase the number of nThreads to 2, and you start getting this:
> 
> java.lang.IndexOutOfBoundsException: Index: 0, Size: 0
> 
> at java.util.ArrayList.RangeCheck(Unknown Source)
> 
> at java.util.ArrayList.remove(Unknown Source)
> 
> at java.util.Collections$SynchronizedList.remove(Unknown Source)

Now the workaround to get away with this problem , is to use block level synchronization . Synchronize the methods which update the list to the fine grain level is the best approach to avoid such exceptions .

`synchronized (list) {   list.clear();   list.add("888");   list.remove(0); }`

I learnt my lesson here , one should use atomic level synchrozation to keep the performance and effeciency intact.

The [Full Post](http://rayfd.wordpress.com/2007/11/11/when-a-synchronized-class-isnt-threadsafe/) by Mr.Ray is worth read it explains further conflicts in using synchronization .

_Crossposted from [https://jasdeepsingh.wordpress.com/2008/04/21/when-synchrozation-fails-in-java/](https://jasdeepsingh.wordpress.com/2008/04/21/when-synchrozation-fails-in-java/)_