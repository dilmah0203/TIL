# ๐ก **Map**

Map์ ํค(key)์ ๊ฐ(value)์ผ๋ก ์ด๋ฃจ์ด์ ธ ์๋ค. Map ์ธํฐํ์ด์ค๋ฅผ ๊ตฌํํ ํด๋์ค์๋ HashMap, TreeMap, LinkedHashMap ๋ฑ์ด ์๋ค.

<br>

**HashMap์ ์์ฑ์**

HaspMap์ ๊ฐ์ฒด๊ฐ ๋ค์ด๊ฐ๋ฉด hashCode() ๋ฉ์๋ ๊ฒฐ๊ณผ ๊ฐ์ ๋ฐ๋ฅธ bucket์ด๋ผ๋ ๋ชฉ๋ก ํํ์ ๋ฐ๊ตฌ๋๊ฐ ๋ง๋ค์ด์ง๋ค. ์๋ก ๋ค๋ฅธ ํค๊ฐ ์ ์ฅ๋  ๊ฒฝ์ฐ, hashCode()์ ๊ฐ์ด ๋์ผํ๋ค๋ฉด bucket์ ์ฌ๋ฌ ๊ฐ์ด ๋ค์ด๊ฐ ์ ์๋ค. ๋ฐ๋ผ์ get() ๋ฉ์๋ ํธ์ถ๋ก hashCode()์ ๊ฒฐ๊ณผ๋ฅผ ํ์ธ ํ๊ณ , bucket์ ๋ค์ด๊ฐ ๋ชฉ๋ก์ ๋ฐ์ดํฐ๊ฐ ์ฌ๋ฌ ๊ฐ์ผ ๊ฒฝ์ฐ equals() ๋ฉ์๋๋ฅผ ํตํ์ฌ ๋์ผ ๊ฐ์ ์ฐพ๊ฒ ๋๋ค.

<br>

Collection์์๋ ํด๋น ์์น์ ๊ฐ์ด ์์ ๊ฒฝ์ฐ ์์ธ๊ฐ ๋ฐ์ํ์ง๋ง Map์์๋ ์กด์ฌํ์ง ์๋ ํค๋ก get()์ ํ  ๊ฒฝ์ฐ null์ ๋ฆฌํดํ๋ค. ์ด๋ฏธ ์กด์ฌํ๋ ํค๋ก ๊ฐ์ ๋ฃ์ ๋์๋ ์๋ก์ด ๊ฐ์ผ๋ก ๋์น๋๋ค.

```java
Map<String, String> map = new HashMap<>();
map.put("A", "a");
map.put("C", "c");
System.out.println(map.get("A")); //a
System.out.println(map.get("B")); //null
```
<br>

**HashMap์ ํค๋ฅผ ํ์ธํ๋ ค๋ฉด**

keySet() ๋ฉ์๋๋ฅผ ์ฌ์ฉํ์ฌ ํค๋ฅผ ํ์ธํ  ์ ์๋ค. ๋ฆฌํด ํ์์ Set์ด๋ค. 

```java
Map<String, String> map = new HashMap<>();
map.put("A", "a");
map.put("B", "b");
map.put("C", "c");
Set<String> keySet = map.keySet();
System.out.println(keySet); //[A, B, C]
for (String data : keySet) {
  System.out.print(map.get(data)); //abc
}
```        
<br>

**HashMap์ ๊ฐ์ ํ์ธํ๋ ค๋ฉด**

Set๊ณผ Map์ ๋ฐ์ดํฐ ์์๊ฐ ์ค์ํ์ง ์์ ์๋ฃ ๊ตฌ์กฐ์ด๋ค. ๊ฐ์ฒด์ ๋ด๊ฒจ ์๋ ๊ฐ๋ง ํ์ํ  ๊ฒฝ์ฐ values() ๋ฉ์๋๋ฅผ ์ฌ์ฉํ  ์ ์์ผ๋ฉฐ Collection ํ์์ ๋ชฉ๋ก์ผ๋ก ๋ฆฌํดํ๋ค.

```java
Map<String, String> map = new HashMap<>();
map.put("A", "a");
map.put("B", "b");
map.put("C", "c");
Collection<String> values = map.values();
for (String data : values) {
System.out.print(data); //abc
}
```
Map์ ์ ์ธ๋ Entry ํ์ ๊ฐ์ฒด๋ฅผ ์ฌ์ฉํ์ฌ ๋ฆฌํดํ  ์๋ ์๋ค. Entry๋ ํ๋์ ํค์ ๊ฐ๋ง์ด ์ ์ฅ๋๋ค.

```java
Set<Map.Entry<String, String>> entry = map.entrySet();
for (Map.Entry<String, String> data : entry) {
System.out.println(data);
}
```


