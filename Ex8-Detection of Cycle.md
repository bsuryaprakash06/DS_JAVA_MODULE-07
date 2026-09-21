# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE: 21-08-2024

## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.

## Algorithm
1. Initialize two pointers, slow and fast, both pointing to the head of the linked list.
2. Traverse the list, moving the slow pointer by one step and the fast pointer by two steps.
3. If the slow and fast pointers meet, a cycle is detected.
4. To find the starting node of the cycle, reset the slow pointer to the head and move both pointers by one step until they meet.
5. If the fast pointer reaches the end of the list (null), return null indicating no cycle exists.

## Program:
```java
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: Surya Prakash B
RegisterNumber: 212224230281
*/

import java.util.Scanner;

public class DetectLoopFloyd {
    public static boolean hasLoop(Node head) {
       Node slow=head;
       Node fast = head;
       while (fast != null && fast.next !=null){
           slow = slow.next;
           fast=fast.next.next;
           
           if(slow == fast){
               return true;
           }
       }
       return false;
       
       
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Node head = null, tail = null;

        int n = scanner.nextInt();

        for (int i = 0; i < n; i++) {
            Node newNode = new Node(scanner.nextInt());
            if (head == null) {
                head = tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }

      
        int pos = scanner.nextInt();

        if (pos > 0) {
            Node loopNode = head;
            for (int i = 1; i < pos && loopNode != null; i++) {
                loopNode = loopNode.next;
            }
            if (loopNode != null) {
                tail.next = loopNode;
            }
        }

        if (hasLoop(head)) {
            System.out.println("Loop detected in the LinkedList.");
        } else {
            System.out.println("No loop detected in the LinkedList.");
        }

        scanner.close();
    }
}

class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}
```

## Output:
![alt text](Output-Images/{A42D809D-A6BA-4773-8434-9690CAF331B4}.png)

## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
