# Dates

<!-- TODO review this -->

## Dates and times in Java

- Java provides the `java.time` package for working with dates and times
- The main classes in this material are:
  - `LocalDate` for a calendar date, such as 2026-10-21
  - `LocalTime` for a time of day, such as 09:30
  - `LocalDateTime` for a date and time together, such as 2026-10-21T09:30
- These classes do not include a time zone. They are useful for dates and times as people use them locally, but not for identifying a precise moment across different time zones
- Date and time values are not strings. Java stores them as date/time objects so that they can be compared and calculated correctly

## Getting the current date and time

- The `now` method returns the current date or time from the computer's clock
- Import each class from `java.time` before using it

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

LocalDate today = LocalDate.now();
LocalTime currentTime = LocalTime.now();
LocalDateTime now = LocalDateTime.now();

System.out.println(today);
System.out.println(currentTime);
System.out.println(now);
```

- The exact output depends on when the program runs. The default output uses the ISO format: date as `year-month-day` and time using a 24-hour clock

```text
2026-10-21
09:30:15.123
2026-10-21T09:30:15.123
```

## Creating date and time values

- Use `of` when you want to create a date or time with specific values
- `LocalDate.of` takes the year, month, and day
- `LocalTime.of` takes the hour and minute, and can also take seconds
- The month is a number from `1` to `12`, and the hour uses the 24-hour clock

```java
import java.time.LocalDate;
import java.time.LocalTime;

LocalDate birthday = LocalDate.of(2000, 5, 20);
LocalTime meetingTime = LocalTime.of(14, 30);
LocalTime lunchTime = LocalTime.of(12, 0, 0);

System.out.println(birthday);
System.out.println(meetingTime);
System.out.println(lunchTime);
```

```text
2000-05-20
14:30
12:00
```

- Java checks that values form a valid date or time. For example, `LocalDate.of(2025, 2, 30)` is invalid and causes a `DateTimeException`
- Leap years and the different number of days in each month are handled by the date classes

## Getting parts of a date or time

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

```text
2026
10
21
9
30
```

- `getDayOfWeek` returns a `DayOfWeek` value, such as `MONDAY` or `SATURDAY`

```java
import java.time.DayOfWeek;
import java.time.LocalDate;

LocalDate date = LocalDate.of(2026, 10, 21);
DayOfWeek day = date.getDayOfWeek();

System.out.println(day);
System.out.println(day == DayOfWeek.WEDNESDAY);
```

```text
WEDNESDAY
true
```

## Comparing dates and times

- Use `isBefore` and `isAfter` to check which date or time comes first
- Use `equals` to check whether two date/time objects represent the same value
- Do not use `==` to compare date/time values

```java
import java.time.LocalDate;

LocalDate today = LocalDate.of(2026, 10, 21);
LocalDate deadline = LocalDate.of(2026, 11, 1);

if (today.isBefore(deadline)) {
    System.out.println("There is still time before the deadline");
}

System.out.println(today.isAfter(deadline));
System.out.println(today.equals(deadline));
```

```text
There is still time before the deadline
false
false
```

- The same comparison methods are available on `LocalTime` and `LocalDateTime`

## Adding and subtracting time

- Methods such as `plusDays`, `minusMonths`, and `plusHours` calculate a new date or time
- Date and time objects are **immutable**: these methods do not change the original value. They return a new value, which you can store in a variable
- Java handles changes across month ends and leap years

```java
import java.time.LocalDate;

LocalDate startDate = LocalDate.of(2024, 2, 28);
LocalDate nextDay = startDate.plusDays(1);
LocalDate followingDay = nextDay.plusDays(1);
LocalDate nextMonth = startDate.plusMonths(1);

System.out.println(startDate);
System.out.println(nextDay);
System.out.println(followingDay);
System.out.println(nextMonth);
```

```text
2024-02-28
2024-02-29
2024-03-01
2024-03-28
```

- If the target month has fewer days, Java adjusts the result to the last valid day of that month. For example, adding one month to January 31 results in the last day of February
- `LocalTime` supports operations such as `plusMinutes` and `minusHours`. If the result passes midnight, the time wraps around to the next or previous day; `LocalTime` itself does not store that day change

```java
import java.time.LocalTime;

