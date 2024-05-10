# ☕️ Java
- [Set-Up](#basics)
  - [VSCode \& Java](#vscode--java)
- [Basics](#basics)
  - [Hello World](#hello-world) 
- [Objects](#objects)
- [Comparator](#comparator)
- [Abstraction](#abstraction)
- [Complexity](#complexity)

## Set-Up
### VSCode & Java
- To create a new project: `Ctrl+Shift+P` -> `Java: Create Java New Project`
- Select `No build tools` and `No build tools` to create a simple Java project
- create a new java source file (Test.java) by clicking on the blue button New File and choose New Java class.
- Hello World example:
```java
public class Test {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```
- Run without debugging: `Ctrl+F5`

### Call additional classes from .jar files
- click on *referenced libraries* in *Java Projects* (bottom left), add the .jar file 

Test it works: 
- duplicate a Test `Hello World` class and change the name to `TestTC`
- Then we may replace System.out by TC to call the println function provided by TC instead of the standard Java function:

```java
import tc.TC;

public class TestTC {
    public static void main(String[] args) {
        TC.println("Hello, World!");
    }
}
```

## Basics
Naming convetion in Java: function names start by lower camel case, class names by upper camel case. 
### Hello World
```java
public class Bonjour{ // class public -> can be seen from outside the class
  public static void main(String[] args){
  System.out.println ("Hello World !"); // print function in Java
  return; // to give the hand back 
}
}
```
`String[] args`: [command line arguments](https://docs.oracle.com/javase/tutorial/essential/environment/cmdLineArgs.html) 

`System.out.print("hello");` does not skip line afterwards
`System.out.println("hello");` skips line afterwards

It is possible to overload: 
```java
public class Calculs2{
  public static void main(String[] args){
    int n = 10, b;
    b = n*(n-1)/2;
    System.out.println("résultat="+b);
    return;
  }
}
```

### Variables
Variables need to be **declared** and **typed**
Both declaration and initialisation can be combined `int j = 3`

- Affectation
convert to a type: `int x = (int)12.7`
useful for double division from int.

### Loops and conditions 
-** If statements**
```Java
if(boolean condition ){
  // do actio heere
}
else{ // complete }
```
Else is optional.

- `While`
  ```Java
    while(n != devinette){
        // complete here
    }
    else{
        // else condition
    }
```
- `For`
```Java
for(i = 0; i <= 9; i++){
// complete 
}
```
### Functions
```Java
static <type_result> <name>(<params>)
{
[declare var]
[instructions]
return <result>;
}
```

NB: `void` when a function has type void, `return` is optional however it eases the comprehension of the code overall. 

### Commenting in Java
- Documentation Comments
  This type of comment is used generally when writing code for a project/software package, since it helps to generate a documentation page for reference, which can be used for getting information about methods present, its parameters, etc. For example,
Examples:
```Java
// Java program to illustrate frequently used 
// Comment tags 

/** 
* <h1>Find average of three numbers!</h1> 
* The FindAvg program implements an application that 
* simply calculates average of three integers and Prints 
* the output on the screen. 
* 
* @author Pratik Agarwal 
* @version 1.0 
* @since 2017-02-18 
*/
public class FindAvg 
{ 
	/** 
	* This method is used to find average of three integers. 
	* @param numA This is the first parameter to findAvg method 
	* @param numB This is the second parameter to findAvg method 
	* @param numC This is the second parameter to findAvg method 
	* @return int This returns average of numA, numB and numC. 
	*/
	public int findAvg(int numA, int numB, int numC) 
	{ 
		return (numA + numB + numC)/3; 
	} 

	/** 
	* This is the main method which makes use of findAvg method. 
	* @param args Unused. 
	* @return Nothing. 
	*/

	public static void main(String args[]) 
	{ 
		FindAvg obj = new FindAvg(); 
		int avg = obj.findAvg(10, 20, 30); 

		System.out.println("Average of 10, 20 and 30 is :" + avg); 
	} 
} 
```
### Tables
- unidim
```Java
int[] t = new int[5]; // allocation obligatoire
for(int i = 0; i < 5; i++){
	t[i] = i*i;	
}
// example of init
int[] t = new int[]{1, 0, -10, 17, 20, 17};
```
Size of the table: `t.length`
- bi-dim
```Java
toto[][] tab;
tab = new toto[n][m];
// example of init
int[][] tab=new int[][]{{1, 2}, {4, 5}, {7, 8}};
```

# Objects
### New class \& instantiation 
```Java
public class X{
	public String nom;
	public int promotion;
	public X(String n, int promo){ // pas de static
		this.nom = n;
		this.promotion = promo;
	// pas de return
	}
}
```
### Class variables
- `final` : value cannot change after creation (constante)
- `static`: value is known when compiling
  e.g. `public static final int annee_creation = 1794;`

-----
- `public`: variables, methods are visible
- `private`: opposite of public

# Comparator 
[`public interface Comparator<T>`](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html)

Type Parameters:
T - the type of objects that may be compared by this comparator

> The Comparator interface is used to order objects of an arbitrary class.
> It is not to be confused with the Comparable interface, which is implemented by the class to be sorted.
> The Comparator interface is implemented in a separate class.
```Java
class MyComparator implements Comparator<MyClass> {
  @Override public int compare(MyClass a, MyClass b)
  {
    // Compare logic
    ...
    return result;
  }
}
```

# Abstraction
Data abstraction is the process of hiding certain details and showing only essential information to the user.
Abstraction can be achieved with either abstract classes or interfaces (which you will learn more about in the next chapter).
>  `interface`, is a completely "abstract class" that is used to group related methods with empty bodies

To access the interface methods, the interface must be "implemented" (kinda like inherited) by another class with the implements keyword (instead of extends). 
The body of the interface method is provided by the "implement" class:

```Java
// Interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

NB:
Like abstract classes, interfaces cannot be used to create objects (in the example above, it is not possible to create an "Animal" object in the MyMainClass)
Interface methods do not have a body 
- the body is provided by the "implement" class
- On implementation of an interface, you must override all of its methods
- Interface methods are by default abstract and public
- Interface attributes are by default public, static and final
- An interface cannot contain a constructor (as it cannot be used to create objects)

Why use it ?
- To achieve security - hide certain details and only show the important details of an object (interface).
- Java does not support "multiple inheritance" (a class can only inherit from one superclass).
However, it can be achieved with interfaces, because the class can implement multiple interfaces. Note: To implement multiple interfaces, separate them with a comma (see example below).

# Complexity 
How much time will an algo take depending on the size of the inpput ? 
$T(P) = K ·f(P)$ with $K$ depednant on the computer and $f(P)$ dependant on the algo itself.

Examples:
- sequantial search: $O(n)$ on avg for table of size $n$
- sort the list first and then search -> dichotomic search $O(log_2(n))$
