/*
Program that creates expression trees and has methods for evaluating postfix and prefix expressions from these trees.
Creates ExpressionNode objects which hold a data value as well as the values of their left and right children.
*/

import java.util.LinkedList;

public class ExpressionTree
{
	ExpressionNode root = new ExpressionNode("0", null, null);
	private MyStack<ExpressionNode> stack;
	
	public ExpressionTree(String postfix)
	{
		//create array to hold operators and operands
		String[] expressions = new String[postfix.length()];
		
		//split by whitespace
		expressions = postfix.split("\\s+");

		//create a stack using MyStack class
		stack = new MyStack<ExpressionNode>();
				
		
		//loop through and see whether each element is an operator or operand, then perform operations accordingly
		for(int i = 0; i < expressions.length; i++)
		{				
			//see if it's any of the four operators allowed for this program
			if(expressions[i].equals("+") || expressions[i].equals("-") || expressions[i].equals("*") || expressions[i].equals("/"))
			{
				//make sure it's not empty and warn them if it is
				if(stack.isEmpty() == true)
				{
					System.out.println("Stack is empty.");
				} else
				{
					//get the two operands by popping the stack twice
					ExpressionNode rightVal = stack.pop();
					ExpressionNode leftVal = stack.pop();
					//if it's an operator, make it a node, passing in pops for its left and right nodes
					ExpressionNode opNode = new ExpressionNode(expressions[i], leftVal, rightVal);
					//add new ExpressionNode to the stack
					stack.push(opNode);
				}
			} else
			{
				//if it's not an operator, it's an operand
				//make new ExpressionNode with null values for right and left (since it's operand)
				ExpressionNode numNode = new ExpressionNode(expressions[i], null, null);
				//push the new node onto the stack
				stack.push(numNode);
			}
		}
		//set the root by a pop from the stack (since it's all finished now)
		root = stack.pop();
	}
	
	public int eval()
	{
		//call private method, passing in root
		return eval(root);
	}
	
	public ExpressionNode getRoot()
	{
		//simple accessor method for root
		return root;
	}
	
	public String postfix()
	{
		//call private method, passing in root
		return postfix(root);
	}
	
	public String prefix()
	{
		//call private method, passing in root
		return prefix(root);
	}
	
	private int eval(ExpressionNode root)
	{
		//this method returns the integer value associated with evaluating the expression tree
				
		//see if it's empty and if it is, warn them
		if(stack.isEmpty() == true)
		{
			System.out.println("Stack is empty.");
		}
		
		int returnVal = 0;

		//if it's null, need to return the integer value
		if(root.left == null && root.right == null)
		{
			// return numerical value of root.data
			int data = Integer.parseInt(root.data);
			return data;
		} else
		{
			//get result of the left side by recursively calling eval
			int a = eval(root.left);
			//get result of the right side by recursively calling eval
			int b = eval(root.right);
			
			//do the operations, as necessary, on a and b
			if(root.data.charAt(0) == '+')
			{
				returnVal = a + b;
			} else if(root.data.charAt(0) == '-')
			{
				returnVal = a - b;
			} else if(root.data.charAt(0) == '*')
			{
				returnVal = a * b;
			} else if(root.data.charAt(0) == '/')
			{
				returnVal = a / b;
			}
		}
		//return the end result
		return returnVal;
	}
	
	private String prefix(ExpressionNode root)
	{
		String toReturn = "";
		
		if(root==null)
		{
			return toReturn;
		}
		
		//since it's prefix, first concatenate the root value to the string to be returned
		toReturn += root.data;
		
		//add spaces for clarity
		toReturn += " ";
		
		if(root.left != null)
		{
			//concatenate the result of recursively calling postfix on the left node to the string to be returned
			toReturn += prefix(root.left);
			
			//add spaces for clarity
			toReturn += " ";
		}
				
		if(root.right != null)
		{
			//concatenate the result of recursively calling postfix on the right node to the string to be returned
			toReturn += prefix(root.right);
			
			//add spaces for clarity
			toReturn += " ";
		}
		//return the final string		
		return toReturn;
	}
	
	private String postfix(ExpressionNode root)
	{
		String toReturn = "";
		
		if(root==null)
			return toReturn;
		
		if(root.left != null)
		{
			//since it's postfix, start by concatenating the result of calling postfix on the left to the string
			toReturn += postfix(root.left);
			
			//add space for clarity
			toReturn += " ";
		}
				
		if(root.right != null)
		{
			//then concatenate the result of calling postfix on the right to the string
			toReturn += postfix(root.right);
			//space for clarity
			toReturn += " ";
		}
		
		//finally, add the root's data to the string to return
		toReturn += root.data;
		toReturn += " ";
		
		//return the completed string
		return toReturn;
	}
	
	private class ExpressionNode
	{
		//set fields for data, left node, and right node
		String data;
		ExpressionNode left;
		ExpressionNode right;
		
		//construct the node
		private ExpressionNode(String data, ExpressionNode l, ExpressionNode r)
		{
			//set the values to the values passed in
			this.data = data;
			this.left = l;
			this.right = r;
		}
	}
}
