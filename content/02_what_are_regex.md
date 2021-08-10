---
layout: default
title: What are regular expressions
nav_order: 5
---
# What regular expressions are (and aren't)

In this section we will explore the similarities and differences between the terms "regular expressions", "wildcards", and "shell globbing", and learn some of the basic syntax of regular expressions.

## Regular expressions

A regular expression is a series of special characters that describe a _pattern_ in a string of text according to a standardized set of rules.

Some regular expressions can be difficult to read at first because every character in the expression has a specific rule-defined meaning. For example, the regular expression below contains letters, numbers, and punctuation to describe a typical username consisting of a specific number of lowercase characters and numbers as well as (optionally) a hyphen or underscore:

![Anatomy of a regular expression](images/regexp-en.png)

(Image from [Learn Regex the Easy Way](https://github.com/ziishaned/learn-regex/blob/master/img/regexp-en.png))

Specifically, this pattern will match the text `john_doe`, `jo-hn_doe` and `john12_as`, but _not_ `Jo` because that string contains an uppercase letter (and is also too short).


## Wildcards

A **wildcard** is a special character that represents one or more unknown other characters. It is very common in a wide range of contexts and applications -- particularly when searching through text -- to have one or more wildcards available to expand the range of possible results.

For example, in MS Word, you can use the `?` character to find any single character (including spaces). So, searching for `c?t` would find each of the following results: `cat`, `cot`, `cut`, `c t`. Other wildcard characters match _any number of characters_, _the beginning of a word_, _the end of a word_, and so on.

Often, such wildcards are different in every application (in other words, they are not standardized or "regularized"). This can be confusing if you switch between applications.

Regular expressions, on the other hand, are a standardized set of conventions for finding patterns in strings of text where the definition of each special character typically does not differ between applications and implementations. (Other aspects of regex behaviour may differ between "flavours" of regex, however, but the syntax usually remains the same.)

The _wildcard_ symbol for matching a single character in regex is `.` (a single dot or period). This is equivalent to `?` in MS Word, while the `?` in regex has a very different usage: it represents _either zero or one instances of the preceding character_.

## Shell globbing

If you use the UNIX command-line (or _shell_), it is important to note that the shell itself is not capable of interpreting regular expressions. Instead, separate shell programs, for example, `grep`, `sed`, or `awk`, are used to parse regex.

This is an important distinction to make, because the shell has a feature called **filename expansion** or **shell globbing** that in some ways can look very similar. For example, the wildcard for matching _any number of characters_ or _all files in the directory_ in a shell context is `*`:

```bash
ls * # list all files in directory and subdirectories
ls *.txt # list all files in the directory with the extension .txt
ls test.* # list any file named "test", e.g.: test.txt, test.doc, test.png, etc
ls t*.* # list all files beginning with "t", with any extension
```

This is different from the way that the `*` character is used in regex, where it means _zero or more instances of the previous character_.

Another similar-but-different feature of shell globbing and regex is the ability to define a range or class of characters using square brackets. For example, `[a-z]` means all lowercase letters from `a` to `z`, and `[0-9]` means all numbers from 0 to 9. So if you have a group of files in a directory with filenames `test1.txt`, `test2.txt`, `test3.txt`, `test4.txt` and so on, you could list them all with the following command:

```bash
ls test[0-9].txt
```

Square brackets operate in a very similar way in regular expressions, however combining them with other shell globbing characters can lead to unexpected results. For example, the following command lists all files with the extension `.md` in a directory whose filenames begin with any letter between `a` and `l`:

```bash
ls -l [a-l]*.md
```

This is because the shell expands the expression `[a-l]` as any character between `a` and `l`, and then expands `*` to any sequence of characters following that initial letter, followed by the literal string `.md` (the file extension). If `[a-l]*.md` were interpreted as a regular expression, however, it would match _zero or more instances_ (`*`) of a character between `a` and `l` (`[a-l]`), followed by _any single character_ (`.`) and finally the literal string `md`.

In order to make sure that regexes you are providing to a program like `grep` on the command-line are not accidentally expanded by the shell, it is always a good idea to _escape_ any regex you are using by surrounding it in quotation marks.
