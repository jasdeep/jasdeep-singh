---
title: 'Lisp, Python and Java'
author: "Jasdeep Singh"
date: Tue, 29 Jan 2008 07:11:54 +0000
slug: 'lisppython-and-java'
draft: false
excerpt: "A technical post comparing Lisp, Python, and Java implementations of a simple SICP exercise on summing squares of the two largest numbers."
categories: ['LISP', 'Programming', 'Python']
---

While acting on my new year resolutions, I started reading the [SICP](http://mitpress.mit.edu/sicp/) book . The book focuses on the aspects of computer programming fundamentals and making the reader learn this by problem solving through [LISP](en.wikipedia.org/wiki/Lisp_programming_language)  programming language.

So in the first chapter i had to solve some problems , and one of them was :

_Define a procedure that takes three numbers as arguments and returns the sum of the squares of the two larger numbers._

So my implementation of this problem in LISP is here :

`(defun square(x) (* x x) ) (defun sum-of-square(x y) (+ (square x) (square y))) (defun grt(a b) (if(> a b) a b)) (defun grt-2-sum-of-square (a b c ) (sum-of-square (grt a b) (grt b c) ) ) (grt-2-sum-of-square 1 2 3)`

I implemented the same problem with [python](http://www.python.org/) as following :

`#Returns Square def square(x): return x*x #Returns Sum of the Squares def sum_of_square(x,y): return square(x)+square(y) #Returns greater number def grt(a,b): if (a>b): return a else: return b #Returns the sum fo square of greater numbers def grt_2_sum_of_square(x,y,z): a=grt(x,y) b=grt(y,z) return sum_of_square(a,b) # If main mein module is called if __name__=="__main__": #print result print grt_2_sum_of_square(1,2,3)`

and implementation of same problem in [Java](en.wikipedia.org/wiki/Java_(programming_language)) goes like this :

`public class Test { // Returns the Square public int square(int x){ return x*x; } // Returns sum of the Squares public int sum_of_square(int x,int y){ return square(x)+square(y); } //Returns greater number public int grt(int x,int y){ return (x>y)?x:y; } //Return the sum fo square of greater numbers public int grt_2_sum_of_square(int x,int y,int z){ int a=grt(x,y); int b=grt(y,z); return sum_of_square(a,b); } // Main Method public static void main(String a[]){ //instantiates class Test t=new Test(); int res=t.grt_2_sum_of_square(1, 2, 3); System.out.print(res); } }`

There are easier ways of implementing it in python and Java though . But i preferred these as i implemented the same LISP construct. I am amused by the simplicity and cleanliness of LISP code here and no. of lines i had to write for doing this.

I wish i should have been taught LISP in school and i would have been a better programmer :)

Python gives me pleasure of code elegance and simplicity, but Java is the one i am working with . The one that got me a Job.

Learning new things make me feel better, that there is no end to learning.

Powered by [ScribeFire](http://scribefire.com/).

_Crossposted from [https://jasdeepsingh.wordpress.com/2008/01/29/lisppython-and-java/](https://jasdeepsingh.wordpress.com/2008/01/29/lisppython-and-java/)_

---
### Comments:
#### [paddy3118](http://paddy3118.blogspot.com "paddy3118@gmail.com") - <time datetime="2008-01-30 01:53:36">Jan 3, 2008</time>

Hi Jasdeep, That Python solution truly awful :-) Sorry to say it but I considered being more circumspect, and I can see that you wanted to code it like the Lisp solution, but given the problem and a chance to solve it without reference to solutions on other languages then I would write something like: >>> def sumofmax2(a,b,c): return sum(sorted(\[x\*x for x in \[a,b,c\]\])\[-2:\]) ... >>> sumofmax2(2,1,3) 13 >>> Where I have kept the function signature quite like your Lisp one. A further Python idiom would be to allow two or more arguments and find the sum of the two largest like this: >>> def sumofmax2(\*args): return sum(sorted(\[x\*x for x in args\])\[-2:\]) ... >>> sumofmax2(2,1,3) 13 >>> sumofmax2(2,-5,1,3) 34 >>> I am not sure of how much Python you know, but lists are very useful things in Python :-) - Paddy.
<hr />
#### [ਜਸਦੀਪ](http://jasdeepsingh.wordpress.com/ "jsbhangra@gmail.com") - <time datetime="2008-01-30 05:04:00">Jan 3, 2008</time>

Hi Paddy.. Thanks for sharing your thoughts. I appreciate your criticism. Yes, i am a python beginner , I have read more python literature than practicing it. I will now practice it more and more. Python is really great , it did the same thing in one line . -Jasdeep
<hr />
#### [Chris]( "cwt_89@hotmail.com") - <time datetime="2008-02-24 00:42:15">Feb 0, 2008</time>

You could actually get that LISP solution down to just 3 lines of code: (define (grt-2-sum-of-square x y z) (define (square n) (\* n n)) (+ (square (max x y)) (square (max (min x y) z))))
<hr />
#### [Noah](http://noahsmark.com "dakeyras@gmail.com") - <time datetime="2008-08-13 20:26:30">Aug 3, 2008</time>

First, your posted solutions all have an error - if the second argument ("b" in the lisp solution, "y" in the other two) is the largest number, it will be returned from both (grt a b) and (grt b c), so you are going to compute the sum of b's square twice. You can do the Lisp in "one line" as well with "loop", which is roughly equivalent to using list/generator comprehensions in python: (defun max-2-squared (&rest values) (loop for x in (subseq (sort values #'>) 0 2) sum (\* x x))) This reads just like the short python example to me. It requires some extra keystrokes, as a few things in python end up being slightly more succinct (like python's nice slicing notation), but they still feel fundamentally equivalent. Alternatively, you can avoid "loop" (as some do) with: (defun max-2-squared (&rest values) (reduce #'+ (subseq (mapcar (lambda (x) (\* x x)) (sort values #'>)) 0 2))) A few more keystrokes, but still reads about the same to me. Also, the python implementation from Paddy is slightly incorrect - you need sum the squares of the largest two numbers, not take the sum of the largest two squares (it matters when numbers are negative). It should be: def sumofmax2(\*args): return sum(\[x\*x for x in sorted(args)\]\[-2:\]) -Noah
<hr />
