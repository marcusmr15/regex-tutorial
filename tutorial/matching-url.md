# Matching a URL with Regex - Tutorial Guide

A __Regular Expression__, commonly abbreviated as `Regex`, serves as a powerful tool in computer science and text processing alike. Essentially, it is a sequence of characters designed to define a search pattern. Regex enables users to not only locate specific patterns within a body of text but also to manipulate and manage textual data efficiently with its intricate syntax and functionality.

One of the key characteristics of Regular Expressions is their versatility, extending beyond mere text editors to encompass a wide array of programming languages and scripting environments. 


⬇ __TIP__ ⬇

~~~
Press Ctrl + F, then click the '.*' button to use Regular Expressions when searching within text editors or software like VS Code.
~~~

They empower both developers and data analysts to perform intricate search, extraction, and manipulation tasks with ease. Whether it's parsing through large datasets, validating user input, or implementing advanced text processing algorithms, Regular Expressions emerge as indispensable tools in the toolkit of software engineers and data professionals alike. 

Regex application spans across domains such as web development, data mining, natural language processing, and more, showcasing their significance in modern computing paradigms. In essence, Regular Expressions serve as the cornerstone of text processing, offering a robust framework for pattern matching and manipulation in diverse computational contexts.

## Summary

The following Regex is designed to locate any given URL (Uniform Resource Locator) within a text:

