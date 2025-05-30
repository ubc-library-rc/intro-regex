---
layout: default
title: What are regular expressions?
nav_order: 5
---
# What are regular expressions?

In this section we will learn about what regular expressions are, and learn some of the basic syntax of regular expressions.

## Regular expressions

A regular expression is a series of special characters that describe a _pattern_ in a string of text according to a standardized set of rules. This pattern gets compared to the string and either it matches or doesn't - it's kind of like the 'find' function but with superpowers. Regular expressions are often called regex for short.

Some regular expressions can be difficult to read at first because every character in the expression has a specific rule-defined meaning. For example, the regular expression below contains letters, numbers, and punctuation to describe a typical username consisting of a specific number of lowercase characters and numbers as well as, optionally, an underscore or hyphen:

![Anatomy of a regular expression](images/regexp-en.png)

(Image from [Learn Regex the Easy Way](https://github.com/ziishaned/learn-regex/blob/master/img/regexp-en.png))

This pattern matches any text that: is anchored to the start of a line; contains any number of the letters `a-z`, the numbers `0-9`, underscores, and/or hyphens; is 3 to 15 characters long; and is anchored at the end of the line. 
Specifically, this pattern will match the text `john_doe`, `jo-hn_doe` and `john12_as`, but _not_ `Jo` because 1, that string contains an uppercase letter and 2, it's too short.

This is a more complex regular expression, but in this workshop, we'll start with simpler ones and break it down for you step by step.

## Why are regular expressions useful?

Being able to match patterns in text allows you to be more precise with what you're finding and to manipulate text in a more advanced and specific way than using something like the 'find' function. Regular expressions can also be used with programming languages like Python or R, making them even more powerful. For example, you could use regular expressions to pull specific information from a text file and then manipulate it with Python code.



As an aside: wildcards
{: .label .label-green}

A **wildcard** is a special character that represents one or more unknown other characters. It is very common in a wide range of contexts and applications -- particularly when searching through text -- to have one or more wildcards available to expand the range of possible results.

For example, in MS Word, you can use the `?` character to find any single character (including spaces). So, searching for `c?t` would find each of the following results: `cat`, `cot`, `cut`, `c t`. Other wildcard characters match _any number of characters_, _the beginning of a word_, _the end of a word_, and so on.

Often, such wildcards are different in every application (in other words, they are not standardized or "regularized"). This can be confusing if you switch between applications.

Regular expressions, on the other hand, are a standardized set of conventions for finding patterns in strings of text where the definition of each special character typically does not differ between applications and implementations. (Other aspects of regex behaviour may differ between "flavours" of regex, however, but the syntax usually remains the same.)

The _wildcard_ token for matching a single character in regex is `.` (a single dot or period). This is equivalent to `?` in MS Word, while the `?` in regex has a very different usage: it represents _either zero or one instances of the preceding character_. We'll talk about all these special characters (called metacharacters) next.