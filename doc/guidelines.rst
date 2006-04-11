++++++++++++++++++++++++++++++++++
 |Boost| Pointer Container Library
++++++++++++++++++++++++++++++++++
 
.. |Boost| image:: boost.png

================
Usage Guidelines
================

Choosing the right container
----------------------------

The recommended usage pattern of the container classes are the same as the 
for normal standard containers.  

``ptr_vector``, ``ptr_list`` and ``ptr_deque`` offer the programmer different 
complexity tradeoffs and should be used accordingly.  ``ptr_vector`` is the 
type of sequence that should be used by default.  ``ptr_list`` should be used 
when there are frequent insertions and deletions from the middle of the 
sequence and if the container is fairly large (eg.  more than 100 
elements).  ``ptr_deque`` is the data structure of choice when most insertions 
and deletions take place at the beginning or at the end of the sequence.  
The special container ``ptr_array`` may be used when the size of the container is invariant
and known at compile time.

An associative container supports unique keys if it may contain at most 
one element for each key. Otherwise, it supports equivalent keys.  
``ptr_set`` and ``ptr_map`` support unique keys.  
``ptr_multiset`` and ``ptr_multimap`` 
support equivalent keys.  

Recommended practice for Object-Oriented Programming
----------------------------------------------------

Idiomtic Object-Oriented Programming in C++ looks a bit different from 
the way it is done in other languages. This is partly because C++ 
has both value and reference semantics, and partly because C++ is more flexible
than other languages. Below is a list of recommendations that you are
encouraged to follow:

1. Make base classes abstract and without data
++++++++++++++++++++++++++++++++++++++++++++++

The has the following advantages:

	a. It reduces *coupling* because you do not have to maintain or update state

	..
		
        b. It helps you to avoid *slicing*
	
	..
	
        c. It ensures you *override* the right function

You might also want to read the following articles:

- Kevlin Henney's `Six of the best`__

.. __: http://www.two-sdg.demon.co.uk/curbralan/papers/SixOfTheBest.pdf

- Jack Reeves' `Multiple Inheritance Considered Useful`__

.. __: http://www.ddj.com/documents/s=10011/q=1/cuj0602reeves/0602reeves.html

  
2. Make virtual functions private and provide a non-virtual public forwarding function
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

This has the following advantages:

	a. It makes sure all calls to the virtual function always goes through one place in your code
	
	..
	
	b. It enables you to check preconditions and postconditions inside the forwarding function

You might also want to read Herb Sutter's article `Virtuality`__.

.. __: http://www.gotw.ca/publications/mill18.htm

3. Derive your base class from ``boost::noncopyable``
+++++++++++++++++++++++++++++++++++++++++++++++++++++

Having an abstact base class prevents slicing when the base class is involved, but
it does not prevent it for classes further down the hierarchy. This is where
`boost::noncopyable`__ is handy to use.

.. __ : http://www.boost.org/libs/utility/utility.htm#Class_noncopyable



4. don't allow nulls if you can avoid it, Null Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++


**Navigate:**

- `home <ptr_container.html>`_
- `reference <reference.html>`_

:copyright:     Thorsten Ottosen 2004-2005. 

