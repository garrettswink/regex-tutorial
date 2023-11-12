# Regex Tutorial

## Summary
The following document serves as a comprehensive tutorial on regular expressions, with a focus on the email example pattern: /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$. 

Through this tutorial, you will learn the fundamentals of regular expressions, gain a deep understanding of the provided email pattern, and discover how to apply it effectively to validate and extract email addresses in various programming contexts. 

This tutorial will equip you with the knowledge and skills needed to harness the power of regular expressions in your projects.

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
A regular expression (regex) component is a fundamental building block within a regular expression pattern. Each component serves a specific purpose in defining a pattern to match or manipulate text. These components can include literal characters, metacharacters, character classes, quantifiers, anchors, and groups. 

For example, a literal character component represents a specific character to match exactly as it appears, while metacharacters like "*", "+", or "?" modify the behavior of the preceding components. Character classes allow you to match a range of characters, quantifiers specify how many times a component should occur, anchors define where a match should start or end, and groups help organize and capture portions of the matched text. 

Regex components provide a powerful and flexible way to describe patterns for text processing, making them a valuable tool for tasks like searching, validation, and text manipulation in programming and data analysis.

### Anchors
In regular expressions, anchors are special characters that define specific positions within a string where a match must occur. There are two commonly used anchors:

The ^ (caret) anchor signifies the start of a line or string. In the context of the email regex /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/, the ^ anchor is used at the beginning of the pattern to indicate that the match must start at the beginning of the string. This ensures that the email address must start with the local part right from the beginning.

The $ (dollar sign) anchor represents the end of a line or string. In the email regex, it's used at the end of the pattern to indicate that the match must end at the end of the string. This ensures that the email address must conclude with the top-level domain (TLD) and not have any characters after it.

When applied to the email regex, the ^ and $ anchors work together to ensure that the entire string is considered when validating an email address, ensuring that it starts with the local part and ends with the TLD, without any extraneous characters before or after the email address.

### Quantifiers
Quantifiers in regular expressions determine how many times a specific component or group of components should appear in the input text for a successful match. They control the repetition of characters, character classes, or groups. In the email regex example, several quantifiers are used:

+ (plus sign): This quantifier means "one or more." For instance, in ([a-z0-9_\.-]+), it allows for one or more lowercase letters, digits, underscores, periods, or hyphens in the local part of the email address. This ensures that there is at least one character in the local part.

{2,6}: This is a range-based quantifier, specifying the minimum and maximum number of occurrences. In ([a-z\.]{2,6}), it allows for between 2 and 6 lowercase letters or periods in the top-level domain (TLD) part of the email address. This enforces TLDs to have a specific length, such as "com," "org," or "edu," which typically consist of 2 to 6 characters.

Quantifiers, when applied in regular expressions, enable you to define flexible patterns that can accommodate varying numbers of characters, making them a powerful tool for validating and extracting specific information from text, as demonstrated in the email regex.

### OR Operator
The OR operator allows you to specify alternatives for matching a particular part of a pattern. It is represented by the pipe character |. In the context of the email regex, there isn't a direct use of the OR operator (|), but suppose you want to create a regex pattern to match email addresses that end with either ".com" or ".org". You could use the OR operator as follows: /\.com|\.org$/.

Here, \.com and \.org are the alternatives separated by |. This pattern will match strings that end with either ".com" or ".org". So, it provides a choice between two possibilities for the TLD part of the email address, allowing you to match email addresses with different TLDs while still adhering to the rest of the email regex pattern.

### Character Classes
character classes, also known as character sets, allow you to define a group of characters and specify that a match should occur if any one of those characters is found in the input text. Character classes are enclosed within square brackets []. In the email regex, character classes are used in several places:

[a-z0-9_\.-]: This character class specifies a set of characters that are allowed in the local part of the email address. It includes lowercase letters from 'a' to 'z', digits from '0' to '9', underscores '_', periods '.', and hyphens '-'.

[\da-z\.-]: Here, a character class includes digits \d, lowercase letters 'a' to 'z', periods '.', and hyphens '-'. This is also used in the local part of the email address.

[a-z\.]: In this part of the regex, the character class allows lowercase letters 'a' to 'z' and periods '.'. It is used in the TLD part of the email address.

Character classes provide a concise way to define which characters are acceptable at specific positions in the pattern. In the email regex, they help ensure that only valid characters are allowed in the local part, domain part, and TLD of the email address, contributing to the accuracy of email address validation.

