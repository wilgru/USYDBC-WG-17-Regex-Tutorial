# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

The Regex we'll be covering will validate whether or not a piece of text is an email. The regex will look something like this:

bash
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Looks pretty full on, so lets unpack it!

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

So every character in a regex expression represents its literal self, ie. "a" matces the character "a" and "123" matches "123". Now this applies to every characters, except for a special few. 

. - 'wild card'

### Anchors



### Quantifiers

Quantifiers are used to select a certain number of characters, depending on the quantifier. 

\* - zero or more times

\+ - 1 or more times

? - either zero or 1 times

The '+' quantifier is used twice in the email regex, to match at least 1 or more of any characters that are within the character set that preceeds the '+' quantifier. It is basically used to make sure that there is some text in the first capture group for the name, and in the second group for the email provider.

### Grouping Constructs



### Bracket Expressions



### Character Classes

Character classes are basically sets of alike characters (like letters or digits) that we can match an input to more easily. The most commonly used character classes are as follows:

\d - 'digit'
any single number ranging from 0 to 9.

\s - 'space'
mainly white spaces, tabs, newlines and couple other uncommon spacing characters.

\w - 'word'
Any letter found in the Latin alphabet, so basically characters you would find in a word. the \w class also includes digits and underscores.
Note that non-Latin letters (like cyrillic or hindi) do not belong to the \w class.

Using one of the above character classes, we can match against any single character from that set. For example in our email regex, we use a \d to check for one or more digits (amongst other possible characters) dirrectly after the '@' symbol using a character set followed by a quantifier. This is to allow for ann email provider to contain numbers in its name.

Handy note: You can also use each of the above character classes but with a capital letter to match any character that doesnt exists within that character classes set of characters. For example, 'ES6' would match '\D\S\W' and of course you can use both of them together like this '\D\D\d'. 

### The OR Operator

### Flags

### Character Escapes

A character escape basically lets you use any special character that would otherwise be used as a regex compnent as its literall self by appending a forward slash before said character, ie \\. or \\$.

We use this in our email regex when we literally want a period after thhe email provider's name, which otherwise would be interprited as a wild card.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
