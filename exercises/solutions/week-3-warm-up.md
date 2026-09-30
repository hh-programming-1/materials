# Solutions: Loops Warm-up Exercises

## Warm-up exercise 1

```java
package week3;

public class WarmUp1 {
    public static void main(String[] args) {
        for (int number = 3; number <= 15; number += 2) {
            System.out.print(number + " ");
        }
        System.out.println();

        for (int number = 6; number <= 24; number += 3) {
            System.out.print(number + " ");
        }
        System.out.println();

        for (int number = 12; number >= 0; number -= 2) {
            System.out.print(number + " ");
        }
        System.out.println();
    }
}
```

## Warm-up exercise 2

```java
package week3;

public class WarmUp2 {
    int rows = 5;
    int columns = 5;

    public static void main(String[] args) {
        for (int row = 0; row < rows; row++) {
            for (int column = 0; column < columns; column++) {
                if (row == rows - 1 || column == 0 || column == columns - 1) {
                    System.out.print("#");
                } else {
                    System.out.print("-");
                }
            }
            System.out.println();
        }
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
        String invoiceNumber = input.nextLine();
        String[] digits = invoiceNumber.split("");
        int weight = 7;
        int sum = 0;
        int checkDigit = 0;

        for (int index = digits.length - 1; index >= 0; index--) {
            int currentDigit = Integer.parseInt(digits[index]);
            sum += currentDigit * weight;

            if (weight == 7) {
                weight = 3;
            } else if (weight == 3) {
                weight = 1;
            } else {
                weight = 7;
            }
        }

        checkDigit = (10 - sum % 10) % 10;
        System.out.println("Reference number is " + invoiceNumber + checkDigit);
    }
}
```