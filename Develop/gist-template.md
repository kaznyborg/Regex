# Regex  Cheat Sheet

## Summary

Regular expressions, or regex, is used to find patterns in text. The most common uses are for validating text and to search through text. 

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
    they match a position before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret ^ matches the position before the first character in the string. Applying ^a to abc matches a. ^b does not match abc at all, because the b cannot be matched right after the start of the string, matched by ^. See below for the inside view of the regex engine.

### Quantifiers
    Quantifiers defin quantities
        "+" Matches any string that contains at least one 
        "*" matches any string that contains zero or more occurrences of
        "?" Matches any string that contains zero or one occurrences of

### OR Operator
    |  is used as an OR character. and example is abc|xyz = abc OR xyz

### Character Classes
    You can tell the regex engine to match only one out of several characters. Simply place the characters you want to match between square brackets. If you want to match an a or an e, use [ae]. You could use this in gr[ae]y to match either gray or grey. Very useful if you do not know whether the document you are searching through is written in American or British English.

### Flags
    Regular expressions have optional flags that allow for functionality like global searching and case-insensitive searching. These flags can be used separately or together in any order, and are included as part of the regular expression.
        "d" Generate indices for substring matches
        "g" Global Search
        "i" Case-insensitive search
        "m" Allows ^ and $ to match newline characters
        "s" Allows . to match newline characters
        "u" "Unicode"; treat a pattern as a sequence of Unicode code points
        "y" Perform a "sticky" search that matches starting at the current position in the target string

### Grouping and Capturing
    Capturing groups are a way to treat multiple characters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses. For example, the regular expression (dog) creates a single group containing the letters "d" "o" and "g" .

### Bracket Expressions
    Brackets are used to find a range of characters
        [] Find any character between the brackets
        [^] Find any character Not between the brackets
        [0-9] Find any character between the brackets (any digit)
        [^0-9] Find any character Not between the brackets (any non-digit)
        (x|y) Find any of the alternatives specified

### Greedy and Lazy Match
    Greedy search: to find a match, the regular expression engine uses the following algorithm:
        For every position int he string
            try to match the pattern at that position
            if there is no match, go to the next position
        In the greedy mode (by default) a quantified character is repeated as many times as possible.

    Lazy search: The lazy mode of quantifiers is an opposite to the greedy mode. It means: “repeat minimal number of times”.
    We can enable it by putting a question mark '?' after the quantifier, so that it becomes *? or +? or even ?? for '?'.
    To make things clear: usually a question mark ? is a quantifier by itself (zero or one), but if added after another quantifier (or even itself) it gets another meaning – it switches the matching mode from greedy to lazy.

### Boundaries
    The metacharacter \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.
    There are three different positions that qualify as word boundaries:
        Before the first character in the string, if the first character is a word character.
        After the last character in the string, if the last character is a word character.
        Between two characters in the string, where one is a word character and the other is not a word character.

### Back-references
    Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag. Here’s how: <([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1>. This regex contains only one pair of parentheses, which capture the string matched by [A-Z][A-Z0-9]*. This is the opening HTML tag. (Since HTML tags are case insensitive, this regex requires case insensitive matching.) The backreference \1 (backslash one) references the first capturing group. \1 matches the exact same text that was matched by the first capturing group. The / before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.

### Look-ahead and Look-behind
    Lookahead  
        (?=foo)
            Asserts that what immediately follows the current position in the string is foo
    Lookbehind
        (?<=foo)
            	Asserts that what immediately precedes the current position in the string is foo
    Negative Lookahead
        (?!foo)
            Asserts that what immediately follows the current position in the string is not foo
    Negative Lookbehind
        (?<!foo)
            Asserts that what immediately precedes the current position in the string is not foo

## Author

Kaz Nyborg-Andersen https://github.com/kaznyborg