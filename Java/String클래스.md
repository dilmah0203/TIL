# ๐ก **String ํด๋์ค**

String ํด๋์ค๋ ๋ฌธ์์ด๊ณผ ๊ด๋ จ๋ ์์์ ํ  ๋ ์ ์ฉํ๊ฒ ์ฌ์ฉํ  ์ ์๋ ๋ฉ์๋๋ค์ด ํฌํจ๋์ด ์๋ค.


๋ค์ ๊ฒฐ๊ณผ๋ ์๋ก ๊ฐ๋ค.

```java
String str = "abc";

char data[] = {'a', 'b', 'c'};
String str = new String(data);
```

<br>

**String ๋ฌธ์์ด์ byte๋ก ๋ณํ**

**getBytes()**

๊ฐ์ ํ๋ก๊ทธ๋จ ๋ด์์ ๋ฌธ์์ด์ byte ๋ฐฐ์ด๋ก ์ ์ฅํ๋ฉฐ, 
getBytes์ ๋งค๊ฐ ๋ณ์๋ฅผ ํตํด ์บ๋ฆญํฐ ์์ ์ง์ ํ  ์ ์๋ค.


```java
public class Example {

    public static void main(String[] args) {
        Example e = new Example();
        e.convert();
    }

    public void convert() {
        try {
            String ex1 = "์ด์ฃผ์ "; //String ๊ฐ์ฒด ์์ฑ
            byte[] array = ex1.getBytes(); //๋ฌธ์์ด์ ๋ฐฐ์ด๋ก ์ ์ฅ
            for (byte data : array) {
                System.out.print(data + " ");
            }
            System.out.println();
            String ex2 = new String(array); //byte ๋ฐฐ์ด๋ก Sring ๊ฐ์ฒด๋ฅผ ์์ฑ
            System.out.println(ex2);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```  
<br>


**String์ ๋ด์ฉ์ ๋น๊ต/๊ฒ์**

**length()**

int๋ก ๋ฌธ์์ด์ ๊ธธ์ด๋ฅผ ๋ฆฌํดํ๋ฉฐ ๊ณต๋ฐฑ๋ ๊ธธ์ด์ ํฌํจ๋๋ค.

```java
public void checkLength(){
        String s = "Ju Seon";
        System.out.println(s.length()); //7
}
```
<br>


**isEmpty()**

๋ฌธ์์ด์ด ๋น์ด์์ ๊ฒฝ์ฐ true๋ฅผ ๋ฆฌํดํ๋ค.

```java
public void checkEmpty(){
        String s = "Ju Seon";
        System.out.println(s.isEmpty()); //false
}
```
<br>

**equals()**

๋ฌธ์์ด์ด ๊ฐ์ ๊ฒฝ์ฐ true๋ฅผ ๋ฆฌํดํ๋ค.
๋ฉ์๋ ์ด๋ฆ์ IgnoreCase๊ฐ ๋ถ์ ๊ฒฝ์ฐ, ๋์๋ฌธ์ ๊ตฌ๋ถ์ ํ์ง ์๋๋ค.

```java
public void checkEquals(){
        String s1 = "Ju Seon";
        String s2 = "Ju Seon";
        if(s1==s2){
            System.out.println("same"); //same
        }else {
            System.out.println("different");
        }
        if(s1.equals(s2)){
            System.out.println("equals"); //equals
        }
}

public void checkEquals(){
        String s1 = "Ju Seon";
        String s2 = new String("Ju Seon");
        if(s1==s2){
            System.out.println("same");
        }else {
            System.out.println("different"); //different
        }
        if(s1.equals(s2)){
            System.out.println("equals"); //equals
        }
}
```

<br>

**compareTo()**

๋ณดํต ์ ๋ ฌ ์์ ์ฌ์ฉํ๋ฉฐ ๋งค๊ฐ ๋ณ์์ String ๊ฐ์ฒด๊ฐ ์ํ๋ฒณ ์์ผ๋ก ์์ ์์ผ๋ฉด ์์๋ฅผ, ๋ค์ ์์ผ๋ฉด ์์๋ฅผ ๋ฆฌํดํ๋ค. ์ฐจ์ด๋๋ ๋งํผ ์ซ์๊ฐ์ ์ปค์ง๋ค.

```java
public void checkCompareTo(){
        String a = "a";
        String b = "b";
        String c = "c";
        System.out.println(b.compareTo(a)); //1
        System.out.println(b.compareTo(c)); //-1
        System.out.println(a.compareTo(c)); //-2
}
```
<br>

**startsWith()**

๋งค๊ฐ ๋ณ์๋ก ๋๊ฒจ์ค ๊ฐ์ผ๋ก ์์ํ๋์ง ํ์ธํ๋ค.

```java
public static void main(String[] args) {
        Example e = new Example();
        
        String address[] = new String[]{"์์ธ์", "์์ธ", "์์ธ์์ฒญ"};
        e.checkstartsWith(address);
}

public void checkstartsWith(String[] address) {
        String start = "์์ธ";
        int startCount = 0;
        for (String addresses : address) {
            if (addresses.startsWith(start)) {
                startCount++;
            }
        }
        System.out.println(startCount); //3
}
```
<br>

**contains()**

๋งค๊ฐ ๋ณ์๋ก ๋์ด์จ ๊ฐ์ด ๋ฌธ์์ด์ ์กด์ฌํ๋์ง ํ์ธํ๋ค.

