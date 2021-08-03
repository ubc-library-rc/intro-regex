---
layout: default
title: Basic syntax
nav_order: 6
---
# Basic syntax

The simplest form a regular expression can take is a plain text string without any special characters. This will match each of the literal characters in the string exactly. Matches are case sensitive by default. For example, the pattern `regular` represents only the second (lowercase) instance of this word in the following string:

> Regular expressions are a standardized (regular) way of representing patterns in text using special symbols and syntax.

In other words, the first word of the sentence (`Regular`) will **not** be matched because it is uppercase, and the search pattern was `regular` rather than `Regular`.

If you wanted to find  _both_ `regular` and `Regular`, you could either turn off case sensitive matching (see later in this workshop), or use a different pattern, such as `[Rr]egular` to match both capital `R` and lowercase `r` in the text.

Any string that does not contain the reserved characters (i.e., `[ ] ( ) { } . * + ? ^ $ \ |`) will be interpreted literally in a regular expression.

## Special characters

The following characters (or **tokens**) have special meaning in regular expressions:

`.` | Period matches any single character except a line break.
`[]` | Character class. Matches any character contained between the square brackets.
`[^]` | Negated character class. Matches any character that is not contained between the square brackets
`*` | Matches 0 or more repetitions of the preceding symbol.
`+` | Matches 1 or more repetitions of the preceding symbol.
`?` | Makes the preceding symbol optional.
`{n,m}` | Braces. Matches at least "n" but not more than "m" repetitions of the preceding symbol.
`(xyz)` | Character group. Matches the characters xyz in that exact order.
`|` | Alternation. Matches either the characters before or the characters after the symbol.
`\` | Escapes the next character. This allows you to match reserved characters `[ ] ( ) { } . * + ? ^ $ \ |`
`^` | Matches the beginning of the input.
`$` | Matches the end of the input.
