# ☕️ Java
- [Set-Up](#basics)
  - [VSCode \& Java](#vscode--java)
  - [Call additional classes from .jar files](#call-additional-classes-from-jar-files)
- [Basics](#basics)

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
- First programs
```java
public class Bonjour{ // class public -> can be seen from outside the class
  public static void main(String[] args){
  System.out.println ("Salut !"); // print function in Java
  return; // to give the hand back 
}
}
```
`String[] args`: [command line arguments](https://docs.oracle.com/javase/tutorial/essential/environment/cmdLineArgs.html) 

- Variables
Variables need to be **declared** and **typed**
Both declaration and initialisation can be combined `int j = 3`

- Printing
  ` System.out.print("hello");` does not skip line afterwards
  ` System.out.println("hello");` skips line afterwards

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

- If statements
```Java
if(boolean condition ){
  // do actio heere
}
else{ // complete }
```
Else is optional.

- Loops
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
- Functions
```Java
static <type_result> <name>(<params>)
{
[declare var]
[instructions]
return <result>;
}
```

NB: `void` when a function has type void, `return` is optional however it eases the comprehension of the code overall. 

