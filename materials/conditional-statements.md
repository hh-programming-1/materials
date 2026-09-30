# Conditional statements

## Control statements

- By default the statements on a program are executed one statement at a time from the first line to the last line of the program
- **Control statements** are programming statements that control the order in which statements are executed in a program
- The most common categorization of control statements includes **conditional statements** (make decisions whether to execute certain statements), **loops** (repeating statements) and **jump statements** (changing the execution flow by e.g. returning from a method call)

## Conditional statements

- The most common conditional statement is the `if` statement
- The `if` statement specifies a **condition** for executing specific statements within a code block defined by `{}` brackets
- The condition **must evaluate to either true or false** and is commonly constructed using comparison (e.g. `<`) and logical operators (e.g. `&&`)

```java
int grade = 3;

// If grade variable's value is 5, the if block is executed
if (grade == 5) {
  System.out.println("That is the best possible grade!");
}

System.out.println("Good bye!");
```

```
Good bye!
```

## If statement

- The `if` statement can optionally be followed by a `else` statement, providing statements to be executed if the condition is not met

```java
int grade = 3;

if (number == 5) {
  System.out.println("That is the best possible grade!");
} else {
  // This block is executed if the condition is not met
  System.out.print("That is not the best possible grade");
}

System.out.println("Good bye!");
```

```
That is not the best possible grade
Good bye!
```

## Chaining conditions in the if statement

- In case the `if` statements condition is not met, we can provide additional conditions to check using the `if else` statement

```java
int grade = 3

if (number == 1) {
  System.out.println("That is a failing grade");
  // If the previous condition was not met, the next else if condition will be checked
} else if (grade < 3) {
  System.out.println("That grade is not so great");
} else if (grade < 5) {
  System.out.println("That is a pretty good grade");
} else {
  System.out.println("That is an awesome grade!");
}

System.out.println("Good bye!");
```

```
That is a pretty good grade
Good bye!
```

## Comparison operators

- The **comparison operators** are used to compare two values, e.g. checking if variable has certain value

| Operator | Description              | Example   |
| -------- | ------------------------ | --------- |
| `==`     | Equal to                 | `x == 10` |
| `!=`     | Not equal to             | `x != 10` |
| `>`      | Greater than             | `x > 10`  |
| `<`      | Less than                | `x < 10`  |
| `>=`     | Greater than or equal to | `x >= 10` |
| `<=`     | Less than or equal to    | `x <= 10` |

## Logical operators

- The **logical operators** are used to combine conditions e.g. "number is larger than zero AND number is less than ten"

| Operator | Description                                    | Example                  |
| -------- | ---------------------------------------------- | ------------------------ |
| `&&`     | And, both conditions must be true              | `age >= 18 && age <= 65` |
| `\|\|`   | Or, one of the conditions must be true         | `day == 6 \|\| day == 7` |
| `!`      | Not, true becomes false and false becomes true | `!isReady`               |

> [!TIP]
> The `||` or operator can be written with the <kbd>alt gr</kbd> + <kbd>< ></kbd> key combination.

## Conditional statement example: temperature description

> _"Write a program that asks for the temperature. If temperature is less than 0°C, the program prints "It is freezing", if it is less than 20°C it prints "It is cool" and otherwise it prints "It is warm"._

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    System.out.print("Enter the temperature: ");
    int temperature = Integer.parseInt(input.nextLine());

    if (temperature < 0) {
        System.out.println("It is freezing");
    } else if (temperature < 20) {
        System.out.println("It is cool");
    } else {
        System.out.println("It is warm");
    }
}
```

## Conditional statement example: comission calculation

> _"Write a program that asks for the selling price of an apartment and calculates the real estate agent's commission for the sale. The commission is 3.44% of the selling price, but at least €2,214."_

```java
public static void main(String[] args) {
    double commissionRate = 0.0344; // 3.44%
    double minimumCommission = 2214.00;

    Scanner input = new Scanner(System.in);
    DecimalFormat twoDecimals = new DecimalFormat("0.00");

    System.out.print("Enter selling price: ");
    double sellingPrice = Double.parseDouble(input.nextLine());

    double commission = sellingPrice * commissionRate;

    if (commission < minimumCommission) {
        commission = minimumCommission;
    }

    System.out.println("The sales commission is " + twoDecimals.format(commission));
}
```

## Switch statement

- A `switch` statement allows a program to choose between multiple blocks of code based on the value of a variable or expression

```java
int day = 5;

// Switch specifies the value we want to check, day variable in this case
switch (day) {
    // Case specifies a value to match against the switch expression
    case 1:
        // This case is selected when the value of the switch expression matches 1
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    case 4:
        System.out.println("Thursday");
        break;
    case 5:
        System.out.println("Friday");
        break;
    // It is possible to specify multiple values in the same case
    case 6, 7:
        System.out.println("Weekend");
        break;
    // Default case is selected when no other case matches the switch expression
    default:
        System.out.println("Invalid day");
}
```

## Switch statement example: grade description

> _"Write a program which asks for a grade (0-5) and prints its description ("Weak" for 0, "Satisfactory" for 2, "Good" for 4 or 3, and "Excellent" for 5). If the grade is not within 0-5 range, the program should print "Invalid grade"."_

```java
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);

    System.out.print("Enter a grade (0-5): ");
    int grade = Integer.parseInt(input.nextLine());

    switch (grade) {
        case 5:
            System.out.println("Excellent");
            break;
        case 4, 3:
            System.out.println("Good");
            break;
        case 2:
            System.out.println("Satisfactory");
            break;
        case 1:
            System.out.println("Weak");
            break;
        default:
            System.out.println("Invalid grade");
            break;
    }
}
```

## The ternary operator

$$
\underbrace{\texttt{String description =}}_{\text{variable declaration and assignment}}
\underbrace{\texttt{age >= 18}}_{\text{condition}}
\ \texttt{?}\
\underbrace{\texttt{"Adult"}}_{\text{value if true}}
\ \texttt{:}\
\underbrace{\texttt{"Minor"}}_{\text{value if false}}
\texttt{;}
$$

- The `?` operator can be used to assign a value based on a condition
- The condition is written before the `?` symbol. The value before the `:` is returned if the condition is true, while the value after the : is returned if the condition is false
- It is commonly used to replace simple `if` statements

```java
int age = 20;

if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

```java
int age = 20;
// If age >= 18, description variable's value will be "Adult", otherwise "Minor"
String description = age >= 18 ? "Adult" : "Minor";

System.out.println(description);
```
