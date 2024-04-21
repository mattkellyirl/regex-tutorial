# Understanding Regular Expressions/Regex - Validating an Email Address

Regular expressions, commonly abbreviated as regex, are a powerful tool used to identify, validate and extract patterns in text. Regex can be used as an advanced search tool, allowing extraction of specific data from large bodies of text. In web development, regex is widely utilised to validate user input data such as email addresses, credit card information and phone numbers. This eliminates the risk of users sending invalid data and therefore vastly improving the integrity of server-side databases. Regex is supported by many programming languages, such as Java, Python, C# and what we will be discussing in this tutorial, Javascript.

## Summary

The following is the regex used to validate an email address:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

No, that's not an unfortunately long typo! That's the regular expression used to identify an email address. Let's break down how it works.

## Table of Contents

- [Anchors](#anchors)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions / Character Classes](#bracket-expressions--character-classes)
- [Quantifiers](#quantifiers)

## Regex Components

The above regex consists of several components, each serving a specific purpose in defining a pattern.

`/` In JavaScript, the forward slash at the beginning and end of the regex define the entire regex literal. It is similar to how strings are enclosed within double " " or single ' ' quotes.

### Anchors

`^` The caret, when used at the start of the regex (outside of the square brackets '[ ]') acts as an anchor to define the starting position of the string. It specifies that the string must match the characters that follow in the pattern. For example, the regex `^hello`, only matches text that includes "hello" at the start of a string.

### Grouping Constructs

In this regex, there are 3 groups: `([a-z0-9_\.-]+)` + `([\da-z\.-]+)` + `([a-z\.]{2,6})`

- These groups are defined by parentheses '( )' at the beginning and end of each group. Grouping constructs are useful to help organise specific parts of the regex, allowing manipulation of specific parts of data (eg. extracting or changing a specific piece of text, like the domain name from an email, or part of a phone number).

### Bracket Expressions / Character Classes

Bracket expressions contain character classes, which are how we define the sets of characters we want to match in the regular expression.

In this bracket expression: `[a-z0-9_\.-]`

- The `a-z` character class is used, which matches any lowercase character from 'a' to 'z'.
- Similarly, the `0-9` character class matches any digit from '0' to '9'.
- Both the hyphen `-`, and underscore `_` characters match themselves.
- The trickiest part of this bracket expression to understand is the forward slash and dot `\.`. When used by itself, the dot `.` is referred to as a 'metacharacter' or 'wildcard' character, which matches any character except for a newline character `\n`. However, when preceded with a forward slash, the dot is escaped (this is referred to as a character escape), therefore ensuring the regex engine specifically matches only a literal dot `.` character.

In this bracket expression: `[\da-z\.-]`

- The `\d` character class is used, which matches any digit from '0' to '9'. `\d` is the preferred and shorthand way to write the `0-9` class. Both `\d` and `0-9` classes match the same digits, including unicode digits. Unicode digits are numeric characters written in other scripts, such as Arabic, Devanagari and Bengali. It is not common to see both `\d` and `0-9` classes used within the same expression; however it has been used in this regex example.
- `a-z` matches any lowercase character from 'a' to 'z'.
- `\.` matches only the dot character, and the hyphen `-` matches itself.

In this bracket expression: `[a-z\.]`

- `a-z` matches any lowercase character from 'a' to 'z'.
- `\.` matches only the dot character.

### Quantifiers

Quantifers are used to define how many times a character or group of characters can occur in the text pattern.

In this regex, there are 2 quantifiers: `+` and `{2,6}`

The `+` quantifier is used outside of the first 2 bracket expressions, meaning that any of those characters inside the expressions can occur one or more times.

`{2,6}` is used at the end of the last bracket expression, defining that the characters inside of that expression can occur between 2 and 6 times. The purpose of this quantifier is to ensure that the TLD (Top Level Domain) of the email address is between 2 and 6 characters long, meaning that shorter domain names like .com, .co, .net and longer domain names such as .info, .media and .travel are accepted.

## Author

Matt Kelly is Full Stack Developer, studying at The University of Adelaide.  
GitHub: [mattkellyirl](https://github.com/mattkellyirl)  
Email: mattkellyvisual@gmail.com
