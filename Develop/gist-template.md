# Title (replace with your title)

As a web development student, I have developed a tutorial explaining a specifics of regex so that we can understand the search pattern the regex defines

## Summary

A Regex or regular expression is a sequence of characters that define a search pattern. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings. It also looks for input validations. It is a technique commonly developed in theoretical computer science.

We will look a a string of code using regex, this code looks for a match HTML tag.

Example: /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/

The below content will explain what each section of this code does and more.

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
- abc$ -^start / $end of the string

-^ Matches the beginning of the string, or the beginning of a line if the multiline flag (m) is enabled.This matches a position, not a character.
-$ Matches the end of the string, or the end of a line if the multiline flag (m) is enabled. This matches a position, not a character.
\b\B -word, not-word boundary

\b Matches a word boundary position between a word character and non-word character or position (start / end of string). See the word character class (w) for more info.
\B Matches any position that is not a word boundary. This matches a position, not a character.
See Boundaries for more detailed Information

### Quantifiers
Quantifiers indicate that the preceding token must be matched a certain number of times. A quantifire can be greedy or lazy that is explained below.

a*a+a? -0 or more, 1 or more, 0 or 1

"+" Matches 1 or more of the preceding token.
"*" Matches 0 or more of the preceding token.
"?" Matches 0 or 1 of the preceding token, effectively making it optional.
"?" Makes the preceding quantifier lazy, causing it to match as few characters as possible. By default, quantifiers are greedy, and will match as many characters as possible.
a{5}a{2,} -Looks for exactly five, two or more

{2,6} -forces the input of characters between two & six characters long.

a+?a{2,}? -match as few as possible

ab|cd -match ab or cd

### OR Operator
| Acts like a boolean OR. Matches the expression before or after the |. It can operate within a group, or on a whole expression. The patterns will be tested in order. Just as in java will match either set of characters. It will look for this OR that.

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