```java
public void checkContains(String[] address) {
        String text = "์ธ";
        int containCount = 0;
        for (String addresses : address) {
            if (addresses.contains(text)) {
                containCount++;
            }
        }
        System.out.println(containCount); //3
}
```
<br>

**regionMatches()**

ํน์  ์์ญ์ด ๋งค๊ฐ ๋ณ์๋ก ๋์ด์จ ๋ฌธ์์ด๊ณผ ๋์ผํ์ง ํ์ธ ํ boolean ํ์์ผ๋ก ๋ฆฌํดํ๋ค. ์ฒซ ๋ฒ์งธ ๋งค๊ฐ ๋ณ์๊ฐ true์ผ ๊ฒฝ์ฐ ๋์๋ฌธ์ ๊ตฌ๋ถ์ ํ์ง ์๋๋ค.

```java
 public void checkMatch(){
        String text = "This is a Java";
        String check1 = "is";
        String check2 = "java";
        System.out.println(text.regionMatches(true, 2, check1, 0, 2)); //true
        System.out.println(text.regionMatches(false, 10, check2, 0, 4)); //false
}
```

<br>

**String์์ ์์น๋ฅผ ์ฐพ์๋ด๋ ๋ฉ์๋**

**indexOf()**

์์์๋ถํฐ ํน์  ๋ฌธ์์ด์ด๋ char๋ฅผ ์ฐพ๋๋ค. ์์ผ๋ฉด -1์ ๋ฆฌํดํ๋ค. lastIndexOf()๋ ๋ค์์๋ถํฐ ์ฐพ๋๋ค.

```java
public void checkIndex() {
        String text = "My name is Juseon.";
        System.out.println(text.indexOf('s')); //9
        System.out.println(text.indexOf(" J")); //10
        System.out.println(text.indexOf('s', 11)); //13
}
```

<br>

**String์์ ๊ฐ์ ์ผ๋ถ๋ฅผ ์ถ์ถ**

**charAt()**

ํน์  ์์น์ char ๊ฐ์ ๋ฆฌํดํ๋ค.

```java
public void checkCharAt(){
        String text = "Ju Seon";
        System.out.println(text.charAt(3)); //3
}
```
<br>

**substring()**

๋์ ๋ฌธ์์ด์ ์๋ผ String์ผ๋ก ๋ฆฌํดํ๋ค.

```java
public void checkSubString(){
        String text = "Ju Seon";
        String sub = text.substring(3);
        System.out.println(sub); //์ธ๋ฑ์ค 3๋ถํฐ ์๋ฅธ๋ค. Seon
}
```
<br>

**String์์ ๊ณต๋ฐฑ์ ์ ๊ฑฐ**

**trim()**

๋์ ๋ฌธ์์ด์ ๋งจ ์๊ณผ ๋ค์ ์๋ ๊ณต๋ฐฑ๋ค์ ์ ๊ฑฐํ ๋ฌธ์์ด์ ๋ฆฌํดํ๋ค. 

```java
public void checkTrim(){
        String text = "  My name is  ";
        String result = text.trim();
        System.out.println(text);
        System.out.println(result);
}
```

<br>


**String์ ๋ถ๋ณ ๊ฐ์ฒด๋ค**

String์ ํ ๋ฒ ๋ง๋ค์ด์ง๋ฉด ๋ณ๊ฒฝ๋  ์ ์๋ค. ๋ฌธ์์ด์ ๋ํ๊ฒ ๋๋ฉด ์๋ก์ด String ๊ฐ์ฒด๊ฐ ์์ฑ๋๊ณ , ๊ธฐ์กด ๊ฐ์ฒด๋ ๋ฒ๋ ค์ง๋ค. ๊ทธ๋ฆฌ๊ณ  GC์ ๋์์ด ๋๋ค.

์ด๋ฌํ String ํด๋์ค์ ๋จ์ ์ ๋ณด์ํ๊ธฐ ์ํ StringBuffer์ StringBuilder๊ฐ ์๋ค. StringBuffer๋ Thread safeํ๋ฉฐ, StringBuilder๋ Thread safeํ์ง ์๋ค. ์๋๋ StringBuilder ํด๋์ค๊ฐ ๋น ๋ฅด๋ค. ๋ ํด๋์ค๋ ๋ฌธ์์ด์ ๋ํ  ์์ ์๋ก์ด ๊ฐ์ฒด๋ฅผ ์์ฑํ์ง ์๋๋ค.

  **๊ทธ๋ผ ์ธ์  String์ ์ฌ์ฉํ ๊น?**

  ๋ถ๋ณ์ฑ์ ๊ฐ์ง๊ธฐ ๋๋ฌธ์ ๋ณํ์ง ์๋ ๋ฌธ์์ด์ ์์ฃผ ์ฝ๋ ๊ฒฝ์ฐ ์ฌ์ฉํ๋ค. ๋ฌธ์์ด ์ถ๊ฐ์ ์์  ์ญ์  ๋ฑ์ ์ฐ์ฐ์ด ๋น๋ฒํ๊ฒ ๋ฐ์ํ๋ ๊ฒฝ์ฐ String์ ์ฌ์ฉํ๊ฒ ๋๋ฉด ํ์ ๋ง์ ๊ฐ๋น์ง๊ฐ ์์ฑ๋๋ฏ๋ก StringBuffer / StringBuilder ํด๋์ค๋ฅผ ์ฌ์ฉํ๋๊ฒ ์ข๋ค.

<br>


์ฐธ๊ณ  

https://docs.oracle.com/javase/8/docs/api/java/lang/String.html
