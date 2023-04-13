# Tutorial For Understanding Regular Expressions

In this tutorial, you will learn what regular expressions are and how to use them. We will also break down the different components of the regular expression and explain what they do.

## Summary

We will be looking at the following regex expression: `^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`. This regex expression is used to validate email addresses. A regex is a particular text string for describing a search pattern. You can think of regular expressions as wildcards on steroids. You are probably familiar with wildcard notations such as `*.txt` to find all text files in a file manager. The regex equivalent is `.*.txt`. Regexes can be used to search, edit, and manipulate text and data. Each unique component of the regex is responsible for a specific task.

## Table of Contents

- [Regex Components](#regex-components)
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

## `^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`

## Regex Components

A regex component is like a building block, there are several building blocks that come together to form a building. Each component is responsible for a specific task. For example, within our example for matching email adresses, the `^` symbol indicates the beginning of the line, so the pattern starts matching from the beginning of the string. The `$` symbol indicates the end of the line, so the pattern stops matching at the end of the string like the last building block. The `+` symbol indicates that the previous item is matched one or more times. If we continue to use the idea of building blocks, the `+` symbol is like a roof on top of the building block. The `.` symbol matches any character except a newline, like a wall around the building block. The `[]` symbol is used to indicate a set of characters, think of a boundary set when building using the building blocks. The `()` symbol is used to group subpatterns, think of a frame around the building block. The `{}` symbol is used to indicate the number of repetitions of a character, group, or character class between two numbers like a door on the building. The `|` symbol is used to separate alternatives, think of a window on the building block... these components keep on going to fit any or most situations not just email addresses. We will go over each component in detail below.

### Anchors

- Focusing on anchors, their role is to perform a match at the beginning or end of a string. The `^` symbol is used to match the beginning of a string. In our example, `^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`, we see the `^` symbol at the beginning of the regex expression. This symbol indicates where to start matching the pattern. Another anchor we see is the `$` symbol. This symbol indicates where to stop matching the pattern. In our example, we see the `$` symbol at the end of the regex expression. Like a stop sign, the `$` symbol indicates where to stop matching the pattern and like a green light, the `^` symbol indicates where to start matching the pattern.

### Quantifiers

- Moving on to quantifiers, their role is to specify the number of times a character, group, or character class should be matched. The `+` symbol is used to match one or more times. In our example, we see the `+` symbol after the `@` symbol. This symbol indicates that the previous item is matched one or more times. The `*` symbol is used to match zero or more times. In our example, we see the `*` symbol after the `.` symbol. This symbol indicates that the previous item is matched zero or more times. The `?` symbol is used to match zero or one time. In our example, we see the `?` symbol after the `.` symbol. This symbol indicates that the previous item is matched zero or one time. The `{}` symbol is used to match a specific number of times. In our example, we see the `{}` symbol after the `.` symbol. If we bring these together, we see that the previous item is matched between two numbers of times. The `{2,6}` symbol indicates that the previous item is matched between two and six times. The `{2}` symbol indicates that the previous item is matched two times. The `{2,}` symbol indicates that the previous item is matched two or more times. The `{,6}` symbol indicates that the previous item is matched up to six times. In this case, an email address has a minimum of two characters and a maximum of six characters.

### OR Operator

- The OR operator can be simplified as an "or" statement. The `|` symbol is used to separate alternatives, like this: `/(cat|dog)/`. This regex expression will match either `cat` or `dog`. In our example, we do not have separate alternatives since we are only matching email addresses. However, we do have a `.` symbol which matches any character except a newline, but this is besides the point. Usually in most cases, email validations do have OR operators. For example, `^([a-z0-9_\.-]+)@(gmail|yahoo|hotmail)\.([a-z\.]{2,6})$`. This regex expression will match either `gmail`, `yahoo`, or `hotmail` after the `@` symbol. This is a very common use case for the OR operator.

### Character Classes

- The character class is a set of characters inside square brackets. Think of a boundary set for the validation to take place. In our example,`^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$`, we see the `[]` symbol after the `@` symbol.
- `[a-z0-9_\.-]`: This character class matches any lowercase letter, digit, underscore, dot, or hyphen. It allows for one character from this set to occur one or more times consecutively. This is used to define the username part of the email address, which can consist of lowercase letters, digits, underscores, dots, or hyphens.
- `[\da-z\.-]`: This character class matches any digit, lowercase letter, dot, or hyphen. It allows for one character from this set to occur one or more times consecutively. This is used to define the domain name part of the email address, which can consist of digits, lowercase letters, dots, or hyphens.
- `[a-z\.]`: This character class matches any lowercase letter or dot. It allows for one character from this set to occur between two and six times consecutively. This is used to define the top-level domain part of the email address, which can consist of lowercase letters or dots.

### Flags

- In general, flags are used to modify the behavior of a regex expression. In our example, we do not have any flags. However, there are several flags that can be used to modify the behavior of a regex expression. The `g` flag is used to perform a global match, which will return all matches in the string instead of stopping after the first match. The `i` flag is used to perform a case-insensitive match. The `m` flag is used to perform multiline matching. Flags are optional parameters that can be added to the end of a regular expression pattern to modify its behavior. For example, `/pattern/flags`. Flags can be added to the end of a regex expression like this: `^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$g`. This regex expression will match all email addresses in the string instead of stopping after the first match.

### Grouping and Capturing

- Grouping and capturing are techniques used to enclose a part of a pattern in parentheses to capture and extract that portion of the input text during pattern matching. Let's take a look at how grouping and capturing work in the example regex pattern for mathcing emails.
- `([a-z0-9_\.-]+)`: This is the first group, which captures the username part of the email address. It allows for one or more occurrences of lowercase letters, digits, underscores, dots, or hyphens.
- `([\da-z\.-]+)`: This is the second group, which captures the domain name part of the email address. It allows for one or more occurrences of digits, lowercase letters, dots, or hyphens.
- `([a-z\.]{2,6})`: This is the third group, which captures the top-level domain part of the email address. It allows for two to six occurrences of lowercase letters or dots.
- Capturing: When a match is found, the portions of the input text that match the grouped patterns are captured and can be extracted for further processing. The captured groups are typically numbered in the order of their occurrence, starting from 1.

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

[Habib Maksoud](https://github.com/mynamebrogrammer) is an up and coming developer who is passionate about learning new technologies and sharing his knowledge with others. He is currently a student at the full stack web development bootcamp at a UCLA extension program. He is currently looking for a job as a web developer. You can find him on [LinkedIn](https://www.linkedin.com/in/habib-maksoud-87aa2a253/).