LocalTime startTime = LocalTime.of(23, 50);
LocalTime later = startTime.plusMinutes(20);

System.out.println(later);
```

```text
00:10
```

## Working with a date and a time together

- Use `LocalDateTime` when both the date and the time are needed
- You can create one directly with `of`, or combine an existing `LocalDate` and `LocalTime`
- The `toLocalDate` and `toLocalTime` methods return the date and time parts

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;

LocalDate date = LocalDate.of(2026, 10, 21);
LocalTime time = LocalTime.of(9, 30);
LocalDateTime appointment = LocalDateTime.of(date, time);

System.out.println(appointment);
System.out.println(appointment.toLocalDate());
System.out.println(appointment.toLocalTime());
```

```text
2026-10-21T09:30
2026-10-21
09:30
```

- `LocalDateTime` supports comparisons and calculations such as `isBefore`, `plusDays`, and `minusHours`
- Adding hours to a `LocalDateTime` can change its date when the calculation crosses midnight

## Reading dates and times from text

- User input read with `Scanner.nextLine()` is a string
- Use `parse` to convert text in the standard ISO format into a date or time object
- Standard formats are `yyyy-MM-dd` for a date and `HH:mm` for a time

```java
import java.time.LocalDate;
import java.time.LocalTime;
import java.util.Scanner;

Scanner input = new Scanner(System.in);

System.out.print("Enter a date (yyyy-MM-dd): ");
LocalDate date = LocalDate.parse(input.nextLine());

System.out.print("Enter a time (HH:mm): ");
LocalTime time = LocalTime.parse(input.nextLine());

System.out.println("Date: " + date);
System.out.println("Time: " + time);
```

```text
Enter a date (yyyy-MM-dd): 2026-10-21
Enter a time (HH:mm): 09:30
Date: 2026-10-21
Time: 09:30
```

- The text must use a valid format and represent a valid date or time. Invalid input causes a `DateTimeParseException`
- We will learn how to handle exceptions in a later topic

## Formatting dates and times

- The default format is useful for programs, but a different format may be easier for people to read
- Use a `DateTimeFormatter` to format a date or time as text
- In a format pattern, `dd` means day, `MM` means month, `yyyy` means year, `HH` means hour using a 24-hour clock, and `mm` means minutes
- Uppercase `MM` is for months; lowercase `mm` is for minutes

```java
import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;
import java.time.format.DateTimeFormatter;

DateTimeFormatter dateFormat = DateTimeFormatter.ofPattern("dd.MM.yyyy");
DateTimeFormatter timeFormat = DateTimeFormatter.ofPattern("HH:mm");
DateTimeFormatter appointmentFormat =
        DateTimeFormatter.ofPattern("dd.MM.yyyy HH:mm");

LocalDate date = LocalDate.of(2026, 10, 21);
LocalTime time = LocalTime.of(9, 30);
LocalDateTime appointment = LocalDateTime.of(date, time);

System.out.println(date.format(dateFormat));
System.out.println(time.format(timeFormat));
System.out.println(appointment.format(appointmentFormat));
```

```text
21.10.2026
09:30
21.10.2026 09:30
```

- To parse text in a custom format, create a formatter and pass it to `parse`

```java
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;

DateTimeFormatter dateFormat = DateTimeFormatter.ofPattern("dd.MM.yyyy");
LocalDate date = LocalDate.parse("21.10.2026", dateFormat);

System.out.println(date);
```

```text
2026-10-21
```

## 💡 Date example: finding Midsummer Day

> Midsummer Day is the Saturday between June 20 and June 26. Find the date of Midsummer Day in a given year.

```java
import java.time.DayOfWeek;
import java.time.LocalDate;

int year = 2026;

for (int day = 20; day <= 26; day++) {
    LocalDate date = LocalDate.of(year, 6, day);

    if (date.getDayOfWeek() == DayOfWeek.SATURDAY) {
        System.out.println("Midsummer Day is " + date);
    }
}
```

```text
Midsummer Day is 2026-06-20
```

- The loop checks each possible date, creates a `LocalDate`, and tests its day of the week
- The `DayOfWeek` values are constants, so comparing the result with `==` is appropriate here