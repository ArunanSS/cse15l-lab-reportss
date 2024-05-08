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

### Part 2

1. Finding files by name:

Command:
<img width="322" alt="M" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/958f6924-6a6f-4de4-b3b9-cb751deef75b">

Output:
<img width="400" alt="" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/241bb262-2a36-4603-b370-7cb2dc343e0f">

Command: 
<img width="338" alt="Screenshot 2024-05-08 at 2 37 13 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/68a59d50-0129-40af-8e88-3c7e499fb93b">

Output:
<img width="312" alt="Screenshot 2024-05-08 at 2 37 31 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/01dff107-d53a-497c-b134-5f945dbd9819">

Source: "https://www.redhat.com/sysadmin/linux-find-command"


2. Finding directories

Command:
<img width="264" alt="" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/89f72ee8-ec82-440b-ad3b-75912c7fdda7">

Output:
<img width="216" alt="" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/9d3f7657-efda-4909-8ec9-ee8ff2650b64">

Command:
<img width="275" alt="Screenshot 2024-05-08 at 2 38 25 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/e021d4db-1d46-4f84-8a44-8d07de2706c0">


Output:
<img width="255" alt="Screenshot 2024-05-08 at 2 38 35 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/1b033a48-0c0b-4874-814f-11ef80b1d7dd">


Source: "https://www.cyberciti.biz/faq/howto-find-a-directory-linux-command/#:~:text=cards%20as%20follows%3A-,find%20%2F%20%2Dtype%20d%20%2Dname%20%22project.,type%20d%20%2Dname%20%22project."


3. This is for finding files based on size

Command:
<img width="333" alt="" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/df629d69-af2d-4d4c-a265-0af181904531">

Output:
<img width="322" alt="" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/d0f93744-2815-4934-91f0-3e53e26e12cb">

Command:
<img width="315" alt="Screenshot 2024-05-08 at 2 39 37 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/7360e58b-e071-46af-a7e1-b57cceda1d77">


Output:
<img width="389" alt="Screenshot 2024-05-08 at 2 39 47 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/7b332cff-6105-4a98-b675-c00647700503">


Source: "https://linuxconfig.org/how-to-use-find-command-to-search-for-files-based-on-file-size"

4. Finding files modified within days

Command: 
<img width="403" alt="" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/f63b3a0a-6b91-4776-94d4-47dd86675576">

Output:
<img width="404" alt="" src="https://github.com/ArunanSS/cse15l-lab-reports/assets/83483462/6f1108ee-d375-49c7-b89d-f8fe98eb7390">

Command:
<img width="331" alt="Screenshot 2024-05-08 at 2 40 44 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/894ac133-e893-4d6d-a5a3-0b4282ab2721">


Output: 
<img width="573" alt="Screenshot 2024-05-08 at 2 40 55 PM" src="https://github.com/ArunanSS/cse15l-lab-reportss/assets/83483462/b1aed2f3-0534-4e9d-a5ec-83e047e1f974">


Sources: "https://www.baeldung.com/linux/recently-changed-files"



How ChatGPT was used to help this: 

Prompt: What are some command line operations that I can use in linux and i inputed the examples that we had 

Output: It gave a variety of operations, but I chose find

Prompt: What are some of the command line operations that can be used with examples

Output: I was shown about 20 different examples, chose the ones to use then modified them into how they should work

Prompt: Can you explain how these outputs work in a simple way

Output: I was show how the outputs work to overall get a better understanding of it



