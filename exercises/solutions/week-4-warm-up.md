# Solutions: Strings & Dates Warm-up Exercises

## Warm-up exercise 1

```java
package week4;

import java.util.Scanner;

public class WarmUp1 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter a sentence: ");
        String sentence = input.nextLine().trim();
        String wordsOnly = sentence.replaceAll("[,?.!]", " ").trim();

        if (wordsOnly.isEmpty()) {
            System.out.println("Number of words: 0");
        } else {
            System.out.println("Number of words: " + wordsOnly.split("\\s+").length);
        }
    }
}
```

## Warm-up exercise 2

```java
package week4;

import java.util.Scanner;

public class WarmUp2 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter text: ");
        String text = input.nextLine();
        StringBuilder normalized = new StringBuilder();

        for (int index = 0; index < text.length(); index++) {
            char character = text.charAt(index);
            if (Character.isLetterOrDigit(character)) {
                normalized.append(Character.toLowerCase(character));
            }
        }

        boolean palindrome = true;
        for (int left = 0, right = normalized.length() - 1; left < right; left++, right--) {
            if (normalized.charAt(left) != normalized.charAt(right)) {
                palindrome = false;
                break;
            }
        }

        if (palindrome) {
            System.out.println("The text is a palindrome");
        } else {
            System.out.println("The text is not a palindrome");
        }
    }
}
```

## Warm-up exercise 3

```java
package week4;

import java.util.Scanner;

public class WarmUp3 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter PIN (4-8 digits): ");
        String pin = input.nextLine();

        if (pin.length() < 4 || pin.length() > 8 || !pin.matches("\\d+")) {
            System.out.println("PIN invalid");
            return;
        }

        for (int attempt = 1; attempt <= 3; attempt++) {
            System.out.print("Enter PIN again: ");
            String confirmation = input.nextLine();
            if (pin.equals(confirmation)) {
                System.out.println("PIN valid");
                return;
            }
        }

        System.out.println("PIN invalid");
    }
}
```

## Warm-up exercise 4

```java
package week4;

import java.time.DayOfWeek;
import java.time.LocalDate;
import java.time.Month;
import java.time.temporal.TemporalAdjusters;

public class WarmUp4 {
    public static void main(String[] args) {
        int year = LocalDate.now().getYear();
        LocalDate midsummerDay = LocalDate.of(year, Month.JUNE, 20)
                .with(TemporalAdjusters.nextOrSame(DayOfWeek.SATURDAY));
        LocalDate midsummerEve = midsummerDay.minusDays(1);

        System.out.println("Midsummer Eve is " + midsummerEve);
    }
}
```

## Warm-up exercise 5

```java
package week4;

import java.time.DayOfWeek;
import java.time.LocalDate;
import java.time.YearMonth;

public class WarmUp5 {
    public static void main(String[] args) {
        LocalDate today = LocalDate.now();
        YearMonth month = YearMonth.from(today);
        LocalDate fridayTheThirteenth;

        while (true) {
            LocalDate candidate = month.atDay(13);
            if (candidate.getDayOfWeek() == DayOfWeek.FRIDAY && !candidate.isBefore(today)) {
                fridayTheThirteenth = candidate;
                break;
            }
            month = month.plusMonths(1);
        }

        System.out.println("The next Friday the 13th is " + fridayTheThirteenth);
    }
}
```