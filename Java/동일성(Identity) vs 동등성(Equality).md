# π‘ **λμΌμ±(Identity) vs λλ±μ±(Equality)**

> **λμΌμ±**μ μ£Όμκ° κ°μμ μλ―Ένκ³ , **λλ±μ±**μ κ°μ²΄κ° κ°μμ μλ―Ένλ€. <br>
> μλ°μμ ==λ λμΌμ±, equalsλ λλ±μ±μ λΉκ΅νλ€.

<br>

**Primitive Type**

Primitive Typeμ κ°μ²΄κ° μλκΈ° λλ¬Έμ λλ±μ± λΉκ΅λ₯Ό ν  μ μμΌλ©°, λμΌμ± λΉκ΅λ λ³μμ κ°μΌλ‘ λΉκ΅νλ€.

<br>

**Reference Type**

```java
String str1 = new String("Lee");
String str2 = new String("Lee");

System.out.println(str1 == str2); //false
System.out.println(str1.equals(str2)); //true
```

new μμ½μ΄λ₯Ό ν΅ν΄ μλ‘ λ€λ₯Έ κ°μ²΄λ₯Ό λ©λͺ¨λ¦¬μ ν λΉνμμΌλ―λ‘ **λμΌνμ§ μλ€.** <br>
νμ§λ§ λ κ°μ²΄μ λ΄μ©μ κ°μΌλ―λ‘ **λλ±νλ€.**

<br>

Objectν΄λμ€μ equals()λ©μλλ λ€μκ³Ό κ°μ΄ κ΅¬νλμ΄μλ€.

```java
public boolean equals(Object obj) {
    return (this == obj);
}
```

λ§€κ°λ³μλ‘ μ λ¬λ κ°μ²΄λ₯Ό == μ°μ°μλ‘ λΉκ΅νμ¬ λ¦¬ν΄νλ€. μ¦ μ€λ²λΌμ΄λ©νμ§ μκ³  μ¬μ©ν  κ²½μ° λμΌμ±μ λΉκ΅νκ² λλ€. <br>
λ°λΌμ λλ±μ± λΉκ΅λ₯Ό μν΄μλ equals λ©μλλ₯Ό Override ν΄μΌνλ€.

<br>

```java
public boolean equals(Object anObject) {
    if (this == anObject) {
        return true;
    }
    if (anObject instanceof String) {
        String anotherString = (String)anObject;
        int n = value.length;
        if (n == anotherString.value.length) {
            char v1[] = value;
            char v2[] = anotherString.value;
            int i = 0;
            while (n-- != 0) {
                if (v1[i] != v2[i])
                    return false;
                i++;
            }
            return true;
        }
    }
    return false;
    }
```

String ν΄λμ€λ equals()λ₯Ό μ¬μ μ νλ€. ==λ₯Ό ν΅ν΄ λμΌμ±μ νλ¨νκ³ , λμΌνμ§ μλ€λ©΄ StringμΈμ§ νλ¨ν λ€ λ¬Έμ νλνλλ₯Ό λΉκ΅νλ€. <br>
λͺ¨λ  λ¬Έμκ° κ°λ€λ©΄ λλ±νλ€κ³  νλ¨νλ€.

<br>

**equals()μ hashcode()**

- equals() : λλ±μ± λΉκ΅

- hashcode() : λμΌμ± λΉκ΅

equals()λ₯Ό overrideν  λμλ hashcode()λ κ°μ΄ overrideν΄μΌνλ€. μλλ©΄ equals()λΉκ΅λ₯Ό ν΅ν΄ κ°μ²΄κ° κ°μλ μ£Όμ κ°μ κ°μ§ μμ μλ μκΈ° λλ¬Έμ΄λ€.


```java
public class Example {
   private int number;

    public Example(int number){
       this.number = number;
   }

    @Override
    public boolean equals(Object o) {
        if (this == o) //μ£Όμκ° κ°μΌλ©΄ true
            return true;
        if (o == null || getClass() != o.getClass()) //objκ° nullμ΄κ±°λ κ°μ μλ£νμ΄ μλλ©΄ false
            return false;
        Example example = (Example)o; //κ°μ ν΄λμ€μ΄λ―λ‘ ν λ³ν
        return Objects.equals(number, example.number);
    }

    @Override
    public int hashCode() {
        return Objects.hash(number);
    }
}
```

```java
public class Main {
    public static void main(String[] args){
        Example ex = new Example(32);
        Example ex2 = new Example(32);

        System.out.println("hashcode : "+ex.hashCode());
        System.out.println("hashcode : "+ex2.hashCode());
        System.out.println("equals : "+ ex.equals(ex2));
    }
}
```

