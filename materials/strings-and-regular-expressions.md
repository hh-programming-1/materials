# Strings and regular expressions

<!-- TODO review this -->

## What is a string?

- A **string** is a sequence of characters, such as a name, a sentence, or a number entered by the user
- In Java, strings are objects of the `String` class. A string value is written between double quotation marks
- A string that contains no characters is called an **empty string** and is written as `""`
- A string is not the same as a `char`: a `char` holds one character and is written between single quotation marks

```java
String name = "Ada";
String message = "Hello, " + name + "!";
char firstLetter = 'A';
String empty = "";

System.out.println(message);
```

```text
Hello, Ada!
```

## Combining strings

- The `+` operator combines strings. If either side of `+` is a string, Java converts the other value to text
- This is called **concatenation**

```java
String firstName = "Ada";
String lastName = "Lovelace";
int year = 1843;

String fullName = firstName + " " + lastName;
System.out.println(fullName);
System.out.println("Year: " + year);
```

```text
Ada Lovelace
Year: 1843
```

## Comparing strings

- Use the `equals` method to check whether two strings contain the same characters
- Do not use `==` to compare string contents. `==` checks whether two references point to the same object, not whether their text is equal
- `equalsIgnoreCase` compares text without distinguishing uppercase and lowercase letters

```java
String answer = "yes";

if (answer.equals("yes")) {
    System.out.println("Continuing");
}

if (answer.equalsIgnoreCase("YES")) {
    System.out.println("The answer is yes");
}
```

```text
Continuing
The answer is yes
```

## Getting information from a string

- The `length` method returns the number of characters in a string
- Characters are indexed starting from `0`, so the first character is at index `0` and the last is at index `length() - 1`
- The `charAt` method returns the character at the given index
- An index must be within the string. For example, `word.charAt(4)` causes an error because the valid indexes of `"Java"` are `0` through `3`

```java
String word = "Java";

System.out.println(word.length());
System.out.println(word.charAt(0));
System.out.println(word.charAt(3));
```

```text
4
J
a
```

## Changing a string

- In Java, string contents cannot be changed after the string is created
- Methods such as `toUpperCase`, `toLowerCase`, and `trim` return a new string. To keep the result, assign it to a variable
- `trim` removes whitespace at the beginning and end of a string; it does not remove spaces between words

```java
String name = "  Ada Lovelace  ";

// trim removes whitespace at the beginning and end of a string
String trimmedName = name.trim();
// toUpperCase turns all characters to upper case, e.g. hello => HELLO
String upperCaseName = trimmedName.toUpperCase();
// toLowerCase turns all characters to lower case, e.g. HeLlo => hello
String lowerCaseName = trimmedName.toLowerCase();

System.out.println(">" + trimmedName + "<");
System.out.println(upperCaseName);
System.out.println(lowerCaseName);
```

```text
>Ada Lovelace<
ADA LOVELACE
ada lovelace
```

## Taking parts of a string

- The `substring` method returns part of a string. The starting index is included and the ending index is excluded
- `substring(start)` takes characters from `start` to the end of the string

```java
String word = "Programming";
// Takes characters from index 0 until index 6 (excluding the end index)
System.out.println(word.substring(0, 7));
// Takes characters from index 7 until the end of the string
System.out.println(word.substring(7));
```

```text
Program
ming
```

## Searching for text

- The `contains` method checks whether a string includes a sequence of characters
- The `startsWith` and `endsWith` methods check the beginning or end of a string

```java
String fileName = "report.pdf";

System.out.println(fileName.endsWith(".pdf"));
System.out.println(fileName.contains("port"));
System.out.println(fileName.startsWith("exam"));
```

```text
true
true
false
```

## What is a regular expression?

- A **regular expression**, often shortened to **regex**, is a pattern that describes text
- A regex can be used to, for example, check whether a strings follows a specified format
- Here are some examples of values and their regular expression patterns

