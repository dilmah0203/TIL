# π‘ **μΆμν΄λμ€ vs μΈν°νμ΄μ€**

**μΆμν΄λμ€ vs μΈν°νμ΄μ€**

- μΆμν΄λμ€μ μΈν°νμ΄μ€λ μΈμ€ν΄μ€ν νλ κ²μ λΆκ°λ₯νλ©°,
- κ΅¬νλΆκ° μλ λ©μλμ μλ λ©μλλ₯Ό λͺ¨λ κ°μ§ μ μλ€λ μ μμ μ μ¬νλ€.
- μΈν°νμ΄μ€μμ λͺ¨λ  λ³μλ κΈ°λ³Έμ μΌλ‘ public static final μ΄λ©°, λͺ¨λ  λ©μλλ public abstractμΈ λ°λ©΄ μΆμν΄λμ€λ staticμ΄λ finalμ΄ μλ νλλ₯Ό μ§μ ν  μ μκ³  public, protected, private λ©μλλ₯Ό κ°μ§ μ μλ€.
- μΈν°νμ΄μ€λ λ€λ₯Έ μ¬λ¬κ°μ μΈν°νμ΄μ€λ€μ ν¨κ» κ΅¬νν  μ μμ§λ§ μΆμν΄λμ€λ μμμ ν΅ν΄ κ΅¬νλλλ° μλ°λ λ€μ€ μμμ μ§μνμ§ μμΌλ―λ‘ μΆμν΄λμ€λ₯Ό μμλ°μ μμν΄λμ€λ λ€λ₯Έ ν΄λμ€λ₯Ό μμλ°μ μ μλ€.

<br>

**μΆμν΄λμ€**

μΆμ λ©μλλ μλμ κ°μ΄ κ΅¬νλΆκ° μλ λ©μλλ₯Ό λ§νλ©°, μ΄λ€ ν΄λμ€κ° μΆμ λ©μλλ₯Ό ν¬ν¨νλ€λ©΄ μΆμ ν΄λμ€λ‘ μ μΈλμ΄μΌ νλ€.

```java
public abstract void method();
```

μΆμν΄λμ€λ₯Ό μμλ°λ ν΄λμ€λ λΆλͺ¨ν΄λμ€μ μλ λͺ¨λ  μΆμλ©μλλ€μ κ΅¬ννλ€. κ·Έλ μ§ μμ κ²½μ° ν΄λΉ μλΈν΄λμ€ λν abstractλ‘ μ μΈλμ΄μΌ νλ€.

```java
public abstract class ν΄λμ€μ΄λ¦ {
    //νλ μ μΈ
    //μΆμλ©μλ
    //μΌλ°λ©μλ
    public void move() {
    }
}
```

μΈν°νμ΄μ€μ κ²½μ° default λλ staticμΌλ‘ μ μΈλμ§ μμ λ©μλλ abstractμ΄κΈ° λλ¬Έμ μλ΅μ΄ κ°λ₯νλ€.

<br>

**μΈμ  μ¬μ©ν κΉ?**

- μ¬λ¬ νμ ν΄λμ€μ κ³΅ν΅ κΈ°λ₯μ μΊ‘μνν  λ
- public μ΄ μλ κ³΅ν΅μ μΈ νλλ λ©μλλ₯Ό κ°μ§λ ν΄λμ€λ₯Ό μμλ°κ³ μ ν  λ 
- μν λ³κ²½μ μν΄ non-static, non-final νλ μ μΈμ΄ νμν  λ

λ€μ μμλ₯Ό λ³΄μ. 

```java
public abstract class Shape {
    int x;
    
    public void move() {
        ...
    }
    abstract void draw();
    abstract double area();
}
public class Rectangle extends Shape {
    @Override
    public void draw() {
        ...
    }
    @Override
    public double area() {
        ...
    }
}
public class Triangle extends Shape {
    @Override
    public void draw() {
        ...
    }
    @Override
    public double area() {
        ...
    }
}
```

