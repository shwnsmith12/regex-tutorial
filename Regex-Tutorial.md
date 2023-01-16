# Regex Tutorial

AS A web development student

I WANT to develop a tutorial explaining the specifics of Regex (Regular Expressions)

SO THAT someone can use this to gain a cursory understanding of the search patterns that Regex defines

## Summary

A Regex (or regular expression) is a sequence of characters that help us define a search pattern. These patterns use string-searching algorithms for "find" or "find and replace" operations on string inputs. It can also looks for input validations, and is a technique commonly developed in theoretical computer science.

Example: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

Please read below to learn how to decipher this code, and others like it!

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [OR Operator](#or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Author](#author)

## Regex Components

### Anchors

* `^abc$`: 
    * `^` Matches the beginning of the string - it matches the position, however, and not the character 
        * (Note: the (m) flag can be enabled to flag multiple lines)
    * `$` Matches the end of the string - it matches the position, however, and not the character
        * (Note: the (m) flag can be enabled to flag multiple lines)

* `\b\B`:
    * `\b` Matches a word boundary position between a word character and non-word character or position (start / end of string). See the word [Character Classes](#character-classes) (w) for more info
    * `\B` Matches any position that is not a word boundary - it matches the position, however, and not the character 
        * See [Boundaries](#boundaries) for more detailed information

### Quantifiers

Quantifiers are used to make a determination of how many times specific characters, or group of characters, must be present in order to match.

For example, if we used the following code in our Regex "sto+" then this will match any string "st" followed by at least one "o". Using the example code below will match any string that contains "a-z", "0-9", "_", ".", or "-" (like: 'stop' or 'stoop').

The "+" quantifier makes it so that the string must contain at least one of these in order to have a match:

`([a-z0-9_\.-]+)`

### Grouping Constructs

* `(ABC)` - Captures multiple tokens together, and creates a capture group for extracting a substring or using a back-reference
* `(?<name>ABC)` - Name capturing group captures groups of a specific name
* `\1` - Captures groups with a numeric reference
* `(?:ABC)` - Groups multiple tokens together without creating a capture group

### Bracket Expressions

The bracket expression, `[ ]`, is a Regex that matches a single character or collating element. If the initial character is a circumflex `^`, then this bracket expression is complemented.

See [Character Classes](#character-classes) to see some examples.

### Character Classes

Character classes match a character from a specific set, and there are many predefined character classes that can be used to define sets.

* `[ABC]` - Characters inside brackets `[ ]` will match ANY character in the set
* `[^ABC]` - Inside `[ ]`, the caret `^` will match ANY character that is NOT in the set
* `[A-Z]` - Inside `[ ]`, the dash `-` between two characters creates a range
* `.` - Matches ANY character, except for line breaks
* `[\s\S]` - Matches ANY character, including line breaks, without the DOTALL flag
    * Note: The `[^]` carrot in brackets can also work, but isn't supported in all web browsers
* `\w` - Matches ANY word character (alphanumeric & underscore). Only matches low-ascii characters (no accented or non-roman characters)
* `\W` - Matches ANY character that is NOT a word character (alphanumeric & underscore)
* `\d` - Matches ANY digit character (0-9)
* `\p` - Matches a character in the specified unicode category

### OR Operator

The OR Operator `|` Acts like the boolean "OR". It will match the expression before or after the `|`.

Example: `/^#?([a-f0-9]{5}|[a-f0-9]{2})$/`

The OR Operator indicates that it could search either of the components that we are separating with the `|`. From our example above we have `([a-f0-9]{5}|[a-f0-9]{2})`. This would mean that our hex value could either be 5 characters `[a-f0-9]{5}` or 2 characters `[a-f0-9]{2}`.

### Flags

Expression flags change how the expression is interpreted. Flags follow the closing `/` of the expression.

* `g` - Global Search. They retain the index of the last match, and allow subsequent searches to start from the END of the previous match.
    * Note: Without the global flag `g`, all subsequent searches will return the SAME match
* `m` - Multiline Flag. If a multiline flag `m` is enabled, the beginning and end anchors `^` and `$` will match the start AND end of a LINE, instead of the start AND end of the whole STRING.
* `y` - The `y` expression will only match from its lastIndex position. It also ignores the global `g` flag if has been set.   
    * - Note: Because searches in Regex are discrete, this flag has no further impact on the displayed result
* `i` - Ignores case sensitivity
* `s` - Dot `.` will match ANY character, including new line.
  
### Character Escapes

Backslash `\` is the "Escape Character" in Regex. Escaping a character will prevent it from being interpreted as a literal character.

Using the blow example, the `\.` is called in several places. Using the `\` will find JUST the dot.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Author

Shawn Smith
My Github [github] https://github.com/shwnsmith12