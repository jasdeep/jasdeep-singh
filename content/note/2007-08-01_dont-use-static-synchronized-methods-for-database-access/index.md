---
title: 'Don''t use static synchronized methods for database access'
author: "Jasdeep Singh"
date: Wed, 01 Aug 2007 17:44:34 +0000
slug: 'dont-use-static-synchronized-methods-for-database-access'
draft: false
excerpt: "Warns against static synchronized methods for database access due to performance bottlenecks and recommends the DAO pattern instead."
categories: ['Programming']
---

I was busy performance tuning my J2EE application in fact struts based web application . I came to know about a serious design issue , as i was using singleton design pattern (i guess) in my database access logic . That is all the methods for every database class were declared static , and to keep thread safety they were synchronized. `public class MyDBAccessor { public static synchronized void accessMyDBFirst(){ // The logic for accessing the database } public static synchronized void accessMyDBSecond(){ // The logic for accessing the database } }`

But the above code has severe performance penalty as for multiple threads accessing the database , if one thread , say T1 acquires the lock of accessMyDBFirst() , but in fact it locks the whole class methods , that another thread T2 which requires to access accessMyDBSecond() method must wait until the first T1 relieves the lock.

So this mechanism makes more more threads to wait i.e. more requests to wait which severely degrades the performance and response time.

So my sincere advice is **not to use above code logic** in your database access code logic ..

So i had to rework all of my database code in order to improve performance , i just did one thing **removed static keyword** in above code logic , and for every method access i instantiated the class from a static factory method . This approach subsequently improves performance and response time. The second approach is apparently actual [DAO (data access object)](http://java.sun.com/blueprints/corej2eepatterns/Patterns/DataAccessObject.html) pattern approach . My first implementation of Data access logic was wrong and did not stick to the DAO design pattern.

So i will implementing the from DAO's next time . Further I am curious about [ORM](http://en.wikipedia.org/wiki/Object-relational_mapping) too . [hibernate](http://www.hibernate.org/) is buzzword these days .Hopefully we will use hibernate this time.

I will appreciate your thoughts on above post..

_Crossposted from [https://jasdeepsingh.wordpress.com/2007/08/01/dont-use-static-synchronized-methods-for-database-access/](https://jasdeepsingh.wordpress.com/2007/08/01/dont-use-static-synchronized-methods-for-database-access/)_

---
### Comments:
#### [Rupinder]( "rupinder4183@yahoo.com") - <time datetime="2008-04-24 10:38:52">Apr 4, 2008</time>

Hi dude, it is a obvious good post. I remember of making a similar blunder in an earlier project. Alas, I can't do anything to that but will beware of this from now. Thanx....
<hr />
