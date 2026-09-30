# Solutions: Java Basics Warm-up Exercises

## Warm-up exercise 1

```java
package week1;

public class WarmUp1 {
    public static void main(String[] args) {
        System.out.println("John Doe");
    }
}
```

Replace `"John Doe"` with your own name.

## Warm-up exercise 2

```java
package week1;

public class WarmUp2 {
    public static void main(String[] args) {
        for (int number = 1; number <= 10; number++) {
            System.out.println(number);
        }
    }
}
```

## Warm-up exercise 3

```java
package week1;

public class WarmUp3 {
    public static void main(String[] args) {
        for (int number = 2; number <= 20; number += 2) {
            if (number == 10) {
                System.out.println("Ten");
            } else {
                System.out.println(number);
            }
        }
    }
}
```

## Warm-up exercise 4

```java
package week1;

public class WarmUp4 {
    public static void main(String[] args) {
        int[] points = {1, 2, 3, 16, 20};
        int sum = 0;

        for (int point : points) {
            sum += point;
        }

        System.out.println(sum);
    }
}
```