# Coding Tasks

# 1. There is an array with every element repeated three times except one. Find that element.
> Answer
```java
public class PickUniqueNumber {

    public static void main(String[] args) {
        int[] Arr = {4, 4, 4, 5, 5, 5, 6, 6, 6, 7, 8, 8, 8};//7
        System.out.println("The unique number of Array is -> "+pickUniqueNum(Arr));
    }

    public static int pickUniqueNum(int[] nums) {
        int a = 0;
        int b = 0;

        for (int n : nums) {
            a = a^n & ~b;
            b = b^n & ~a;
        }

        return a;
    }
}

```

# 2. Given a linked list, swap every i-th and i-th + 2 nodes and return its head.
> Answer
```java
class SwapLinkedList {

    static Node firstNode;

    static class Node {
        int data;
        Node next;

        Node(int d) {
            data = d;
            next = null;
        }

    }

    public static void main(String[] args) {

        /* The linked list is 1->2->3->4 */
        SwapLinkedList list = new SwapLinkedList();
        list.firstNode = new Node(1);
        list.firstNode.next = new Node(2);
        list.firstNode.next.next = new Node(3);
        list.firstNode.next.next.next = new Node(4);

        System.out.println("SwapLinkedList before swapping ");
        list.printList(firstNode);
        Node st = list.swap(firstNode);
        System.out.println("");

        System.out.println("SwapLinkedList after calling pairwiseSwap() ");
        list.printList(st);
        System.out.println("");

    }

    public Node swap(Node firstNode) {
        if ((firstNode == null) || (firstNode.next.next == null))
            return firstNode;
        Node node = firstNode.next.next;
        firstNode.next.next = swap(firstNode.next.next.next.next);
        node.next.next = firstNode;
        return node;
    }

    void printList(Node node) {
        while (node != null) {
            System.out.print(node.data + " ");
            node = node.next;
        }
    }
}
```
