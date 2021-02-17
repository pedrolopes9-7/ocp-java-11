## Chapter 1 Flashcards
### Welcome to Java

#### Main features of Java that can be asked you in the exam:
- Secure, Multithreaded, Platform Independent, Object-Oriented

#### Java Classes

The main method is used as a gateway between the JVM and the program written. Any of the three syntaxes for the main method below are accepted by the JVM.

```java
1: public class FirstClass {
2:   public static void main(String[] args)
3:   public static void main(String args [])
4:   public static void main(String... args) 
5: }
```
- Passing arguments to *main* method. The method accepts all types of arguments interpreted as a String. If the String contains any space, you must use the double comma:
```shell
    javac FirstClass.java
    java FirstClass "Space Separated" FirstClass
```

```java
1: public static void main(String[] args){
2:    System.out.println(args[0] + " " + args[1])
3: }
```

- Each ***.java*** file can only contain only and only one ***public*** class and many ***private*** classes
- The filename **must** match the class name, including case, and have a *.java* extension
- The ***javac*** responsible for compiling ***.java*** files into ***.class*** files. Example:
  ```shell
    javac [-d | -cp | -classpath | --class-path] <ClassName>
  ```
  where:
  **-d** specifies a target directory for the compilation
  **-d** must not be confused with **-D** (Case Sensitveness)
- The ***java*** command responsbile for executing the program on the Java Virtual Machine (JVM)
```shell
    java [-cp | -classpath | --class-path] <ClassName>
```
where:
  **-cp | -classpath | --class-path** defines the path to find the compiled Java classes (*.class*)
- Starting in Java SE 11, it is possible to execute the program in one line without using *javac*, and instead compiling it in memory. The below command only executes the source-code and therefore no *.class* file is created:
```shell
    java FirstClass.java FirstClass
```
- Programs executed in-line can't import any source-code that is **not** part of the JDK.
- The ***javadoc*** command 
- The ***jar*** command
```shell
    jar [-c | --create | -v | --verbose | -f | --file ] <jarName>.jar [-C] <directory>
```
where:
**-c** creates new JAR
**-v** prints details of the execution
**-f** JAR filename
**-C** directory containig files to create the JAR

- The Java Runtime Environment (JRE) for just running Java programs (from previous versions of Java SE 11, it was possible to donwload just the JRE)

### Packages and imports

- Any class, field of method must be imported or be within the same package as the calling class
- Impossible to have many wildcards in one statement
- Wildcards only matches **classes** but not other packages or methods
- The package *java.lang* is always imported by every application and thus can be ommited
- Two classes with same name imported with his FQCN throws an compilation error
- Imports always choose the Fully Qualified Class Name (FQCN) to pick instead of the wildcard **(*)**
- If no package is defined, JVM picks one called *default*
- The package must be declared as the first thing in the class, before the imports.
- Imports must be declared before any class
  
- Example of imports and packages:
```java
0:  package test;
1:  import java.lang.System;
2:  import java.lang.*;
3:  import java.util.Date;
4:  import java.sql.Date;
5:  import java.util.Random;
6:  import java.util.*;
7:  public class ImportExample {
8:     public static void main(String[] args) {
9:        Random r = new Random();
10:        System.out.println(r.nextInt(10));
11:     }
12: }
```
Line 1 and 2 are redudant because *java.lang* is always imported. Line 6 is redundant because the example only used the *Random* class and not the entire wildcard. Line 4 and 5 will throw an compilation error.
