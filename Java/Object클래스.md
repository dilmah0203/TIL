# π‘ **Objectν΄λμ€**

μλ°μμ λͺ¨λ  ν΄λμ€μ λΆλͺ¨λ java.lang.Object

<br>

```java
  public class Inheritance{}
  public class Inheritance extends Object{} //μ€ν κ²°κ³Όλ κ°λ€
```

<br>

**Objectν΄λμ€κ° μ κ³΅νλ μ£Όμ λ©μλ**

- **toString()** 

  κ°μ²΄λ₯Ό λ¬Έμμ΄λ‘ λ³ννκΈ° μν λ©μλ, μ€λ²λΌμ΄λ© λμ΄ μμ§ μμ κ²½μ°μλ
  ν΄λμ€μ΄λ¦@16μ§μμ½λ λ₯Ό λ°ν

```java
public class Book{
    int bookNumber;
    String bookTitle;

    Book(int bookNumber, String bookTitle){
        this.bookNumber = bookNumber;
        this.bookTitle = bookTitle;
    }

    public String toString(){
        return bookTitle + " " + bookNumber;
    }
}
```

```java
public class Tostring{
    public static void main(String[] args){
        Book book = new Book(3, "μμ€");

        System.out.println(book);
        System.out.println(book.toString());
    }
}
```

```java
> μμ€ 3
> μμ€ 3
```


<br>

```java
import java.util.Arrays;

public class arraytest {
  public static void main(String[] args) {
	int[] array = new int[] {1,2,3,4};

	System.out.println(array.toString());
	System.out.println(Arrays.toString(array));
  }

}

```

```java
> [I@43a25848] //Object.toString()λ©μλμ κ°μ μΆλ ₯νλ κ²μ΄κ³ , λμ κ°μ²΄μ ν΄μ¬μ½λκ°μ μΆλ ₯νλ€
> [1, 2, 3, 4] //java.util.Araays ν¨ν€μ§λ₯Ό μ΄μ©νμ¬ κ°μ λ¬Έμμ΄ ννλ‘ λ¦¬ν΄
```

<br>

- **equals()** 

  κ°μ²΄κ° κ°μμ§ λΉκ΅νλ λ©μλμ΄λ€. <br>
  μ΅μμ ν΄λμ€μΈ Objectμ ν¬ν¨λμ΄ μκΈ° λλ¬Έμ μ¬μ μνμ¬ μ¬μ©μ΄ κ°λ₯νλ€

  == <br>
  λΉκ΅ μ°μ°μμ΄λ€. <br>
  κΈ°λ³Έμλ£νμ λν΄μλ κ°μ λΉκ΅, μ°Έμ‘°μλ£νμμλ μ£Όμκ°μ λΉκ΅

```java
public class A{
    String name;

    public A(String name){
        this.name = name;
    }
}
```

```java
public class B {
	public static void main(String[] args) {
		A a = new A("Lee");
		A b = new A("Lee");

		System.out.println(a == b);
		System.out.println(a.equals(b));
	}
}
```

```java
> false //κ°κ° μμ±μλ₯Ό μ¬μ©νμ¬ λ§λ€μκΈ° λλ¬Έ
> false //μ€λ²λΌμ΄λ© νμ§ μμμΌλ―λ‘ hashcode() κ°μ λΉκ΅
```

**equalsμ¬μ μ**

```java
public boolean equals(Object obj){
	return this.name == ((A)obj).name;
}
```

```java
> false
> true //λ€λ₯Έ κ°μ²΄λΌλ κ°μ λ¬Έμμ΄μ κ°μ§κ³  μλ€λ©΄ κ°λ€κ³  νλ¨
```

equals λ©μλλ₯Ό Object νμμΌλ‘ λ§€κ°λ³μλ₯Ό λ°λλ€. <br>
Object νμμ A ν΄λμ€μ νλλ₯Ό μ¬μ©ν  μ μκΈ° λλ¬Έμ νλ³νμ ν΄μ€λ€.
