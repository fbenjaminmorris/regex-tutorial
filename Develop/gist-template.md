# Matching Email Regulas Expression

In this tutorial, I'm going to introduce one of the more commonly used Regular Expressions and, by describing how it works, explain some important regex concepts.

## Summary

We will be walking through the following regex, explaining what each component does.

/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

This regex makes sure that the given string matches the template for an email address.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
The two anchors in regex are ^ and $.

^ means that the following code must appear at the beginning of the string.

$ means that the preceding code must appear at the end of the string.

Because our regular expression contains both, a given string must match all the given specifications exactly, or it won't be a match.

Although this sounds limiting, you will see how quantifiers, grouping and bracket expressions allow a large range of variation in the given string.

### Quantifiers
Quantifiers are used to specify how many times a given character is expected to appear.

Our regex uses two quantifiers, + and {2,6}.

In our expression, [a-z0-9_.-]+ means that any character matching the characters inside the brackets is expected to appear at least once, with no upper limit.

The same is true of [\da-z.-]+

[a-z.]{2,6} means that 2 to 6 characters matching those inside the brackets are expected. The numbers inside the curly braces specify the lower and upper limit of the number of characters expected.

### OR Operator
- | Acts like a boolean OR. Matches the expression before or after the |. It can operate within a group, or on a whole     expression. The patterns will be tested in order. Just as in java will match either set of characters. It will look for this OR that.

### Character Classes
Regex has special character classes that match types of characters.

In our expression, \d is used to match any digit character.

The backslash is necessary in order to differentiate the digit class from a plain letter d.

Although we only have one character class in the expression, the behavior-changing function of a backslash is helpful in understanding another frequently used part of the expression, ".".

Unlike the other character classes, \d, \w (matching a word character) and \s (matching a whitespace character), the character class ".", which matches any character, does not require a backslash.

Because of the unique behavior of ".", the backslash must be used to negate its use as a character class and interpret it as the character ".".

### Flags
Flags will always follow the closing forward slash of an expression, and change how it is interpreted.

There are no flags in our example; however, the following are some examples:

Ignore case i will make the entire expression case-sensitive.
Global search g will store the index of the last match.
Multiline m will cause the beginning and end anchors to match the start and end of a line instead of the whole string.
Unicode u allows extended unicode escapes in the form \x{FFFFF}.
Sticky y will only match from its last index position and ignores the global search flag.
Dotall s causes dot (.) to match any character.

### Grouping and Capturing
Grouping and capturing is done with ( ) in regex.

Anything within a set of parentheses is taken as a single group, which allows all the information inside to be treated as a single unit.

Look at the entire expression, paying special attention to the parentheses.

/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/

Between /^ and $/, there are three distinct character groups, ([a-z0-9_.-]+), ([\da-z.-]+), and ([a-z.]{2,6}).

If we remove the internal logic, the regex can be expressed this way: (1)@(2).(3). This is much easier to read, and corresponds to what we know about email addresses, which always follow the (string)@(website).(com/edu/etc) template.

### Bracket Expressions
The final piece necessary to our RegEx is bracket expressions. There are three within our code:

[a-z0-9_.-], [\da-z.-], and [a-z.]

A bracket expression represents a single character. The character can be anything specified within the brackets. So, for example, in [a-z0-9_.-], this character will be matched by any lowercase letters from a-z, any digit from 0-9, or a period.

Combined with the quantifier +, this piece of code means that any number of characters matching those specified within the brackets will match.

### Greedy and Lazy Match
- ### Greedy:
    A greedy quantifier always attempts to repeat the sub-pattern as many times as possible before exploring shorter matches by backtracking.

Generally, a greedy pattern will match the longest possible string.

By default, all quantifiers are greedy.

- ### Lazy:
    A lazy (also called non-greedy or reluctant) quantifier always attempts to repeat the sub-pattern as few times as possible, before exploring longer matches by expansion.

Generally, a lazy pattern will match the shortest possible string.

To make quantifiers lazy, just append ? to the existing quantifier, e.g. +?, {0,5}?.

### Boundaries
The metacharacter \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.

There are three different positions that qualify as word boundaries:

- Before the first character in the string, if the first character is a word character.
- After the last character in the string, if the last character is a word character.
- Between two characters in the string, where one is a word character and the other is not a word character.
Simply put: \b allows you to perform a “whole words only” search using a regular expression in the form of \bword\b. A “word character” is a character that can be used to form words. All characters that are not “word characters” are “non-word characters”.

### Back-references
Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag. Here’s how: <([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1>. This regex contains only one pair of parentheses, which capture the string matched by [A-Z][A-Z0-9]*. This is the opening HTML tag. (Since HTML tags are case insensitive, this regex requires case insensitive matching.) The backreference \1 (backslash one) references the first capturing group. \1 matches the exact same text that was matched by the first capturing group. The / before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match

### Look-ahead and Look-behind
Lookahead and lookbehind, collectively called “lookaround”, are zero-length assertions just like the start and end of line, and start and end of word anchors explained earlier in this tutorial. The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match. That is why they are called “assertions”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

Our example does not contain lookarounds; however, the following are some examples.

- A positive lookahead, (?=ABC), will match a group after the pattern without including it in the result.
- A negative lookahead, (?!ABC), will specify a group that cannot match after the pattern; otherwise, the result is   unsuccessful.
- A positive lookbehind, (?<=ABC), will match a group before the pattern without including it in the result.
- A negative lookbehind, (?<!ABC), will specify a group that cannot match before the pattern; otherwise, the result is unsuccessful.

## Author

My name is Frank B Morris and I am trying to make sure I pass my class.

Here is my github repository: https://github.com/fbenjaminmorris
