# Solutions: Methods Warm-up Exercises

## Warm-up exercise 1

```java
package week6;

import java.util.Scanner;

public class WarmUp1 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter word: ");
        String word = input.nextLine();

        if (isPalindrome(word)) {
            System.out.println("The word is a palindrome");
        } else {
            System.out.println("The word is not a palindrome");
        }
    }

    public static boolean isPalindrome(String word) {
        for (int left = 0, right = word.length() - 1; left < right; left++, right--) {
            if (word.charAt(left) != word.charAt(right)) {
                return false;
            }
        }
        return true;
    }
}
```

## Warm-up exercise 2

```java
package week6;

import java.util.Scanner;

public class WarmUp2 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Enter skier's height: ");
        int skierHeight = Integer.parseInt(input.nextLine());
        int poleLength = calculatePoleLength(skierHeight);
        int skiLength = calculateSkiLength(poleLength);

        System.out.println("Pole length: " + poleLength + "cm");
        System.out.println("Ski length: " + skiLength + "cm");
    }

    public static int calculatePoleLength(int skierHeight) {
        double length = skierHeight * 0.85;
        int roundedLength = roundToNearestFive(length);
        return roundedLength;
    }

    public static int calculateSkiLength(int poleLength) {
        return poleLength + 40;
    }

    public static int roundToNearestFive(double value) {
        return (int) Math.round(value / 5) * 5;
    }
}
```