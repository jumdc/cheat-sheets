# ☕️ Java
- [Java](#java)
  - [Basics](#basics)
    - [VSCode \& Java](#vscode--java)
    - [Call additional classes from .jar files](#call-additional-classes-from-jar-files)



## Basics
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