~~~
\bhttps?:\/\/[\w.-]+([\/?@#$%^&*()!~`=+[\]{}|;:'",<>\w.-]+)?
~~~

This regex provides a basic mechanism for identifying URLs, handling both http and https protocols, and allowing for various characters in the URL path.

❗`NOTE` 

It is important to consider the following:

1. This Regex does not enforce rules for valid domain names strictly. For instance, consecutive dots or hyphens may in invalid positions will result in that URL not being rejected by the Regex.
2. The character class for the optional part is quite permissive and might include characters that are not typically found in a valid URL path or query string (e.g., `@`, `^`, `*`). 

Given these considerations, this Regex successfully identifies URLs with all combinations of characters. If strict URL validation is required for more precise domain and path rules, modifications must be made.

## Table of Contents

- [Boundaries](#boundaries)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Conclusion](#conclusion)
- [Author](#author)

## Regex Components

### Boundaries

In Regular Expressions, boundaries are used to define positions within a string rather than matching actual characters. Boundaries are useful for specifying where a match should occur relative to certain locations like word boundaries, the start or end of a line, or the start or end of a string.

~~~
\b
~~~

In our Regex:

- `\b`: Matches a position where a word character (usually a letter, digit, or underscore) is adjacent to a non-word character or the start/end of a string.

`\b` ensures that the match occurs at the start of a word. For instance, it would prevent matching a URL embedded within another word.



### Quantifiers

Quantifiers in Regular Expressions specify how many instances of a character, group, or character class should be matched in the input string. 

In our Regex, the `?` and `+` characters are quantifiers:

~~~
https?:\/\/
~~~

- In this case, we are literally searching for the characters 'http', but the `s?` part makes the `s` optional, so it matches both `http` and `https`.

~~~
(...)?
~~~

- The `?` after the group (parenthesis) means that the entire group is optional (it can occur 0 or 1 time).

~~~
[...]+
~~~

- `+`: This indicates one or more of the preceding character class within the brackets and is used twice in the regex. Thus, this part matches the domain name and possibly subdomains (e.g., www.example, sub.domain). However, in this case we are not searching for the literal character `w`, more of this in the next topic.

    - Notice the `+` is used three times in the Regex, but only twice as a quantifier (at the end of a bracket) in this Regex. The extra time it appears is as a literal character.

### Character Classes

Character classes in Regular Expressions define sets of characters that can match a single character in the input string. In our Regex, character classes are used to match specific types of characters.

~~~
\w.-
~~~

- `\w`: Matches word characters (including underscores), dots, and hyphens in the domain name and path. `\w` matches any word character (alphanumeric & underscore), any number, and underscores; which would be the same as typing: `a-zA-Z0-9_`.
- `.` : Matches a literal dot (for domain names).
- `-`: Matches a literal hyphen (also common in domain names).

~~~
\/?@#$%^&*()!~`=+[\]{}|;:'",<>\w.-
~~~

This matches various special characters, word characters (including underscores), dots, and hyphens (notice the last 4 characters, and how they are explained in the text above) in the URL path. 

### Bracket Expressions

Bracket expressions in Regular Expressions, also known as character classes, allow you to define a set of characters that you want to match. When you use a bracket expression, the regex engine will match any single character contained within the brackets. We use Bracket Expressions in our Regex twice.

~~~
[...]
~~~

Escape Sequences within Brackets:

- To match special characters like `[`, `]`, and `\` in the second Bracket Expression, they need to be escaped with a backslash `\` first as these characters on their own have rules of their own.

### Grouping and Capturing

Grouping and capturing in Regular Expressions allow multiple characters to be treated as a single unit and capture the matched text for later use. Basically Grouping and Capturing is used to create sub-patterns within a regex, which can be referred to later. In our Regex, parentheses (...) are used for grouping and capturing.

~~~
(...)
~~~

- `([\/?@#$%^&*()!~=+[]{}|;:'",<>\w.-]+)?`: This captures the part of the URL that follows the domain. The group is optional, as denoted by the `?` quantifier outside the parentheses.

The content matched by the expression inside the parentheses can be referenced later in the regex or in replacement strings.

### Greedy and Lazy Match

Greedy quantifiers try to match as much text as possible while still allowing the overall Regex to succeed.

In our regex:

~~~
https?
~~~

The `?` here is not a greedy quantifier. It makes the `s` optional, matching either http or https.

~~~
[\w.-]+:
~~~

The `+` is a greedy quantifier. It matches one or more occurrences of any word character (`\w`), dot (`.`), or hyphen (`-`). It tries to consume as many of these characters as possible.

~~~
([\/?@#$%^&*()!~=+[]{}|;:'",<>\w.-]+)?`:
~~~

The `+` inside the group is a greedy quantifier. It matches one or more of any characters listed within the brackets. The outer `?` makes the entire group optional (it can match zero or one occurrence of the group).
Greedy matching can lead to "overconsumption" of characters if not handled properly.

## Conclusion

To summarize the concepts explained in the text above, this Regex is divided into three main parts:

1. The first part will match a URL that starts with `http` or `https`, followed by `://`.

2. It then will match one or more word characters to capture domain names and subdomains, with either:
    - Lower and uppercase characters (`a-z` and `A-Z`)
    - Numbers (`0-9`)
    - Underscores (`_`)
    - Dots (`.`)
    - Hyphens (`-`)
3. Optionally, it can capture additional URL components like paths, query strings, and fragments, which include a wide array of possible characters. like these, to name a few:
    - `@`
    - `#`
    - `%`
    - `^`
    - `&`

⚠️ Is it also important to note that case-sensitivity is taken into consideration in Regular Expressions. `\W` will search for everything BUT what `\w` stands for. In other words, `\W` is a negation of `\w`. 

### Example Matches

This Regex will successfully identify URLs like the examples provided below:

- http://example.com
- https://www.example.com/path/to/resource?query=param#fragment
- http://sub.domain-example.com/path@with=+-special$chara[]ct{}er*s
- https://example.com/

You can test this Regex yourself by going to a website like [RegExr](https://regexr.com/) or [Regex101](https://regex101.com/), and pasting the examples provided above. You can also test with your own URLs!

## Author

This Regex tutorial was created by __Marcos Munoz__, an emerging full-stack web developer from Mexico City. 

Please feel free to contact me by email and I would also like to extend an invitation for you to check out my GitHub profile, you can review other projects I have worked in, which go from creating a quiz website to programming a full-stack web application following an MVC structure.

- GitHub: [marcusmr15](https://github.com/marcusmr15)
- Email: marcosmunozr15@gmail.com

Thanks for reading! 📖
