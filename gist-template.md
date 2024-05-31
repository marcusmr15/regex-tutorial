# Matching a URL with Regex - Tutorial Guide

A __Regular Expression__, commonly abbreviated as `Regex`, serves as a powerful tool in computer science and text processing alike. Essentially, it is a sequence of characters designed to define a search pattern. Regex enables users to not only locate specific patterns within a body of text but also to manipulate and manage textual data efficiently with its intricate syntax and functionality.

One of the key characteristics of Regular Expressions is their versatility, extending beyond mere text editors to encompass a wide array of programming languages and scripting environments. 

⬇ __TIP__ ⬇

~~~
Press Ctrl + F, then click the '.*' button to use the regular expressions search within text editors or software like VS Code
~~~

They empower both developers and data analysts to perform intricate search, extraction, and manipulation tasks with ease. Whether it's parsing through large datasets, validating user input, or implementing advanced text processing algorithms, Regular Expressions emerge as indispensable tools in the toolkit of software engineers and data professionals the same. 

Regex application spans across domains such as web development, data mining, natural language processing, and more, showcasing their significance in modern computing paradigms. In essence, Regular Expressions serve as the cornerstone of text processing, offering a robust framework for pattern matching and manipulation in diverse computational contexts.

## Summary

The following Regex is designed to locate any given URL (Uniform Resource Locator) within a text:

~~~
\bhttps?:\/\/[\w.-]+([\/?@#$%^&*()!~`=+[\]{}|;:'",<>\w.-]+)?
~~~

This regex provides a basic mechanism for identifying URLs, handling both http and https protocols, and allowing for various characters in the URL path.

❗ `NOTE` 

It is important to consider the following:

1. This Regex does not enforce rules for valid domain names strictly, for instance, with consecutive dots or hyphens in invalid positions.
2. The character class for the optional part is quite permissive and might include characters that are not typically found in a valid URL path or query string. 

Given these considerations, this Regex successfully identifies URLs with all combinations of characters. If strict URL validation is required for more precise domain and path rules, modifications must be made.

## Table of Contents

- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Conclusion](#conclusion)
- [Author](#author)

## Regex Components


### Quantifiers

Quantifiers in regular expressions specify how many instances of a character, group, or character class should be matched in the input string. 

In our regex, the `?` and `+` characters are quantifiers:

- `https?` = The 's?' part makes the 's' optional, so it matches both 'http' and 'https'.
- [...]`+`: This indicates one or more of the preceding character class within the brackets and is used twice in the regex. Thus, this part matches the domain name and possibly subdomains (e.g., www.example, sub.domain).

### Character Classes

Character classes in regular expressions define sets of characters that can match a single character in the input string. In our regex, character classes are used to match specific types of characters:

- `[\w.-]`: Matches word characters (including underscores), dots, and hyphens in the domain name and path. `\w` matches any word character (alphanumeric & underscore), any number, and underscores; which would be the same as typing: `a-zA-Z0-9_`.

- `.` : Matches a literal dot (for domain names).
-: Matches a literal hyphen (also common in domain names).

- [/?@#$%^&*()!~`=+
{}|;:'",<>\w.-]: Matches various special characters, word characters (including underscores), dots, and hyphens in the URL path.

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

## Conclusion

Placeholder text.

## Author

_A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)_

- Email: marcosmunozr15@gmail.com
- GitHub: [github username](placehodler)
