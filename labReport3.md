# Lab Report 3
## **Arunachalam Senthil**


### Part 1
Bug Chosen: averageWithoutLowest

## This is the failure inducing Input

```java
public void testAverageWithoutLowest() {
    int[] numbers = {5, 2, 7, 3, 8};
    assertEquals(4.75, ArrayMethods.averageWithoutLowest(numbers), 0.001);
}
```

## This is the one that doesn't induce a failure
```java
public void testAverageWithoutLowestNoChange() {
    int[] numbers = {2, 4, 6, 8, 10};
    assertEquals(6.0, ArrayMethods.averageWithoutLowest(numbers), 0.001);
}
```

##  Symptom, as the output of running the tests

<img width="1133" alt="Fun" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/449e8611-5e59-44b8-8a98-50d84a384a2b">


## Before Fix

```java
public static double averageWithoutLowest(int[] numbers) {
    if (numbers.length < 2) {
        throw new IllegalArgumentException("Array length must be at least 2");
    }

    int lowest = numbers[0];
    int sum = 0;

    for (int number : numbers) {
        sum += number;

        if (number < lowest) {
            lowest = number;
        }
    }

    return (double) (sum - lowest) / (numbers.length - 1);
}
```

## After Fix

```java
public static double averageWithoutLowest(int[] numbers) {
    if (numbers.length < 2) {
        throw new IllegalArgumentException("Array length must be at least 2");
    }

    int sum = 0;

    for (int number : numbers) {
        sum += number;
    }

    int lowest = Arrays.stream(numbers).min().orElseThrow();

    return (double) (sum - lowest) / (numbers.length - 1);
}
```

## Brief Explanation
This method's lowest value calculation had a problemn at first. What I did to solve this is first  the least value in the array is found using an improper array issue, and this makes it into a better  computation without lowest value.


