# ๐ก **Reader์ Writer**

Reader์ Writer์ **char** ๊ธฐ๋ฐ์ ๋ฌธ์์ด์ ์ฒ๋ฆฌํ๊ธฐ ์ํ ํด๋์ค์ด๋ค.

```java
public abstract class Reader
extends Object
implements Readable, Closeable
```

```java
public abstract class Writer
extends Object
implements Appendable, Closeable, Flushable
```

Appendable ์ธํฐํ์ด์ค๋ ๊ฐ์ข ๋ฌธ์์ด์ ์ถ๊ฐํ๊ธฐ ์ํด ์ ์ธ๋์๋ค.
Writer์ ์๋ write()๋ append()๋ฉ์๋๋ฅผ ์ฌ์ฉํ์ฌ ๋ฐ์ดํฐ๋ฅผ ์ธ ๊ฒฝ์ฐ, ๋ฉ์๋๋ฅผ ํธ์ถํ  ๋๋ง๋ค ํ์ผ์ ์ฐ๊ธฐ ๋๋ฌธ์ ๋งค์ฐ ๋นํจ์จ์ ์ด๋ค. ์ด๋ฌํ ๋จ์ ์ ๋ณด์ํ๊ธฐ ์ํ BufferedWriter ํด๋์ค๊ฐ ์๋ค.