μΆμ ν΄λμ€λ **Is a** κ΄κ³μΌ λ μ¬μ©νλ©° Rectangleκ³Ό Triangle ν΄λμ€λ Shape ν΄λμ€λ₯Ό νμ₯νλ€. draw()μ area() λ©μλλ μΆμν΄λμ€λ₯Ό μμλ°λ Rectangleκ³Ό Triangleν΄λμ€κ° μ€λ²λΌμ΄λ©νλλ‘ ν¨μΌλ‘μ¨ λμ λ³κ²½μ΄ κ°λ₯νλ€. λν Shapeν΄λμ€μμ int xλ₯Ό μ μΈν¨μΌλ‘μ¨ **μνμ κ΄μ¬**ν  μ μλ€λ κ²μ΄ μΈν°νμ΄μ€μμ ν° μ°¨μ΄μ μ΄λ€. 


<br>

**μΈν°νμ΄μ€**

```java
public interface μΈν°νμ΄μ€μ΄λ¦ {
    //μμ νλ
    //λ©μλ
}
```

<br>

**μΈμ  μ¬μ©ν κΉ?**

- κ΅¬ν ν΄λμ€λ€ κ°μ κ΄λ ¨μ±μ΄ μλ κ²½μ°
- νΉμ  λ°μ΄ν° νμμ νλμ λͺμνκ³ μΆμλ°, μ΄λμ κ΅¬νλλμ§ μκ΄ μλ κ²½μ°
- λ€μ€μμμ νμ©ν  λ

<br>

λ€μ μμλ₯Ό λ³΄μ.

```java
public class Car {
    public void method() {
        System.out.println("car method");
    }
}
  
public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.method();
    }
}
```

Main ν΄λμ€μμ λ€μκ³Ό κ°μ΄ κ°μ²΄λ₯Ό μμ±νλ€. κ°μ²΄λ μμ± μ΄ν Carν΄λμ€μ μ μΈλ λͺ¨λ  λ©μλλ₯Ό μ¬μ©ν  μ μκ² λλ€. νμ§λ§ Main ν΄λμ€μμ λ€λ₯Έ κ°μ²΄λ₯Ό μ¬μ©νκ³  μΆμ λλ μλ‘μ΄ κ°μ²΄λ‘ λ³κ²½ν΄μ£Όμ΄μΌ νλ€. μ΄κ²μ Carν΄λμ€μ Mainν΄λμ€κ° κ°ν κ²°ν©μ μ΄λ£¨κ³  μλ€κ³  λ³Ό μ μμΌλ©° μΈν°νμ΄μ€λ₯Ό μ΄μ©νμ¬ λ€μκ³Ό κ°μ΄ κ²°ν©λλ₯Ό λ?μΆ μ μλ€.

```java
public class Example {
    void auto(Movable m) {
        m.method();
    }
}
public interface Movable {
    public void method();
}
public class Car implements Movable {
    @Override
    public void method() {
        System.out.println("method in Car class");
    }
}
public class Bus implements Movable {
    @Override
    public void method() {
        System.out.println("method in Bus class");
    }
}
public class Main {
    public static void main(String[] args) {
        Example e = new Example();
        e.auto(new Car()); //method in Car class
        e.auto(new Bus()); //method in Bus class
    }
}
```

Movable μΈν°νμ΄μ€λ₯Ό μμλ°μ Carκ³Ό Busν΄λμ€μ κ°κ° λ₯Έ λμμ μ μΈνκ³  μ΄ λμμ μ¬μ©νλ Main ν΄λμ€μμλ λ€λ₯Έ κ°μ²΄λ₯Ό μ¬μ©ν  μ Movableμ κ΅¬ννλ κ°μ²΄λ₯Ό μμ±νκ³  λ°κΏμ£ΌκΈ°λ§ νλ©΄ λλ€. 

<br>

