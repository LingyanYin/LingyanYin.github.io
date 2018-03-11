---
layout: post
title: Why Auto, Decltype
date:   2017-06-08 21:29:00
categories: 
---

After reading the Chapter 1 and Chapter 2 of <<Effective Modern C++>>, I need to write some notes about the new features of type deduction in C++11. The contents below are all based on my own understanding.
auto and decltype are both based on the template type deduction. The type deduction happens during compilation time.

auto helps 1) avoid verbose typing of long type names; 2) avoid mismatch the real underlying types (for example, vector.size() returns size_type (32/64 bits in different machines), using auto could avoid mismatching); 3) delctype(auto) usage in C++14 helps combine two together: deducing a type from its initializer but performing the type deduction using the decltype rules. auto type deduction is same as template type deduction except that it assumes that a braced initializer represents a std::initializer_list, template type deduction does not.

decltype almost produces the type of a variable or expression without any modification. One situation requires attention: For lvalue expression other than names of type T, decltype always reports a type of T& (int x=10, decltype(x) is T; decltype((x)) is T&).

auto and template type deduction treat arguments that are references as non-references. When deducing types for by-value parameters, const, volatile arguments are treated as non-const and non-volatile.

Reference

Meyers, Scott. Effective modern C++: 42 specific ways to improve your use of C++ 11 and C++ 14. " O'Reilly Media, Inc.", 2014.
