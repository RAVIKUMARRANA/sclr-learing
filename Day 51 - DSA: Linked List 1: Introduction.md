Design and implement a Linked List data structure.
A node in a linked list should have the following attributes - an integer value and a pointer to the next node.


	public static class Node {
       public int data;
       public Node next;

        public Node(int x) {
            data = x;
            next = null;
        }
  }

  static Node head = null;
  public static void insert_node(int position, int value) {
       Node nn=new Node(value);
       Node temp=head;
       if(position==1)
       { 
           nn.next=head;
           head=nn;
       }else{
			       for(int i=1;i<position-1;i++)
			       {
			           temp=temp.next;
			       }
			        nn.next=temp.next;
			        temp.next=nn;
			    }
  }
	
	
	public static void delete_node(int position) {
    if (position == 1) {
            head = head.next;
        } else {
            Node temp = head;
            for (int i = 1; i < position - 1 && temp != null; i++) {
                temp = temp.next;
            }
            if (temp != null && temp.next != null)
                temp.next = temp.next.next;
        }
  }

  public static void print_ll() {
    Node temp = head;
        if(temp==null) return;
        while (temp.next != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.print(temp.data);
  }

 You are given a singly linked list having head node A. You have to reverse the linked list and return the head node of that reversed list.

NOTE: You have to do it in-place and in one-pass.

Reverse Singly-linked list
 /**
 * Definition for singly-linked list.
 * class ListNode {
 *     public int val;
 *     public ListNode next;
 *     ListNode(int x) { val = x; next = null; }
 * }
 */
public class Solution {
    public ListNode reverseList(ListNode A) {
        ListNode prev = null;
        ListNode current = A;
        ListNode nextNode = null ;
        while(current != null){
            nextNode = current.next;
            current.next = prev;
            prev = current;
            current = nextNode;
           
        }
        return prev;
    }
}

Given a singly linked list A, determine if it's a palindrome. Return 1 or 0, denoting if it's a palindrome or not, respectively.

public class Solution {
    public int lPalin(ListNode A) {

        if(A.next == null){ return 1;}

        ListNode slow = A;
        ListNode fast = A;

        while(fast.next != null && fast.next.next != null){
            slow = slow.next;
            fast = fast.next.next;
        }

        ListNode prev=null;
        ListNode temp=slow.next;
        while(temp!=null)
        {
            ListNode nn=temp.next;
            temp.next=prev;
            prev=temp;
            temp=nn;
        }

        while(prev != null && A != null){
            if(prev.val != A.val){
                return 0;
            }
            prev=prev.next;
            A = A.next;
        }
        return 1;
    }
}
