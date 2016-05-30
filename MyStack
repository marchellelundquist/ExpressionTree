/*
Stack program that supports the ExpressionTree program by creating a LinkedList-based stack
as well as methods for popping, peeking, pushing, and checking for emptiness
*/

import java.util.LinkedList;

public class MyStack<T>
{
	private LinkedList<T> stack;

	public MyStack()
	{
		stack = new LinkedList<T>();
	}
	
	//if stack is empty return null; if not, remove element from stack
	public T pop()
	{

		if(stack.size() == 0)
		{
			return null;
		}
		else
		{
			return stack.remove();
		}
	}

	//displays first elements in stack by utilizing LinkedList's getFirst() method
	public T peek()
	{
		return stack.getFirst();
	}

	//adds element to the top of stack by utilizing LinkedList's addFirst() method
	public void push(T e)
	{
		stack.addFirst(e);
	}
    
    //returns boolean evaluation of the stack's emptiness by utilizing LinkedList's isEmpty() method
    public boolean isEmpty()
    {
        return stack.isEmpty();
    }
}