### Flags
Flags are modifiers that can be added to the end of a regular expression pattern to alter how the pattern is matched or processed. One common flag is the case-insensitive flag, denoted by "i," which allows the regex to match characters regardless of their case. For example, the regex /example/i with the "i" flag would match "example," "Example," "EXAMPLE," and so on. 

Another useful flag is the global flag, "g," which allows the regex to find all occurrences of the pattern in the input text, not just the first one. Flags provide flexibility and control over how regular expressions are applied, making them a valuable tool for various text processing tasks in programming and data analysis.

### Grouping and Capturing
Grouping and capturing allow you to isolate and extract specific portions of a matched text. Parentheses ( and ) are used to create capture groups within a regex pattern. These groups not only help in organizing complex patterns but also enable you to retrieve and manipulate specific parts of the text that match those groups. For instance, in the email regex /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/, there are three capture groups: one for the local part, one for the domain part, and one for the top-level domain (TLD). When this regex is applied to an email address, it captures each of these components separately, making it easy to access and use them in subsequent code. Grouping and capturing are essential techniques for extracting meaningful information from text and performing actions based on those extracted parts.

### Bracket Expressions
Bracket expressions, also known as character classes, are used to define a set of characters from which a match should be made. They are enclosed within square brackets [ ] and allow you to specify a range of characters or individual characters that you want to match. For example, [aeiou] is a bracket expression that matches any vowel character, and [0-9] matches any digit from 0 to 9. You can also include individual characters or special characters within the brackets, like [abc] to match either 'a,' 'b,' or 'c.' Additionally, you can use negation within a bracket expression by including a caret ^ as the first character, such as [^0-9], which matches any character that is not a digit. Bracket expressions provide a versatile way to define character patterns within regular expressions, making it easier to match specific sets of characters in text.

### Greedy and Lazy Match
The concepts of "greedy" and "lazy" matching refer to how quantifiers like *, +, and ? behave in terms of matching text. These quantifiers control the repetition of the preceding character or group.

By default, quantifiers are greedy, which means they match as much text as possible while still allowing the overall pattern to match. For example, in the regex .*, the * quantifier is greedy, and it will match the longest possible sequence of characters. So, if you apply it to the text "abcdefg", it will match the entire string "abcdefg" in one go.

To make a quantifier lazy, you can add a ? after it. This tells the quantifier to match as little text as possible while still allowing the pattern to match. For example, in the regex .*?, the *? quantifier is lazy, and it will match the shortest possible sequence of characters. So, if you apply it to the same text "abcdefg," it will match each character individually, resulting in multiple matches: "a," "b," "c," "d," "e," "f," and "g."


### Boundaries
In regular expressions, boundaries are used to specify where a match should occur within the input text. They help define the context in which a pattern should be found. There are several types of boundaries:

Word boundaries are denoted by \b. They match the position between a word character (such as a letter or digit) and a non-word character (such as whitespace or punctuation). For example, \bword\b would match the word "word" but not "words" within a text.

Line anchors include ^ and $. The ^ anchor matches the start of a line or string, and $ matches the end of a line or string. These ensure that a match occurs at the beginning or end of a line.

Boundary assertions include (?=...) for positive lookahead and (?<=...) for positive lookbehind. They specify that a pattern should match only if it's followed by or preceded by a certain condition. For example, word(?= boundary) matches "word" only if it's followed by " boundary."

Non-boundary assertions include (?!) for negative lookahead and (?<!...) for negative lookbehind. They specify that a pattern should match only if it's not followed by or not preceded by a certain condition.

Boundaries are useful for precisely controlling where a match should occur within text and are often employed in tasks like finding whole words, validating input format, and extracting data from specific context.

### Back-references
Backreferences are a powerful feature that allows you to refer back to previously captured groups within the same regular expression pattern. They enable you to match a repeated occurrence of the same text that was previously captured by a capturing group.

Backreferences are typically denoted using a backslash followed by a number. The number represents the position of the capturing group you want to refer back to. For example, \1 refers to the first capturing group, \2 refers to the second, and so on.

### Look-ahead and Look-behind
Lookahead and lookbehind assertions, also known as positive and negative assertions, are advanced features in regular expressions that allow you to define conditions for a match without including the matched text itself. These assertions are useful for specifying patterns that depend on the context around a particular substring.

Lookahead and lookbehind assertions add powerful context-based matching capabilities to regular expressions, allowing you to define intricate patterns based on what comes before or after a substring without including those surrounding characters in the match.

## Author
Garrett Swink is a student in the Full Stack Web Development Bootcamp at Columbia University. Visit his Git Repo at: https://github.com/garrettswink

