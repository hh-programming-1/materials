# Solutions: Loops Warm-up Exercises

## Warm-up exercise 1

```java
package week3;

public class WarmUp1 {
    public static void main(String[] args) {
        for (int number = 3; number <= 15; number += 2) {
            printNumber(number, number == 15);
        }
        System.out.println();

        int number = 6;
        for (int index = 0; index < 7; index++) {
            printNumber(number, index == 6);
            number += index + 2;
        }
        System.out.println();

        number = 10;
        for (int index = 0; index < 7; index++) {
            printNumber(number, index == 6);
            if (index % 2 == 0) {
                number += 1;
            } else {
                number += index / 2 + 2;
            }
        }
        System.out.println();
    }

    private static void printNumber(int number, boolean last) {
        System.out.print(number);
        if (!last) {
            System.out.print(" ");
        }
    }
}
```

## Warm-up exercise 2

```java
package week3;

public class WarmUp2 {
    public static void main(String[] args) {
        for (int digit = 9; digit >= 0; digit--) {
            int repetitions = 10 - digit;
            for (int count = 0; count < repetitions; count++) {
                System.out.print(digit);
            }
        }
        System.out.println();

        for (int digit = 9; digit >= 0; digit--) {
            int repetitions = digit % 2 == 1 ? 2 : 1;
            for (int count = 0; count < repetitions; count++) {
                System.out.print(digit);
            }
        }
        System.out.println();
    }
}
```

## Warm-up exercise 3

The method prints ten lines. Each line has an increasing number of stars on both sides, with the spaces between them decreasing to zero.

```java
package week3;

public class WarmUp3 {
    public static void main(String[] args) {
        stars();
    }

    public static void stars() {
        for (int i = 1; i <= 10; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            for (int j = 1; j <= 20 - 2 * i; j++) {
                System.out.print(" ");
            }
            for (int j = 0; j < i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

## Warm-up exercise 4

This version prints the final, isosceles-triangle variation and keeps asking for heights until the user enters zero or a negative number.

```java
package week3;

import java.util.Scanner;

public class WarmUp4 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        while (true) {
            System.out.print("Enter triangle height: ");
            int height = Integer.parseInt(input.nextLine());
            if (height <= 0) {
                break;
            }

            for (int row = 1; row <= height; row++) {
                for (int space = 0; space < height - row; space++) {
                    System.out.print(" ");
                }
                for (int star = 0; star < 2 * row - 1; star++) {
                    System.out.print("*");
                }
                System.out.println();
            }
        }
    }
}
```

## Warm-up exercise 5

```java
package week3;

import java.util.Scanner;

public class WarmUp5 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter invoice number: ");
        int invoiceNumber = Integer.parseInt(input.nextLine());
        int remainingDigits = invoiceNumber;
        int weight = 7;
        int sum = 0;

        while (remainingDigits > 0) {
            int digit = remainingDigits % 10;
            sum += digit * weight;
            remainingDigits /= 10;

            if (weight == 7) {
                weight = 3;
            } else if (weight == 3) {
                weight = 1;
            } else {
                weight = 7;
            }
        }

        int checkDigit = (10 - sum % 10) % 10;
        System.out.println("Reference number: " + invoiceNumber + checkDigit);
    }
}
```