# Solutions: Arrays & Lists Warm-up Exercises

## Warm-up exercise 1

```java
package week5;

public class WarmUp1 {
    public static void main(String[] args) {
        int[] numbers = {2, 9, 5, 1, 7, 4};
        int largest = numbers[0];

        for (int number : numbers) {
            if (number > largest) {
                largest = number;
            }
        }

        System.out.println("Largest number: " + largest);
    }
}
```

## Warm-up exercise 2

```java
package week5;

import java.util.ArrayList;

public class WarmUp2 {
    public static void main(String[] args) {
        ArrayList<String> words = new ArrayList<>();
        words.add("milk");
        words.add("chips");
        words.add("soda");
        words.add("hot dogs");

        String longest = words.get(0);
        for (String word : words) {
            if (word.length() > longest.length()) {
                longest = word;
            }
        }

        System.out.println("Longest word: " + longest);
    }
}
```

## Warm-up exercise 3

```java
package week5;

import java.util.ArrayList;
import java.util.Scanner;

public class WarmUp3 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        ArrayList<Integer> numbers = new ArrayList<>();

        while (true) {
            System.out.print("Enter integer: ");
            String value = input.nextLine();
            if (value.isEmpty()) {
                break;
            }
            numbers.add(Integer.parseInt(value));
        }

        System.out.println("Even integers:");
        for (int number : numbers) {
            if (number % 2 == 0) {
                System.out.println(number);
            }
        }
    }
}
```

This follows the instruction to print even integers. The handout's example includes `1`, which is odd.

## Warm-up exercise 4

```java
package week5;

import java.util.ArrayList;
import java.util.Scanner;

public class WarmUp4 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        ArrayList<String> words = new ArrayList<>();

        while (true) {
            System.out.print("Enter word: ");
            String word = input.nextLine();
            if (word.isEmpty()) {
                break;
            }
            words.add(word);
        }

        System.out.print("Search word: ");
        String searchWord = input.nextLine();
        if (words.contains(searchWord)) {
            System.out.println("The word " + searchWord + " is on the list");
        } else {
            System.out.println("The word " + searchWord + " is not on the list");
        }
    }
}
```