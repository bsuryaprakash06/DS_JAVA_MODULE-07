# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE: 14-08-2024

## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.

## Algorithm
1. Initialize a boolean array `visited` of the same length as the input array `nums` to keep track of visited elements.
2. Initialize a variable `maxLength` to 0 to store the maximum size of the sets.
3. Iterate over each element in `nums`. If the element has not been visited, start a new set.
4. Follow the permutation `nums[k]`, marking elements as visited and counting the size of the set until a cycle is formed (an already visited element is reached).
5. Update `maxLength` with the maximum size found and return it after checking all elements.

## Program:
```java
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: Surya Prakash B
RegisterNumber: 212224230281
*/

import java.util.Scanner;

class LongestSet {

    public static int longestSetLength(int[] nums) {
        boolean[] visited = new boolean[nums.length];
        int maxLength = 0;

        for (int i = 0; i < nums.length; i++) {
            if (!visited[i]) {
                int count = 0;
                int current = i;

                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    count++;
                }

                maxLength = Math.max(maxLength, count);
            }
        }

        return maxLength;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int[] nums = new int[n];

      
        System.out.println("Enter " + n + " elements:");
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int result = longestSetLength(nums);
        System.out.println("Maximum size of S[k] = " + result);

        sc.close();
    }
}
```

## Output:

## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
