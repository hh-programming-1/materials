# Lesson exercise 1: loops

A little more practice for the lesson.

Printouts:

## Task 1

Create an application that produces the following output (create and test one output at a time!):

```text
3 5 7 9 11 13 15
6 8 11 15 20 26 33
10 11 13 14 17 18 22
```

Don't hardcode your solution; instead, find the rule for printing the numbers in a loop.

## Task 2

Create an application that prints:

```text
9887776666555554444443333333222222221111111110000000000
998776554332110
```

## Task 3

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

## Task 4

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

## Task 5

When paying bills, a reference number is used. The reference number is based on the invoice number, to which the check digit for the reference number is added at the end. Create an application that asks the user for the invoice number (int) and prints the reference number generated from it.

Rules for forming the reference number:

- Multiply the digits of the invoice number from right to left by the weights 7, 3, 1, 7, 3, 1, ...
- Add the resulting numbers together
- Subtract the total from the next full ten. If the difference is 10, the check digit is 0

Example:

- The invoice number is 2020061.
- Multiply the digits and add them together: `2 × 7 + 0 × 1 + 2 × 3 + 0 × 7 + 0 × 1 + 6 × 3 + 1 × 7 = 45`.
- The sum is 45 and the next ten is 50, so the difference is `50 - 45 = 5`.
- The check digit is 5, so the reference number is 20200615.

Solve the problem step by step:

- Read the invoice number from the user.
- In a loop, print one digit at a time from right to left so that you can handle each digit of the invoice number one by one. Here, it is useful to remove the printed digit from the invoice number before the next loop iteration.
- Declare the variables outside the loop:

    ```java
    int weight = 7;
    int sum = 0;
    int checkDigit = 0;
    ```

- While printing the digits one by one from right to left, add the digit multiplied by the weight to the sum
- In each step, change the value of the weight variable from 7 → 3, 3 → 1, and 1 → 7. The weight changes continuously.
- When all digits have been processed, only the check digit calculation remains; this is the key part in figuring out how to find the next full ten.
- Finally, print the invoice number and the check digit to the console

Additionally, you can test with the invoice number 12345, from which the resulting reference number is 123453.