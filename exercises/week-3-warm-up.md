# Loops Warm-up Exercises

For this week's exercises, create a new `week3` package (folder) under the `src/main/java` folder. For each exercise, create an exercise-specific `.java` file in the `week3` folder.

```
src/
└── main/
    └── java/
        ├── ...
        └── week3/ 👈
            └── WarmUp1.java 👈
```

> [!IMPORTANT]
> **Warm-up exercises are not submitted or evaluated in Viope**. The purpose of these exercises is to practice the topics with the help of the model solutions.

## Warm-up exercise 1

Using loops, create an application that prints the following:

```text
3 5 7 9 11 13 15
6 9 12 15 18 21 24
12 10 8 6 4 2 0
```

Don't hardcode your solution; instead, find the rule for printing the numbers in a loop.

> [!TIP]
> Consider printing each row of numbers using an separate loop.

## Warm-up exercise 2

Using loops, create an application that prints the following:

```
#---#
#---#
#---#
#---#
#####
```

Don't hardcode your solution; instead, find the rule for printing the symbols in a loop.

> [!TIP]
> Having outer loop going through the rows and inner loop going through the columns might be useful.

## Warm-up exercise 3

What does the following program print to the console?

```java
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
```

Try to determine the output without using VS Code first, and then confirm that your reasoning is correct.

## Warm-up exercise 4

Create an application that asks for the height of the triangle, and when the value is zero or less, it stops asking. Print the triangle to the console according to the example.

Example output:

```text
Enter triangle height: 4
*
**
***
****
```

Let us correct the triangle printing as follows: instead of a right triangle, print an isosceles triangle.

Example output:

```text
Enter triangle height: 4
   *
  ***
 *****
*******
```

## Warm-up exercise 5

When paying bills, a reference number is used. The reference number is based on the invoice number, to which the check digit for the reference number is added at the end. Create an application that asks the user for the invoice number and prints the reference number generated from it.

Rules for forming the reference number:

- Multiply the digits of the invoice number from right to left by the weights 7, 3, 1, 7, 3, 1, ...
- Add the resulting numbers together.
- Subtract the total from the next full ten. If the difference is 10, the check digit is 0.

Use the following code as a starting point for the `main` method:

```java
Scanner input = new Scanner(System.in);
System.out.print("Enter invoice number: ");
String invoiceNumber = input.nextLine();
// digits is an array containing each invoice number digit, e.g. "123" => {"1", "2", "3"}
String[] digits = invoiceNumber.split("");
int weight = 7;
int sum = 0;
int checkDigit = 0;

for (/* iterate the digits array from the end index to the beginning index */) {
    int currentDigit = Integer.parseInt(digits[i]);
    // Increase the sum
}

// Calculate the check digit and print the reference number
```

Example:

- The invoice number is 2020061.
- Multiply the digits and add them together: `2 × 7 + 0 × 1 + 2 × 3 + 0 × 7 + 0 × 1 + 6 × 3 + 1 × 7 = 45`.
- The sum is 45 and the next ten is 50, so the difference is `50 - 45 = 5`.
- The check digit is 5, so the reference number is 20200615.

Solve the problem step by step:

- Read the invoice number from the user.
- In a loop, print one digit at a time from right to left so that you can handle each digit of the invoice number one by one.
- While printing the digits one by one from right to left, add the digit multiplied by the weight to the sum.
- In each step, change the value of the weight variable from 7 → 3, 3 → 1, and 1 → 7. The weight changes continuously.
- When all digits have been processed, only the check digit calculation remains; this is the key part in figuring out how to find the next full ten.
- Finally, print the invoice number and the check digit to the console.

Example outputs:

```text
Enter invoice number: 2020061
Reference number is 20200615
```

```text
Enter invoice number: 12345
Reference number is 123453
```

> [!IMPORTANT]
> Once you have completed these warm-up exercises, check the model solutions in Moodle's "Schedule" page.
