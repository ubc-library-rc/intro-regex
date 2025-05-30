---
layout: default
title: Regex syntax
nav_order: 6
---
# Regex syntax

In this section, we'll cover the basic syntax of regular expressions as well as a few more advanced forms.

## Literal characters

The simplest form a regular expression can take is a plain text string without any special characters. This will match each of the literal characters in the string exactly. For example, `tune` will match a literal t, a literal u, a literal n, and a literal e. When reading regular expressions, it's helpful to read them according to the _meaning_ of each character, not what we usually call the character. `tune` will match:

> **tune**

> at**tune**d

> for**tune**

> inoppor**tune**

Matches are case sensitive by default. For example, the pattern `tune` represents only the first, lowercase, instance of this word in the following string:

> Humming a **tune** as you work can improve your mood. Tune is another word for song.

In other words, the second instance of the word "Tune" will **not** be matched because it is uppercase, and the search pattern was `tune` rather than `Tune`.

If you wanted to find  _both_ `tune` and `Tune`, you could either turn off case sensitive matching (see later in this workshop), or use a different pattern, such as `[Tt]une` to match both capital `T` and lowercase `t` in the text. We'll cover what square brackets mean in a minute.

Any string of letters and/or numbers that doesn't contain metacharacters will be interpreted literally in a regular expression.

## Metacharacters

What are metacharacters, then? They're characters (or **tokens**) that have special meaning when used in regular expressions:

`.` | Period matches any single character, except a line break.
`*` | Matches as many of the preceding token as possible (including 0) (greedy).
`+` | Matches 1 or more repetitions of the preceding token.
`?` | Matches 0 or 1 of the preceding token (makes the preceding token optional).
`[]` | Creates a character class. Matches a single character contained between the square brackets. For example, above, we wrote '[Tt]une' which matches for both 'Tune' and 'tune'.
`[^]` | Creates a negated character class. Matches a single character that is **not** contained between the square brackets.
`[a-z]` | Square brackets can also be used for ranges. This range says match any character in the range 'a-z'. This can also be done with numbers, for example '0-9'.
`[^a-z]`  | Similarly, ranges can be negated as well.
`{x}` | Curly braces. This will match exactly x number of the preceding character. For example 'a{3}' matches exactly 3 of a.
`{x,` | Curly braces. This will match n or more times of the preceding character. For example, 'a{3,}' will match 3 or more times of a.
`{n,m}` | Curly braces. These match at least n but not more than m times of the preceding character. For example, '{1,3}' will match at least 1 time but not more than 3 times.
`(xyz)` | Character group. Matches the characters xyz in that exact order.
`|` | Alternation. Matches either the characters before or the characters after the token (if both are found, both will be matched).
`\` | Escapes the next character. This allows you to make metacharacters become literal characters (for example, '\?' will match a literal question mark).
`^` | Matches the beginning of a line.
`$` | Matches the end of a line.

Metacharacters can be combined, too. For example, '.+' will match any character except a newline, as many times as possible but at least once.

## Shortcuts

There are some regular expressions that are used so frequently that there are shortcuts for them:

`\w` | Shortcut for any word character: any letter, digit, or underscore, '[a-zA-Z0-9_]'.
`\W` | Any non-word character: anything **except** '[a-zA-Z0-9_]'.
`\d` | Any digit: '[0-9]'.
`\D` | Any non-digit: anything **except** '[0-9]'.
`\s` | Any whitespace character: any space, tab, or newline.
`\S` | Any non-whitespace character: anything **except** any space, tab, or newline.
`\n` | Matches a newline.
`\N` | Matches anything but a newline.
`\r` | Matches a carriage return.
`\t` | Matches a tab.

There are additional shortcuts but these are a good place to start. These are useful because they save you time typing out regular expressions that you'll likely use often.

## Lookaheads and lookbehinds

There are many more advanced expressions but here are several that are particularly useful. They're called lookaheads or lookbehinds, and they do what it sounds like - they look ahead of your regular expression, or they look behind it. Here's what they are:
<br>
<br>

`(?=...)` | Positive lookahead. The given pattern can be matched only if the string provided in the positive lookahead is present after the pattern (ahead of the pattern). For example, `cat(?=house)` will match:

> **cat**house

but not

> catastrophe

<br>

`(?!...)` | Negative lookahead. The given pattern can be matched only if the string provided in the negative lookahead is **not** present after the pattern (ahead of the pattern). For example, `cat(?!house)` will match:

> **cat**astrophe

but not

> cathouse

<br>

`(?<=...)` | Positive lookbehind. The given pattern can be matched only if the string provided in the positive lookbehind is present before the pattern (behind the pattern). For example, `(?<=house)cat` will match:

> house**cat**

but not

> alleycat

<br>

`(?<!...)` | Negative lookbehind. The given pattern can be matched only if the string provided in the negative lookbehind is **not** present before the pattern (behind the pattern). For example, `(?<!house)cat` will match:

> alley**cat**

but not

> housecat

<br>

Lookaheads and lookbehinds can be a little confusing to wrap your head around initially, but they are extremely powerful for being able to match strings in specific situations, so they are well worth the effort.