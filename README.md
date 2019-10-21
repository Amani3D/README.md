# README.md

The stack and the heap.Two areas of memory, one where objects live(the heap) 
and one where method invocations and local variables live(the stack). 
Two kinds of variables. Instance variables and local variables. Local 
variables are also known as stack variables. A stack is pretty self 
explanatory, it is a stack of variables and methods. But a heap is just a 
pile of of objects.
An instance variable would be:
	public class Duck {
		int size;
	}
(Every duck has a size)
A local variable would be:
	public void foo(int x) {
		int i = x + 3;
		boolean b = true;
	}
(The parameter x and the variables i and b are all local variables)

When calling a method it lands on top of a call stack. The new thing being
pushed onto the stack is called the stack frame. It holds the state of the
method, including what line of code is executing and what the the values are
of the local variables. The method at the top of the stack is always the one
running at the moment. Until a method hits it closing curly brace it will 
stay on the top. 
An example of a stack would be:
(top of the stack/code running first)
	public void doStuff() {
		boolean b = true;
		go(4);
	}
	public void go(int x) {
		int z = x + 24;
		crazy();
		//imagine more code here
	}
	public void crazy() {
		char c = 'a';
	}
(bottom of the stack/code that will be ran last)
If a local variable is a reference to an object then it doesn't matter where
it goes on the stack but the object goes on the heap. Instance variables
also live on the heap. The value of an objects instance variable live inside
the object. Java makes space for the instance variables based on their
primitive type. Even if the instance variable is an object reference, Java
still makes space for it. 
(Declare a new reference)
	Duck myDuck
(Create and object)
	Duck myDuck = new Duck();
(The = links the object and the reference)
This is calling a Duck constructor, not a method. A constructor may look
and feel like a method but it is not a mthod. The only way to invoke a
constructor is with the word new, followed by the class name. Either you can
write your constructor or the compiler can write it for you. 
(default constructor)
	public Duck() {
	}
Unlike methods contructors have no return type. And constructor names are
always the same as the class name. A constructor runs before an object can
be assigned. 
(constructor code)
	public class Duck() {
	
		public Duck() {
			System.out.println("Quack");
		}
	}



(This calls the Duck constructor)	
	public class UseADuck {

		public static void main (String[] args) {
			Duck d = new Duck();
		}
	}
Most use a constructor to initialize the state of an object, to make and
assign values to the objects instance variables. 
	public Duck() {
		size = 34;
	}
(maybe you want to put the size for specific ducks, not just one duck)
	public class Duck {
		int size;

		public Duck() {
			System.out.println("Quack");
		}
			
		public void setSize(int newSize) {
			size = newSize;
		}
An object shouldn't be used until one or more parts of it's state have
been initialized.
	public class Duck {
		int size;

		public Duck(int duckSize) {
			System.out.println("Quack");

			size = duckSize;

			System.out.println("size is " + size);
		}
	}

	public class UseADuck {
		public static void main (String[] args) {
			Duck d = new Duck(42);
If you want two options for making a duck you can set a size as the
constructor argument and one where they don't specify a size.

If you don't initialize a constructor then the compiler will initalizie one for you. 

If you wish to have a no arg constructor then you have to build it yourself. 

More than one constructor means that you are overloading.



