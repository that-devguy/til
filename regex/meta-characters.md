# Meta-characters

Special characters that have a predefined meaning and serve as building blocks for creating patterns. These have a special significance in regex and are used to match specific characters or define behaviors.

## Meta-characters
- [Single Character](#single-characters)
- [Quantifiers](#quantifiers)
- [Position](#position)
- [Character Classes](#character-classes)
- [Alternation](#alternation)

## Single Characters
Characters that provide shortcuts for matching specific types of characters or character classes.

Most commonly used single character meta characters:
- `.` (dot): Matches any single character except a newline character.
- `\d`: Matches any digit character (0-9).
- `\D`: Matches any non-digit character.
- `\w`: Matches any word character (alphanumeric character or underscore).
- `\W`: Matches any non-word character.
- `\s`: Matches any whitespace character (space, tab, newline, etc.).
- `\S`: Matches any non-whitespace character.
- `\b`: Matches a word boundary (the position between a word character and a non-word character).
- `\B`: Matches a non-word boundary.

## Quantifiers
Characters that allow you to specify the number of occurrences of a character or group in a pattern.

List of quantifiers:
- `*`: Matches zero or more occurrences of the preceding character or group.
- `+`: Matches one or more occurrences of the preceding character or group.
- `?`: Matches zero or one occurrence of the preceding character or group.
- `{n}`: Matches exactly n occurrences of the preceding character or group.
- `{n,}`: Matches n or more occurrences of the preceding character or group.
- `{n,m}`: Matches at least n and at most m occurrences of the preceding character or group.

## Position
Characters that help define patterns based on the position within the text, such as matching the start or end of a line or a word boundary.

List of position characters:
- `^`: Matches the start of a line or string.
- `$`: Matches the end of a line or string.
- `\b`: Matches a word boundary.
- `\B`: Matches a non-word boundary.

## Character Classes
A set of characters enclosed within brackets `[]` that represents a single character from the set of characters specified within the class. This allows you to define patterns that match specific sets of characters without explicitly listing each character individually.

Example of a character class:

*Example text:* The lynk is quite a link don't you think? l nk l(nk

*Our regex:* `l[yi (]nk`

*Our result:* The `lynk` is quite a `link` don't you think? `l nk` `l(nk`

Important notes about character classes:
- When a regular expression encounters a character class, it will match any single character that belongs to that class. For example the character class `[aeious]` will match any lowercase vowel.
- Character classes can specify ranges of characters using `-` between the starting and ending characters. For example, `[a-z]` means any lowercase letter from `a` to `z`.
- By placing a `^` as the first character inside our character class we can negate it. For example, `[^0-9]` matches any character that is not a digit.
- Some characters within character classes have special meanings. For example `-` and `^`, to match these special characters we can escape them with `\`.

## Alternation

Refers to the concept of providing multiple choices or options for matching. It allows you to specify alternative for a particular position within a pattern. Represented by a pipe, `|`.

Example of alternation:

*Example text:* zach@example.com, zach@example.net, and zach@example.org

*Our regex:* `\w+@\w+\.(net|com)`

*Our result:* `zach@example.com`, `zach@example.net`, and zach@example.org

Important notes about alternation:
- When the regex encounters the `|`, it will try to match the expression before the `|` or the one after. It will choose the first alternative that matches.
- You can have more than two alternatives. For instance, if you look at the example above, we could select all 3 emails by changing the alternation to `(net|com|org)`.
- Alternatives are usually grouped together within parentheses. This allows us to apply additional modifiers or contraints to the group as a whole.
- Order matters. Regex evalutates the alternatives from left to right, and stops evaluating the remaining alternatives once it's found a match.