**JDK 8μ μΈν°νμ΄μ€μ μΆκ°λ κΈ°λ₯**

- default method

  JDK 8 μ΄μ μ μΈν°νμ΄μ€μμ κ΅¬νμ μ μν  μ μμλ€. κ·Έλμ μλ‘μ΄ λ©μλλ₯Ό μΆκ°νλ €λ©΄ μΈν°νμ΄μ€λ₯Ό κ΅¬ννλ λͺ¨λ  ν΄λμ€λ€μ΄ ν΄λΉ λ©μλλ₯Ό κ΅¬νν΄μΌνλ€.
  νμ§λ§ default methodλ‘ μΆκ°κ° κ°λ₯ν΄μ§λ©΄μ κΈ°μ‘΄ μΈν°νμ΄μ€λ₯Ό κ΅¬ννλ ν΄λμ€μμ λ©μλλ₯Ό overrideνμ§ μμλ λλ€.
  κΈ°μ‘΄ μ½λμ μν₯μ μ£Όμ§ μκ³  μλ‘μ΄ λ©μλλ₯Ό κ°μ§ μ μλλ‘ μ΄μ  μΈν°νμ΄μ€μ λν νΈνμ±μ μ κ³΅νλ€.

```java
public interface Calculator {
    final int first = 10; //μμ νλ
    public int plus(int x, int y); //λ©μλ
    public int minus(int x, int y);
    default int multiply(int x, int y) {
        return x * y;
    }
}
public class Example implements Calculator {
    @Override
    public int plus(int x, int y) {
        return x + y;
    }
    @Override
    public int minus(int x, int y) {
        return x - y;
    }
}
public class Main {
    public static void main(String[] args) {
        Calculator calc = new Example();
        int value = calc.multiply(2, 3);
        System.out.println(value); //6
    }
}
```

<br>

- static method

  κ°μ²΄ μμ± μ¬λΆμ μκ΄μμ΄ μ¬μ©μ΄ κ°λ₯νλ©°, overrideκ° λΆκ°λ₯νκ³  μμλμ§ μλλ€.
  μμλ₯Ό μ μΈν  λλ static blockμμ μ΄κΈ°νν  μ μκ³ , μ μΈκ³Ό λμμ μ΄κΈ°νν΄μΌνλ€.
  
```java
public interface Calculator {
    final int first = 10; //μμ νλ
    public int plus(int x, int y); //λ©μλ
    public int minus(int x, int y);
    static int multiply(int x, int y) {
        return x * y;
    }
}
public class Ex implements Calculator {
    @Override
    public int plus(int x, int y) {
        return x + y;
    }
    @Override
    public int minus(int x, int y) {
        return x - y;
    }
}
public class Main {
    public static void main(String[] args) {
        int value = Calculator.multiply(5, 3);
        System.out.println((value));
    }
}
```

<br>

**μ λ¦¬**

μΆμν΄λμ€λ μ κ·Όμ νμμ μ μ½ μμ΄ κ°μ²΄μ μν λ³κ²½κ³Ό λ©μλ μ€λ²λΌμ΄λ©μ ν΅ν κ³΅ν΅ κΈ°λ₯μ κ΅¬ννκ³  νμ₯μν¬ λ μ¬μ©νλ©°, 
μΈν°νμ΄μ€λ λμ λ³κ²½μ ν΅ν΄ κ²°ν©λλ₯Ό λ?μΆλ κ²μ λμμ€λ€.

<br>

μ°Έκ³ 

[https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html](https://docs.oracle.com/javase/tutorial/java/IandI/createinterface.html)

[https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)

[https://www.geeksforgeeks.org/difference-between-abstract-class-and-interface-in-java/](https://www.geeksforgeeks.org/difference-between-abstract-class-and-interface-in-java/)

[https://www.journaldev.com/1607/difference-between-abstract-class-and-interface-in-java](https://www.journaldev.com/1607/difference-between-abstract-class-and-interface-in-java)


