# π‘ **BigIntegerμ BigDecimal**

> java.math ν¨ν€μ§

**BigInteger**

- longνμ λλ λ²μμ μ μν κ°μ λ€λ£° λ μ¬μ©

- μ¬μΉμ°μ°μ ν  μ μμΌλ©°, λ¬Έμμ΄μ μ΄μ©νμ¬ κ°μ νν

- κΈ°νΈλ‘ μ§μ  μ°μ°ν  μ μκΈ° λλ¬Έμ add(), subtract(), multiply(), divide(), compareTo() μ κ°μ λ΄μ₯ λ©μλλ₯Ό μ¬μ©.

```java
    BigInteger e1 = new BigInteger("100000");
    BigInteger e2 = new BigInteger("10000");

    System.out.println("λ§μ :" + e1.add(e2));
    System.out.println("λΊμ :" + e1.subtract(e2));
    System.out.println("κ³±μ :" + e1.multiply(e2));
    System.out.println("λλμ :" + e1.divide(e2));
    System.out.println("λλ¨Έμ§ :" + e1.remainder(e2));

    int compare = e1.compareTo(e2); //λ μ λΉκ΅, κ°μΌλ©΄ 0 λ€λ₯΄λ©΄ -1λ₯Ό λ°ν
```

<br>

**BigDecimal**

- μ€μν κ°μ λ€λ£° λ μ¬μ©

- arithmetic(μ°μ°), scale manipulation(λ²μ μ‘°μ ), rounding(λ°μ¬λ¦Ό), comparison(λΉκ΅), hashing(ν΄μ±), and format conversion(ν¬λ©§ λ³κ²½)μ μ§μ

- κ³μ° μλλ double, floatλ₯Ό μ¬μ©νλ κ²½μ°λ³΄λ€ λλ¦¬μ§λ§ μ λ°ν κ²°κ³Όλ₯Ό λ³΄μ₯


```java
    BigDecimal e1 = new BigDecimal("123.45");
     
    int a = e1.intValue(); // ν λ³ν
    long b = e1.longValue();
    float c = e1.floatValue();
    double d = e1.doubleValue();
    
    System.out.println(e1.scale()); //2, μμμ  μ²«μ§Έ μλ¦¬λΆν° 0μ΄μλ μλ‘ λλλ μλ¦¬μ
    System.out.println(e1.precision()); //5, μ λ°λ. 0μ΄μλμκ° μμνλ μμΉλΆν° 0μ΄μλ μλ‘ λλλ μλ¦¬μ
    
    int compare = bigNumber1.compareTo(bigNumber2); //λ μ λΉκ΅ : -1
```
