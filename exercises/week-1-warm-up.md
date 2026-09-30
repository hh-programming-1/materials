# Java Basics Warm-up Exercises

The purpose of these exercises is to familiarize yourself with basics of Java and executing Java programs. You can apply the JavaScript syntax presented in the previous course with the following differences:

- You should write your own Java code within the `main` method in the program class.
- Use `System.out.println` instead of `console.log` to print to the console window. For example, `System.out.println("Hello!");`
- To define a variable, use the keyword `int` instead of `var` or `let`. For example, `int x = 0;`
- Create an array of integers as follows `int[] someNumbers = {1, 2, 6, 9};`

> [!IMPORTANT]
> These exercises are not submitted, but necessary for learning how to write and execute Java programs.

## Warm-up exercise 1

In the Java project you worked with previously, add a `WarmUp1.java` file in the `week1` folder with a `WarmUp1` class and a `main` method.

```
src/
└── main/
    └── java/
        └── week1/
            ├── HelloProgram.java
            └── WarmUp1.java 👈
```

> [!TIP]
> In VS Code, right-click on the `week1` folder and choose "New file". Name the file `WarmUp1.java` and press `Enter`. VS Code will automatically write the `WarmUp1` class for you.

In the `main` method, implement a program that prints your name.

> [!TIP]
> Writing "sout" and pressing the `Tab` key will automatically write `System.out.println();` in VS Code. This is just one among many autocomplete features of VS Code.

## Warm-up exercise 2

Add a `WarmUp2.java` file in the `week1` folder with a `WarmUp2` class and a `main` method.

Implement a program that prints the numbers from 1 to 10, each on a new line.

> [!IMPORTANT]
> Proper formatting is essential for the readability of the code. Use the <kbd>shift</kbd> + <kbd>alt</kbd> + <kbd>f</kbd> keyboard shortcut in VS Code to automatically format your code.

> [!TIP]
> Use a [for loop](https://www.w3schools.com/Java/java_for_loop.asp) to iterate through the integers and the System.out.println method to display each number.

## Warm-up exercise 3

Add a `WarmUp3.java` file in the `week1` folder with a `WarmUp3` class and a `main` method.

Implement a program that prints **even** numbers from 2 to 20. If the number is 10, the program should print "Ten" instead of the number.

> [!TIP]
> Use a single `for` loop to iterate through the numbers and an [if-else](https://www.w3schools.com/java/java_conditions.asp) statement to handle the special case for the number 10.

## Warm-up exercise 4

Add a `WarmUp4.java` file in the `week1` folder with a `WarmUp4` class and a `main` method.

Using the following `main` method as a template, implement that calculates and prints the sum of all integers in the `points` array.

```java
public static void main(String[] args) {
    int[] points = {1, 2, 3, 16, 20};
    // Write your code here
}
```

> [!TIP]
> Use a `for` loop to iterate through the array.