package myPack;

import java.awt.List;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collection;

public class Assignment52 {

	public static void main(String[] args) {
		FixedStack f = new FixedStack(5);
		f.push(1);
		f.push(2);
		f.push(3);
		f.push(4);
		f.push(5);
		System.out.println(f);
		f.push(6);
		f.pop();
		f.pop();
		System.out.println(f);
		f.push(13);
		f.push(43);
		System.out.println(f);
		
		

		VariableStack var = new VariableStack(5);
		var.push(1);
		var.push(2);
		var.push(3);
		var.push(4);
		var.push(5);
		System.out.println(var);
		var.push(6);
		//var.pop();
		System.out.println(var);

	}

}


interface Stack{
	void push(int i);
	int pop();
}


class FixedStack implements Stack{
	int size;
	int index;
	int stack[];
	FixedStack(int size){
		this.size=size;
		index=-1;
		stack= new int[size];
	}

	@Override
	public void push(int i) {
		if (index>=size-1)
			System.out.println("StackOverflow");
		else
			stack[++index]=i;
		
	}

	@Override
	public int pop() {
		
		return stack[index--];
	}

	@Override
	public String toString() {
		return "FixedStack [size=" + stack.length + ", index=" + index + ", stack=" + Arrays.toString(stack) + "]";
	}
	
	
}

class VariableStack implements Stack{
	int size;
	int index;
	ArrayList<Integer> list= new ArrayList<Integer>(size);
	
	public VariableStack(int size) {
		this.size=size;
		index=-1;
	}

	@Override
	public void push(int i) {
		list.add(i);
		index++;
		
		
	}

	@Override
	public int pop() {
		
		return list.get(index--);
		
	}

	@Override
	public String toString() {
		return "VariableStack [size=" + list.size() + ", list=" + list + "]";
	}
	
}
