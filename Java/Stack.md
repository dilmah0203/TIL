# ๐ก **Stack**

Stack ํด๋์ค๋ ์๋ฐ์์ ์์์ ์๋ชป ๋ฐ์ ํด๋์ค๋ค. ์๋์ ์ทจ์ง์ธ LIFO๋ฅผ ์๊ฐํ๋ค๋ฉด Vector์ ์ํด์๋ ์๋์ง๋ง ์๋ฐ์ ํ์ ํธํ์ฑ์ ์ํด ์์๊ด๊ณ๋ฅผ ์ ์งํ๊ณ  ์๋ค. 

peek()๋ฉ์๋๋ ๋ฐ์ดํฐ๋ฅผ ๋ฆฌํด๋ง ํ์ง๋ง, pop()์ ์ง์ฐ๊ณ  ๋ฆฌํดํ๋ค๋ ์ฐจ์ด์ ์ด ์๋ค.

<br>

```java
Stack<Integer> intStack = new Stack<Integer>();
  for (int loop = 0; loop < 3; loop++) {
      intStack.push(loop);
      System.out.println(intStack.peek());
  }
  System.out.println(intStack.size()); //3
```

```java
Stack<Integer> intStack = new Stack<Integer>();
  for (int loop = 0; loop < 3; loop++) {
      intStack.push(loop);
      System.out.println(intStack.pop());
  }
  System.out.println(intStack.size()); //0
```
<br>

Vector๋ get()๊ณผ set()์ญํ ์ ํ๋ ๋ชจ๋  ๋ฉ์๋์ synchronized ํค์๋๊ฐ ๋ถ์ด ์๋ค. ๋ฉํฐ์ค๋ ๋ ํ๊ฒฝ์ด ์๋ ๋ ์ฌ์ฉํ๋ฉด lock์ด๋ผ๋ ์์ ๋๋ฌธ์ ๋ง์ ์ค๋ฒํค๋๊ฐ ๋ฐ์ํด ์ฑ๋ฅ์ ์ ํ์ํฌ ์ ์๋ค. ๋ฐ๋ผ์ Vector๋ ํน์  ์ํฉ์์๋ง ์ต์ ์ผ๋ก ๋์ํ๊ฒ ๋๊ณ , ์ด๋ค ์ํฉ์์๋ ๊ทธ๋ ์ง ์๊ฒ ๋๋ฏ๋ก ํจ์จ์ ์ธ Thread-safe ์ปฌ๋ ์์ด๋ผ๊ณ  ํ  ์ ์๋ค.

๊ทธ๋ผ ์ด๋ค ์ปฌ๋ ์์ ์ฐ๋๊ฒ ์ข์๊ฐ?

ArrayList๋ฅผ ์ฌ์ฉํ๋ฉด๋๋ค.

```java
ArrayList<T> al = new ArrayList<>(Collections.synchronizedList());
```

์ด์๊ฐ์ด ArrayList์ ์์ฑ์์ ๋งค๊ฐ๋ณ์๋ก Collections.synchronizedList()๋ฅผ ๋๊ฒจ์ฃผ๊ฒ๋๋ฉด thread-safeํ ArrayList๋ฅผ ์ฌ์ฉํ  ์ ์๋ค.

<br>

Stack์ด ์ฌ์ฉ๋์ง ์์์ผ ํ๋ ์ด์ ๋ Vector์ ๊ฒฝ์ฐ์ ๊ฐ๋ค. Vector๋ฅผ ์์๋ฐ์์ผ๋ก์จ Stack์ Vector์ ๊ธฐ๋ฅ์ ์ ๋ถ ์ฌ์ฉํ  ์ ์๊ฒ ๋๋ฏ๋ก ์๋ฒฝํ LIFO ๊ตฌ์กฐ๋ฅผ ๊ฐ์ง ์ ์๋ค. ArrayDeque๋ Thread safe ํ์ง ์๋ค๋ ๋จ์ ์ด ์์ง๋ง LIFO ๊ตฌ์กฐ์ ์ ํฉํ๋ค.
