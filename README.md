//# pallavigoel1996-gmail.com
//Tree Traversal IN JAVA (LEFT/RIGHT/BOTTOM/TOP)

import java.util.LinkedList;
import java.util.Queue;
import java.util.TreeMap;

public class ViewOfTrees {
	
	Node root;
	
	static class Node{
		
		Node left;
		Node right;
		int data;
		int height;
		
		
		Node(int key)
		{
			left=null;
			right=null;
			data=key;
			height=0;
		}
		
	}
	int maxL=0;
	int maxR=0;
	
	private void leftview(Node node,int level) {
		// TODO Auto-generated method stub
		
		if(node==null)
		return;
		
		if(level>maxL)
	   {
		System.out.println(node.data);
		maxL=level;
		}
		
	    leftview(node.left,level+1);
		leftview(node.right,level+1);
	
	}
	
	private void rightview(Node node,int level)
	{

		if(node==null)
			return;
		
		if(level>maxR)
		{
			System.out.println(node.data);
			maxR=level;
		}
		
		
		rightview(node.right,level+1);
		rightview(node.left,level+1);
	}
	
	
	public void topView(Node root)
	{
		
		
		if(root==null)
			return;
		
		
		TreeMap<Integer,Integer> map=new TreeMap<Integer,Integer>();
		Queue <Node> q= new LinkedList<>();
		
		q.add(root);
		
		
		while(!q.isEmpty())
		{
			Node temp=q.poll();
			int hd=temp.height;
			
			if(map.get(hd)==null)
			{
				map.put(hd,temp.data);
			}
      
			if(temp.left!=null)
			{
				q.add(temp.left);
				temp.left.height=hd-1;
			}
			
			if(temp.right!=null)
			{
				q.add(temp.right);
			     temp.right.height=hd+1;
			}			
		}
		
		System.out.println(map.values());

	}
	
	

	public void bottomView(Node root)
	{
		
		
		if(root==null)
			return;
		
		
		TreeMap<Integer,Integer> map=new TreeMap<Integer,Integer>();
		Queue <Node> q= new LinkedList<>();
		
		q.add(root);
		
		
		while(!q.isEmpty())
		{
			Node temp=q.poll();
			int hd=temp.height;
      
				map.put(hd,temp.data);
			
			if(temp.left!=null)
			{
				q.add(temp.left);
				temp.left.height=hd-1;
			}
			
			if(temp.right!=null)
			{
				q.add(temp.right);
			     temp.right.height=hd+1;
			}	
		}
		
		System.out.println(map.values());	
	}
	
	
	public static void main(String args[])
	{
		
		 ViewOfTrees view = new ViewOfTrees();
		 view.root=new Node(1);
		 view.root.left=new Node(2);
		 view.root.right=new Node(3);
		 view.root.left.left=new Node(4);
		 view.root.left.right=new Node(5);
		 view.root.left.left.left=new Node(6);
		 view.root.left.left.right=new Node(7);
		 
		 
		 
		view.topView(view.root);
		view.bottomView(view.root);
		System.out.println("LEFT");
		view.leftview(view.root,1);
		System.out.println("RIGHT");
		view.rightview(view.root,1);
		
	}



}

