# Solutions: Conditional Statements Warm-up Exercises

## Warm-up exercise 1

```java
package week2;

import java.util.Scanner;

public class WarmUp2 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter your age: ");
        int age = Integer.parseInt(input.nextLine());

        if (age < 0 || age > 120) {
            System.out.println("Your age is invalid");
        } if (age >= 18) {
            System.out.println("You are an adult");
        } else {
            System.out.println("You are a minor");
        }
    }
}
```

## Warm-up exercise 2

```java
package week2;

import java.util.Scanner;

public class WarmUp2 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Do you want to proceed: ");
        String value = input.nextLine();

        if (value.equals("yes") || value.equals("ok")) {
            System.out.println("Proceeding");
        } else {
            System.out.println("Cancelling");
        }
    }
}
```

## Warm-up exercise 3

```java
package week2;

import java.util.Scanner;

public class WarmUp3 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter hours (1-24): ");
        int hours = Integer.parseInt(input.nextLine());
        System.out.print("Enter minutes (0-59): ");
        int minutes = Integer.parseInt(input.nextLine());

        if (hours >= 1 && hours <= 24 && minutes >= 0 && minutes <= 59) {
            System.out.println("The time is " + hours + ":" + minutes);
        } else {
            System.out.println("That time is invalid");
        }
    }
}
```

## Warm-up exercise 4

```java
package week2;

import java.util.Scanner;

public class WarmUp4 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter your score: ");
        int score = Integer.parseInt(input.nextLine());
        String grade;

        if (score < 0 || score > 100) {
            System.out.println("That score is invalid");
            return;
        } else if (score >= 90) {
            grade = "A";
        } else if (score >= 80) {
            grade = "B";
        } else if (score >= 70) {
            grade = "C";
        } else if (score >= 60) {
            grade = "D";
        } else {
            grade = "F";
        }

        System.out.println("Your grade is " + grade);
    }
}
```
