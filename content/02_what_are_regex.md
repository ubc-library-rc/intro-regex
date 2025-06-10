---
layout: default
title: What are regular expressions?
nav_order: 5
---
# What are regular expressions?

Imagine you're helping organize a community event and you’ve got a big text document full of messages from volunteers. Everyone sent their phone numbers in different formats:

> Call me at 555-123-4567
> 
> My number is (555) 123 4567
>
> 5551234567
>
> 555.123.4567

You need to pull just the phone numbers from this mess, but ideally without spending hours scrolling and copying by hand. The usual 'find' tool won't work here, so what do you do? Enter regular expressions!

## Regular expressions

A regular expression (regex for short) is a series of characters that describe a _pattern_ in a string of text according to a standardized set of rules. This pattern gets compared to the string and either it matches or doesn't - it's kind of like the 'find' function but with superpowers. You may be familiar with the concept of a wildcard character. For example, in Microsoft Word, the `?` character allows you to search for 'any character'. So, searching for `c?t` would find each of the following results: `cat`, `cot`, `cut`, `c t`. 

Regular expressions are similar to this, but it's a much expanded and more powerful system. Regular expressions are also more or less standardized across programs (with some dialectal variations depending on context), whereas wildcards are usually program specific and therefore less useful.

## Why are regular expressions useful?

Being able to match patterns in text allows you to be precise with what you're finding and and it also allowed you to manipulate text in a more advanced and specific way than using something like the 'find' function. Regular expressions can also be used with programming languages like Python or R, making them even more powerful. For example, you could use regular expressions to pull specific information from a text file and then manipulate it with Python code. After learning regular expressions, it's likely you'll find yourself in many situations where they can be used to save time, where you might not have expected it!

## Testing regular expressions

Before we continue, there is a resource you should pull up on your computer browser to follow along as we go.

[regex101](https://regex101.com/) is free online tool for learning, building, and testing regular expressions. You can write your regular expression and write or paste in test strings or longer text to see the matches that you will get. There are many tools like this out there, but this is the one we usually use at Digital Scholarship at the Library. We'll be linking to examples on this website a couple times throughout this workshop so this is your introduction to it!