| Value                                               | Pattern description                                                             | Regex                      |
| --------------------------------------------------- | ------------------------------------------------------------------------------- | -------------------------- |
| Postal code, e.g. `00610`                           | Exactly five digits                                                             | `\d{5}`                    |
| Date, e.g. `22.10.2026`                             | Two digits, a period, two digits, a period, and four digits                     | `\d{2}\.\d{2}\.\d{4}`      |
| Haaga-Helia email, e.g. `john.smith@haaga-helia.fi` | One or more word characters, dot, one or more word characters, @haaga-helia.fi  | `\w+\.\w+@haaga-helia\.fi` |
| Social security number, e.g. `010101-123N`          | Six digits, a century marker (A, + or -), three digits, and a control character | `\d{6}[A+-]\d{3}[0-9A-z]`  |

## Common regular expression symbols

| Pattern | Meaning                                   | Example                                  |
| ------- | ----------------------------------------- | ---------------------------------------- |
| `abc`   | The exact characters `abc`                | `abc` matches `abc`                      |
| `[abc]` | One character: `a`, `b`, or `c`           | `[abc]` matches `b`                      |
| `[a-z]` | One lowercase letter from `a` to `z`      | `[a-z]` matches `m`                      |
| `[A-Z]` | One uppercase letter from `A` to `Z`      | `[A-Z]` matches `M`                      |
| `[0-9]` | One digit from `0` to `9`                 | `[0-9]` matches `7`                      |
| `\.`    | . character                               | `\.` matches `.`                         |
| `\d`    | One digit                                 | `\d` matches `7`                         |
| `\s`    | One whitespace character, such as a space | `\s` matches a space                     |
| `.`     | Any one character                         | `c.t` matches `cat`                      |
| `*`     | Zero or more of the previous item         | `ab*` matches `a`, `ab`, or `abb`        |
| `+`     | One or more of the previous item          | `ab+` matches `ab` or `abb`, but not `a` |
| `?`     | Zero or one of the previous item          | `colou?r` matches `color` or `colour`    |
| `{n}`   | Exactly `n` of the previous item          | `[0-9]{5}` matches five digits           |
| `{n,m}` | Between `n` and `m` of the previous item  | `[0-9]{2,4}` matches two to four digits  |

- Square brackets describe a choice of one character. For example, `[aeiou]` matches one lowercase vowel
- Parentheses group parts of a pattern. For example, `(ab)+` matches `ab`, `abab`, or more repetitions of `ab`
- To match a character that normally has a special meaning, such as a dot, we put a backslash before it in the regex. For example, we use `\.` to match a literal dot

## Checking the whole string with `matches`

- The `String.matches` method returns `true` if the **whole string** matches the regex
- It does not just check whether some part of the string matches. For example, `[0-9]{5}` accepts exactly five digits and rejects text with extra characters
- When the backslash `\` is in the pattern, a double backslash `\\` needs to be used in the regex string

```java
String postalCode = "00100";
String email = "bill.gates@microsoft.com";

if (postalCode.matches("[0-9]{5}")) {
    System.out.println("The postal code has five digits");
}

// Note that double backslash \\ is required with, e.g. \w pattern!
if (email.matches("\\w+\\.\\w+@haaga-helia\\.fi")) {
    System.out.println("The email matches Haaga-Helia's format");
}
```

```text
The postal code has five digits
```

## 💡 String and regex example: validating the date format

> Write a program that checks whether the given date is in the ISO date format YYYY-MM-DD.

```java
import java.util.Scanner;

public class DateFormatCheck {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter the date in format YYYY-MM-DD: ");
        String studentNumber = input.nextLine();

        if (studentNumber.matches("[0-9]{4}-[0-9]{2}-[0-9]{2}")) {
            System.out.println("The date format is valid");
        } else {
            System.out.println("The date is not in format YYYY-MM-DD");
        }
    }
}
```

```text
Enter your student number: 2026-10-22
The date format is valid
```

> [!NOTE]
> This regex checks that the date format is correct, but doesn't check that date itself is real. For example, the date `"2026-99-99"` would pass this check. Sometimes additional check are required on top of the pattern check.
