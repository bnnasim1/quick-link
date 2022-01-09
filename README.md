# quick-link
package quicksort.linkedlist;
import java.util.Scanner;
class node{
 int data;
 node link;
}
class LinkedList{
node start=null;
 void create_node(int Data)
 {
 node temp=new node();
 temp.data=Data;
 temp.link=null;
 if(start==null)
 {
 start=temp;
 }
 else{
 node q;
 q=start;
 while(q.link!=null){
 q=q.link;
 
 }
 q.link=temp;
 }
 }
 void display()
 {
 node q=start;
 if(start==null){
 System.out.println("Empty list");
 }
 else
 {
 while(q!=null){
 System.out.println(q.data);
 q=q.link;
 
 }
 }
 }
 node partition(node start, node end) {
 if (start == end && start == null && end == null) {
 return start;
 }
 node pivot_pr = start;
 node curr = start;
 int pivot = end.data;
 while (start != end) {
 if (start.data < pivot) {
 pivot_pr=curr;
 int temp=curr.data;
 curr.data=start.data;
 
 start.data=temp;
 curr=curr.link;
 
 }
 start=start.link;
 }
 int temp=curr.data;
 curr.data=pivot;
 end.data=temp;
 return pivot_pr;
 
 }
 
 
 void quick(node start,node end ){
 if(start==end)
 return;
 node pivot_pr=partition(start,end);
 quick(start,pivot_pr);
 if (pivot_pr!=null&&pivot_pr==start)
 quick(pivot_pr.link,end);
 else if(pivot_pr!=null&&pivot_pr.link!=null)
 quick(pivot_pr.link.link,end);
 }
 
 }
public class list{
 
public static void main(String[] args) {
 Scanner sc=new Scanner(System.in);
 LinkedList list=new LinkedList();
 
 System.out.println("Enter the Number of Nodes:");
 
 int num=sc.nextInt();
 System.out.println("Add Data in linklist:");
 for(int i=1;i<=num;i++)
 {int v=sc.nextInt();
 list.create_node(v);
 }
 node n=list.start;
 while(n.link!=null)
 n=n.link;
 
 System.out.println(" After Sorting:");
 list.display();
 list.quick(list.start,n);
 System.out.println("Before Sorting:");
 list.display();
 }
 } 
