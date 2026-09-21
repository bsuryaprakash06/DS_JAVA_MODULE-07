# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE: 17-08-2024

## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Create a dummy node and set its next pointer to the head of the linked list.
2. Initialize a current pointer pointing to the dummy node.
3. Traverse the list. If `current.next.val` equals the target value, set `current.next` to `current.next.next` to skip the node.
4. If the value does not match, move the current pointer to the next node.
5. Continue until the end of the list and return `dummy.next` as the new head.

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

## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
