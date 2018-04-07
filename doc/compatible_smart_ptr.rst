++++++++++++++++++++++++++++++++++
 |Boost| Pointer Container Library
++++++++++++++++++++++++++++++++++
 
.. |Boost| image:: boost.png

Compatible Smart Pointer Type
-----------------------------

The interface reference for this library makes use of the pseudo-type

.. parsed-literal::
   *compatible-smart-ptr*\ <T>

to indicate that either ``std::auto_ptr<T>`` or
``std::unique_ptr<T>`` is being used depending on the compiler C++ standard.

**Details:**

The ISO C++11 standard saw the addition of the smart pointer class template
``std::unique_ptr<T>``, and with it the formal deprecation of
``std::auto_ptr<T>``. After spending C++11 and C++14 with deprecated
status, ``std::auto_ptr<T>`` has been formally removed as of
the ISO C++17 standard. As such, headers mentioning
``std::auto_ptr<T>`` may be unusable in standard library
implementations which disable ``std::auto_ptr<T>`` when C++17 or later
is used. Boost.Pointer Container predates the existence of
``std::unique_ptr<T>``, and since Boost v. ``1.34`` it has provided
``std::auto_ptr<T>`` overloads for its interfaces. To provide
compatibility across a range of C++ standards, macros are used for
compile-time replacement of ``std::auto_ptr<T>`` interfaces with
``std::unique_ptr<T>`` interfaces.

`Boost.Config <../../config/index.html>`_ defines the macro
``BOOST_NO_CXX11_SMART_PTR`` for compilers where
``std::unique_ptr<T>`` is not available. For such compilers,
Boost.Pointer Container provides function overloads which use
``std::auto_ptr<T>``. Otherwise, these overloads will use
``std::unique_ptr<T>`` instead. Thus, all mentions of

.. parsed-literal::
   *compatible-smart-ptr*\ <T>

shall be understood to mean that `Boost.Config
<../../config/index.html>`_ has been used as outlined above to provide
a smart pointer interface that is compatible with compiler settings.

**Navigate**

- `home <ptr_container.html>`_
- `reference <reference.html>`_

.. raw:: html 

        <hr>

:Copyright:     Thorsten Ottosen 2004-2006. Use, modification and distribution is subject to the Boost Software License, Version 1.0 (see LICENSE_1_0.txt__).

__ http://www.boost.org/LICENSE_1_0.txt

