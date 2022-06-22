# WG's Regex Tutorial: Email

In this tutorial we’ll be looking at another real-world application for regexes, using a complex combination of components to build the expression that we’ll be covering.

## Summary

The Regex we'll be covering will validate whether or not a piece of text is an email. The regex will look something like this:

```regex
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

Looks pretty full on, so let's unpack it!

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Capture Groups](#capture-groups)
- [ Character Sets](#character-sets)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)


## Regex Components

Every character in a regex expression represents its literal self, ie. "a'' matches the character "a" and "123" matches "123". Now this applies to every character, except for a special few. Let's explore them here.

## Anchors

Anchors are used to determine if an input text starts with a character, ends with a character, or can be used together to determine if the text is something from start to end. 

```regex
^a
```
determines if the text starts with a character. In this case it would start with an 'a'.

```regex
ing$ 
```
determines if the text ends with a character. In this case it would start with an 'ing'.

```regex
^hello$ 
```
determines if the text matches what sits within the \^ and \$. Here the whole string would have to match 'hello' from start to end.

We use the two anchors together in our email Regex to make sure the input is nothing more than what we defined. For example if our input was ‘email me at: John.doe@gmail.com’. This would not work because we want to see if the input starts with /^([a-z0-9_-]+), which ‘email me at:’ does not match (mainly because of the spaces). If we had removed the anchors from our regex though, this example input would work. 

In essence, using both anchors is like saying ‘don’t match any substring within the input text. The whole input must match the regex from start to end’.


## Quantifiers

Quantifiers are used to select a certain number of characters, depending on the quantifier. 

```regex
a*
```
zero or more times. Would match 'aaa' or ''.

```regex
b+
```
1 or more times. Matches 'b' or 'b'.

```regex
c? 
```
either zero or 1 times. Matches '' or 'c'

```regex
{4} 
```
must match exactly the number of times that is listed within these curly braces. In this case it must occur 4 times.

```regex
{2,6} {6,} 
```
(used within {}) use between 2 numbers to match any number of occurrences between those two numbers or use it after a number to match that number of times or more.

The '+' quantifier is used twice in the email regex, to match at least 1 or more of any characters that are within the character set that precedes the '+' quantifier. It is basically used to make sure that there is some text in the first capture group for the name, and in the second group for the email provider.

We also use the curly braces at the end of our email regex, to check whether the email has a top level domain name that is between 2 and 6 letters in length.


## Capture Groups

Capture groups can be used to group multiple regex components together that can then be treated like one component. 

```regex
()
```
define a capture group.

```regex
(?:) 
```
define a non-capture group.

We use these capture groups a couple times in our email regex to group together main sections of our regex. The part before the '@', and sections before and after the period.


## Character Sets

A character set allows us to define a set of characters or character classes, of which an input text would be allowed to match any of. 

```regex
[a-z0-9]
```
Match anything inside the brackets.

```regex
[^A-D3-6]
```
Don't match anything inside the brackets.

We use character sets quite a bit on our email regex. FOr example, we check for a name (or just anything before the '@' in the email address) using [a-z0-9_\.-] inn the first capture group. This character set will match anything that is a letter between a-z or a digit between 0-9 or a '.' period (using the escape character '\\') or a dash.


## Character Classes

Character classes are basically sets of alike characters (like letters or digits) that we can match an input to more easily.

```regex
\d
```
'digit' - any single number ranging from 0 to 9.

```regex
\s
```
'space' - mainly white spaces, tabs, newlines and a couple other uncommon spacing characters.

```regex
\w 
```
'word' - Any letter found in the Latin alphabet, so basically characters you would find in a word. the \w class also includes digits and underscores.
<sub><i>Note that non-Latin letters (like cyrillic or hindi) do not belong to the \w class.</i></sub>

Using one of the above character classes, we can match against any single character from that set. For example in our email regex, we use a \d to check for one or more digits (amongst other possible characters) directly after the '@' symbol using a character set followed by a quantifier. This is to allow for an email provider to contain numbers in its name.

<sub><i>Handy note: You can also use each of the above character classes but with a capital letter to match any character that does not exist within that character classes set of characters. For example, 'ES6' would match '\D\S\W' and of course you can use both kinds of classes together like this '\D\D\d'.</i></sub>


## Character Escapes

A character escape basically lets you use any special character that would otherwise be used as a regex component as its literal self by appending a forward slash before said character, like '\\.' or '\\$'.

```regex
\$
```
character escape. In this instance, we will get the literal character '$'.

We use this in our email regex when we literally want a period after the email provider's name, which otherwise would be interpreted as a wild card.


## Author

Written by William G
GitHub: https://github.com/wilgru