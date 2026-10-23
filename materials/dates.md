# Date and time

## Date and time values in Java

- Dates and times are often needed in applications, for example an order's delivery date, an invoice's due date, the moment of time a message was saved, etc.
- Java has classes for handling time in the package `java.time`
  - `LocalDate`: represents a **date** with day, month, and year
  - `LocalTime`: represents a **time of day** with hour, minute and seconds
  - `LocalDateTime`: represents a **date and the time of day**
- Objects of these classes can be used, for example, to represent a desired moment in time, compare them to each other, and add or subtract time
- Like strings, these classes are immutable and their value cannot change after initialization
- Other classes used for handling dates and times can be found in the packages `java.time.format` and `java.time.temporal`

## Creating date and time values

- Here are some examples of creating date and time values using the `LocalDate` and `LocalTime` classes

```java
// Import the classes to use them
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

import java.util.ArrayList;

public class DateAndTimeExample {
    public static void main(String[] args) {
        LocalDate today = LocalDate.now(); // today's date
        LocalTime timeNow = LocalTime.now(); // current time of day
        LocalDate birthday = LocalDate.parse("1993-01-19"); // from a YYYY-MM-DD string
        LocalDate christmasEve = LocalDate.of(2027, 12, 24); // from (year, month, day) parameters
        LocalTime afternoonTeaTime = LocalTime.of(17, 0); // note: hours are 0-23

        System.out.println("Birthday: " + birthday);
        System.out.println("Year of birth:  " + birthday.getYear());
        System.out.println("Tea time is at: " + afternoonTeaTime);

    }
}
```

```text
Birthday: 1993-01-19
Year of birth: 1993
Tea time is at: 17:00
```

## Formatting date and time values

- The string presentation of the date and time formats follow the standard formats, e.g. `1993-01-19`
- We can use the `DateTimeFormatter.ofPattern` to create the format we want, e.g. `1.19.1993`

```java
Scanner input = new Scanner(System.in);
// Create a format for day.month.year, e.g. 1.19.1993
// d = day of year, M = month of year, yyyy = year
DateTimeFormatter dateFormat = DateTimeFormatter.ofPattern("d.M.yyyy");
System.out.print("Enter a date in format day.month.year: ");
String dateString = input.nextLine();
// LocalDate.parse method will now use our format
LocalDate date = LocalDate.parse(dateString, dateFormat);

System.out.println("Standard format: " + date);
System.out.println("Finnish format: " + dateFormat.format(date));
```

```
Enter a date in format day.month.year: 19.1.1993
Standard format: 19-01-1993
Finnish format: 19.1.1993
```

## Getting parts of date and time

- Methods such as `getYear`, `getMonthValue`, and `getDayOfMonth` return parts of a `LocalDate`
- Methods such as `getHour` and `getMinute` return parts of a `LocalTime`

```java
LocalDate date = LocalDate.of(2026, 10, 21);
LocalTime time = LocalTime.of(9, 30);

System.out.println(date.getYear());
System.out.println(date.getMonthValue());
System.out.println(date.getDayOfMonth());
System.out.println(time.getHour());
System.out.println(time.getMinute());
```

```
2026
10
21
9
30
```

## Comparisons and calculations

- `equals` method is to check whether two date or time objects represent the same value
- `isBefore` and `isAfter` methods are used to check which date or time comes first
- Methods like `plusDays` can be used to add or subtract parts (hour, day, month, ...). The result is a **new time-class object** that contains a valid moment.

```java
import java.time.LocalDate;

LocalDate today = LocalDate.of(2026, 10, 21);
LocalDate deadline = LocalDate.of(2026, 11, 1);

if (today.isBefore(deadline)) {
    System.out.println("There is still time before the deadline!");
}

LocalDate inSevenDays = today.plusDays(7);

System.out.println("In seven days the date is: " + inSevenDays)
```

```text
There is still time before the deadline!
In seven days the date is: 2026-10-28
```

## 💡 dates example: checking for holiday

> Write a program that asks the user when their holiday begins. Then, it should check whether their 28 day holiday has ended or not.

```java
import java.util.Scanner;
import java.time.LocalDate;

public class HolidayCheck {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter when your holiday starts (YYYY-MM-DD): ");
        String dateString = input.nextLine();
        LocalDate start = LocalDate.parse(dateString);
        LocalDate end = start.plusDays(28);
        LocalDate today = LocalDate.now();

        System.out.println("Your holiday ends on " + end);

        if (today.isAfter(end)) {
            System.out.println("Your holiday has ended");
        } else {
            System.out.println("Your holiday is still going or has not started yet");
        }
    }
}
```

```text
Enter when your holiday starts (YYYY-MM-DD): 2026-06-01
Your holiday ends on 2026-06-29
Your holiday has ended
```
