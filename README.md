# AddTwoNums
The Problem Is Solved By Dummy Node Approach

class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
    }
}

public class AddTwoNums {
    public static ListNode addTwoNums(ListNode l1, ListNode l2) {
        // Create a dummy node to act as the starting point
        ListNode dummy = new ListNode(0);
        ListNode current = dummy; // Pointer to build the new list
        int carry = 0; // To store carry value

        // Traverse both lists until both are null
        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry; // Start with the carry

            // Add values from l1 and l2 if they exist
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }

            // Update carry for next iteration
            carry = sum / 10;

            // Create a new node for the digit and move the pointer
            current.next = new ListNode(sum % 10);
            current = current.next;
        }

        // Return the next node after dummy (the actual result)
        return dummy.next;
    }

    public static void printList(ListNode node) {
        while (node != null) {
            System.out.print(node.val + " -> ");
            node = node.next;
        }
        System.out.println("null");
    }

    public static void main(String[] args) {
        // Create the first number: 2 -> 4 -> 3 (represents 342)
        ListNode l1 = new ListNode(2);
        l1.next = new ListNode(4);
        l1.next.next = new ListNode(3);

        // Create the second number: 5 -> 6 -> 4 (represents 465)
        ListNode l2 = new ListNode(5);
        l2.next = new ListNode(6);
        l2.next.next = new ListNode(4);

        // Add the two numbers
        ListNode result = addTwoNums(l1, l2);

        // Print the result
        System.out.print("Result: ");
        printList(result); // Output: 7 -> 0 -> 8 -> null (represents 807)
    }
}
