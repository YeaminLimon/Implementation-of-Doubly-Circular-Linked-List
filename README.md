# YeaminLimon.Implementation-of-Doubly-Circular-Linked-List

import java.util.Scanner;
class Node{
	int data;
	Node next;
	Node prev;
}
class linkedList{
	Node start;
	linkedList(){
		start = null;
	}
	Node getNode() {
		Node newnode = new Node();
		Scanner  input = new Scanner(System.in);
		System.out.println("Enter the data");
		newnode.data = input.nextInt();
		newnode.next = null;
		newnode.prev=null;
		return newnode;
	}
	void insertAtStart() {
		Node newnode = getNode();
		if(start == null) {
			start = newnode;
			newnode.prev=start;
			newnode.next=start;
		}
		else {
			newnode.next = start;
			newnode.prev = start.prev;
			start.prev = newnode;
			start = newnode;
		}
	}
	void insertAtMiddle() {
		Node newnode = getNode();
		if(start == null) {
			start = newnode;
		}
		else {
			System.out.println("Enter the position you insert the node");
			Scanner  input = new Scanner(System.in);
			int position = input.nextInt();
			int nodeCounter = nodeCounter();
			if(position>1 & position <=nodeCounter) {
				int c = 1;
				Node temp = start;
				while(c < position-1) {
					temp = temp.next;
					c++;
				}
				newnode.next = temp.next;
				newnode.prev = temp;
				temp.next.prev = newnode;
				temp.next = newnode;
			}
			else {
				System.out.println("The position you entered is not a middle position");
			}
		}
	}
	void insertAtEnd() {
		Node newnode = getNode();
		if(start == null) {
			start = newnode;
			newnode.prev=start;
			newnode.next=start;
		}
		else {
			newnode.next = start;
			newnode.prev = start.prev;
			start.prev.next = newnode;
			start.prev = newnode;
		}
	}
	void deleteStartNode() {
		if(start == null) {
			System.out.println("The list is empty");
		}
		else {
			start = start.next;
			start.next.prev = start.prev;
		}
	}
	void deleteMiddleNode() {
		if(start == null) {
			System.out.println("The list is empty");
		}
		else {
			System.out.println("Enter the position you delete the node");
			Scanner  input = new Scanner(System.in);
			int position = input.nextInt();
			int nodeCounter = nodeCounter();
			if(position>1 & position <=nodeCounter) {
				int c = 1;
				Node temp = start;
				while(c < position-1) {
					temp = temp.next;
					c++;
				}
				temp.next.next.prev = temp;
				temp.next = temp.next.next;
			}
			else {
				System.out.println("The position you entered is not a middle position");
			}
		}
	}
	void deleteEndNode() {
		if(start == null) {
			System.out.println("The list is empty");
		}
		else {
			
			start.prev.prev.next = start;
			start.prev = start.prev.prev;
		}
	}
	void traverseList() {
		if(start == null) {
			System.out.println("The list is empty");
		}
	    else {
		Node temp = start;
		System.out.print(temp.data+"-->");
		temp = temp.next;
		while(temp!=start) {
			System.out.print(temp.data+"-->");
			temp = temp.next;
		}
	}
	}
	int nodeCounter() {
		Node temp = start;
		int ctr = 1;
		while(temp.next!=start) {
			temp = temp.next;
			ctr++;
		}
		return ctr;
	}
}
public class A1 {

	public static void main(String[] args) {
		linkedList list = new linkedList();
		list.insertAtStart();
		list.insertAtStart();
		list.insertAtStart();
		list.insertAtStart();
		System.out.println("Before inserting at the beginning");
		list.traverseList();
		list.insertAtStart();
		System.out.println("After inserting at the beginning");
		list.traverseList();
		System.out.println("\nBefore inserting at the middle");
		list.traverseList();
		list.insertAtMiddle();
		System.out.println("After inserting at the middle");
		list.traverseList();
		System.out.println("\nBefore inserting at the end");
		list.traverseList();
		list.insertAtEnd();
	            System.out.println("After inserting at the end");
		list.traverseList();
		System.out.println("\nBefore deleting at the beginning");
		list.traverseList();
		list.deleteStartNode();
		System.out.println("After deleting at the beginning");
		list.traverseList();
		System.out.println("\nBefore deleting at the middle");
		list.traverseList();
		list.deleteMiddleNode();
		System.out.println("After deleting at the middle");
		list.traverseList();
		System.out.println("\nBefore deleting at the end");
		list.traverseList();
		list.deleteEndNode();
		System.out.println("After deleting at the end");
		list.traverseList();
		System.out.println("\nFinally, traversal and displaying the list:");
		list.traverseList();

	}

}
