# Strings and regular expressions

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

- Parentheses can make it clear which calculations should happen before concatenation

```java
int apples = 3;
int oranges = 2;

System.out.println("Fruit count: " + (apples + oranges));
```

```text
Fruit count: 5
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

- Call `equals` on a known string value when comparing user input. This avoids an error if the variable being checked is `null`, a value we will discuss later

```java
if ("yes".equals(answer)) {
    System.out.println("Continuing");
}
```

## Getting information from a string

- The `length` method returns the number of characters in a string
- Characters are indexed starting from `0`, so the first character is at index `0` and the last is at index `length() - 1`
- The `charAt` method returns the character at the given index

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

- An index must be within the string. For example, `word.charAt(4)` causes an error because the valid indexes of `"Java"` are `0` through `3`
- A `for` loop can visit each character in a string

```java
String word = "Java";

for (int i = 0; i < word.length(); i++) {
    System.out.println(word.charAt(i));
}
```

## Changing and taking parts of a string

- Strings in Java are **immutable**: their contents cannot be changed after the string is created
- Methods such as `toUpperCase`, `toLowerCase`, and `trim` return a new string. To keep the result, assign it to a variable
- `trim` removes whitespace at the beginning and end of a string; it does not remove spaces between words

```java
String name = "  Ada Lovelace  ";

String trimmedName = name.trim();
String upperCaseName = trimmedName.toUpperCase();

System.out.println(">" + trimmedName + "<");
System.out.println(upperCaseName);
System.out.println(name);
```

```text
>Ada Lovelace<
ADA LOVELACE
  Ada Lovelace
```

- The `substring` method returns part of a string. The starting index is included and the ending index is excluded
- `substring(start)` takes characters from `start` to the end of the string

```java
String word = "Programming";

System.out.println(word.substring(0, 7));
System.out.println(word.substring(7));
```

```text
Program
ming
```

## Searching for text

- Use `contains` to check whether a string includes a sequence of characters
- Use `startsWith` and `endsWith` to check the beginning or end of a string
- These methods are case-sensitive: `"Java"` does not contain `"java"`

```java
String fileName = "report.pdf";

System.out.println(fileName.endsWith(".pdf"));
System.out.println(fileName.contains("port"));
System.out.println(fileName.startsWith("Report"));
```

```text
true
true
false
```

## What is a regular expression?

- A **regular expression**, often shortened to **regex**, is a pattern that describes text
- A regex can be used to check whether text follows a format, find text within a larger string, or replace matching text
- For example, `[0-9]{5}` describes exactly five digits in a row
- A regex is not Java code. Java passes it as a string to methods such as `matches` or `replaceAll`

## Common regular expression symbols

| Pattern | Meaning | Example |
| --- | --- | --- |
| `abc` | The exact characters `abc` | `abc` matches `abc` |
| `[abc]` | One character: `a`, `b`, or `c` | `[abc]` matches `b` |
| `[a-z]` | One lowercase letter from `a` to `z` | `[a-z]` matches `m` |
| `[A-Z]` | One uppercase letter from `A` to `Z` | `[A-Z]` matches `M` |
| `[0-9]` | One digit from `0` to `9` | `[0-9]` matches `7` |
| `\d` | One digit | `\d` matches `7` |
| `\s` | One whitespace character, such as a space | `\s` matches a space |
| `.` | Any one character | `c.t` matches `cat` |
| `*` | Zero or more of the previous item | `ab*` matches `a`, `ab`, or `abb` |
| `+` | One or more of the previous item | `ab+` matches `ab` or `abb`, but not `a` |
| `?` | Zero or one of the previous item | `colou?r` matches `color` or `colour` |
| `{n}` | Exactly `n` of the previous item | `[0-9]{5}` matches five digits |
| `{n,m}` | Between `n` and `m` of the previous item | `[0-9]{2,4}` matches two to four digits |
| `^` | The beginning of the text | `^A` requires the text to start with `A` |
| `$` | The end of the text | `z$` requires the text to end with `z` |

- Square brackets describe a choice of one character. For example, `[aeiou]` matches one lowercase vowel
- Parentheses group parts of a pattern. For example, `(ab)+` matches `ab`, `abab`, or more repetitions of `ab`
- A backslash gives a character a special meaning in regex. In a Java string, backslashes must also be escaped, so write `\\d` in Java source to pass `\d` to the regex engine
- To match a character that normally has a special meaning, such as a dot, put a backslash before it in the regex. In Java source, use `"\\."` to match a literal dot

## Checking the whole string with `matches`

- The `String.matches` method returns `true` if the **whole string** matches the regex
- It does not just check whether some part of the string matches
- For example, `[0-9]{5}` accepts exactly five digits and rejects text with extra characters

```java
String postalCode = "00100";

if (postalCode.matches("[0-9]{5}")) {
    System.out.println("The postal code has five digits");
} else {
    System.out.println("The postal code must contain exactly five digits");
}
```

```text
The postal code has five digits
```

- In this example, the pattern `[0-9]{5}` means five characters, each of which is a digit from `0` to `9`
- `"12a45"` and `"123456"` do not match because they do not contain exactly five digits
- A format check only checks the text's shape. It does not prove that a postal code or other value is real

## Finding a match inside text

- `matches` checks the entire string. To search for a matching part inside a larger string, use `Pattern` and `Matcher`
- `Matcher.find` returns `true` when it finds a matching part. Calling it again searches for the next match

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

String sentence = "Order numbers: 123 and 456.";
Pattern pattern = Pattern.compile("[0-9]+");
Matcher matcher = pattern.matcher(sentence);

while (matcher.find()) {
    System.out.println(matcher.group());
}
```

```text
123
456
```

- `Pattern.compile` creates a reusable regex pattern
- `matcher.group()` returns the text found by the most recent successful `find` call

## Replacing and splitting text with regex

- `replaceAll` replaces every part of a string that matches a regex. Like other string methods, it returns a new string
- `split` separates a string wherever the regex matches and returns an array of strings

```java
String sentence = "Java   is fun";
String oneSpace = sentence.replaceAll("\\s+", " ");
String[] words = oneSpace.split(" ");

System.out.println(oneSpace);
System.out.println(words[0]);
System.out.println(words[1]);
System.out.println(words[2]);
```

```text
Java is fun
Java
is
fun
```

- In this example, `\\s+` means one or more whitespace characters. The doubled backslash is required because this pattern is written inside a Java string
- `split` also uses a regex, so characters with special regex meanings may need to be escaped

## 💡 String and regex example: validating a student number

> Write a program that checks whether a student number consists of exactly six digits.

```java
import java.util.Scanner;

public class StudentNumberCheck {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter your student number: ");
        String studentNumber = input.nextLine();

        if (studentNumber.matches("[0-9]{6}")) {
            System.out.println("The student number format is valid");
        } else {
            System.out.println("The student number must contain exactly six digits");
        }
    }
}
```

```text
Enter your student number: 123456
The student number format is valid
```

- Keep user input as a string when checking its format. If the student number were converted to an integer, leading zeroes would be lost
- This check only verifies that the input has six digits; it does not verify that the number belongs to a real student