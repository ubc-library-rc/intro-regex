---
layout: default
title: Introduction
nav_order: 4
---
# Introduction

If you have heard about regular expressions before, you have probably encountered people who praise them as a kind of coding [superpower](https://xkcd.com/208/).

![Regex is a superpower](images/regular_expressions.png)

On the other hand, many people feel very strongly that there are some things (like [parsing HTML](https://stackoverflow.com/a/1732454)) that regular expressions are definitely **not** suited for.

![Don't use regex to parse XHTML](images/html_regex_so_snippet.png)

So, what are regular expressions? What can they be used for? And should you go ahead and use them to parse HTML anyway?

**Regular expressions** (often referred to as **regex** or **regexp**, and abbreviated as **RE**) are a standardized ("regular") way of representing patterns in text using special symbols and syntax ("expressions").

Regexes (sometimes pluralized as "regexen") share some features with the _wildcards_ commonly found in many applications, and may seem to be confusingly similar to the _shell globbing_ used by modern command-line interfaces.

In this workshop, we will first take a look at the similarities and differences between wildcards, shell globbing, and regexes, and then explore the special syntax of common flavours of regex as well as how to use this syntax to find and replace text in a variety of applications (for example, `grep`, `sed`, and `awk`) and programming languages (for example, JavaScript, Ruby, and Python).
