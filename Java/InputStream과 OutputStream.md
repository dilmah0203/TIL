# ๐ก **InputStream๊ณผ OutputStream**

์๋ฐ์ I/O๋ ๊ธฐ๋ณธ์ ์ผ๋ก InputStream๊ณผ OutputStream์ด๋ผ๋ abstract ํด๋์ค๋ฅผ ํตํด ์ ๊ณต๋๋ค. ๋ฐ์ดํฐ๋ฅผ ์ฝ์ ๋์๋ InputStream์ ์์ ํด๋์ค๋ฅผ ํตํด ์ฝ๊ณ , ๋ฐ์ดํฐ๋ฅผ ์ธ ๋์๋ OutputStream์ ์์ ํด๋์ค๋ฅผ ํตํด ์ด๋ค. InputStream๊ณผ OutputStream์ byte๋ฅผ ๋ค๋ฃจ๊ธฐ ์ํ ํด๋์ค์ด๋ค.

<br>

**InputStream**

```java
public abstract class InputStream
extends Object
implements Closeable
```

InputStreamํด๋์ค๋ Closeable ์ธํฐํ์ด์ค๋ฅผ ๊ตฌํํ์ผ๋ฉฐ, ์ด ์ธํฐํ์ด์ค์๋ close()๋ผ๋ ๋ฉ์๋๋ง ์ ์ธ๋์ด ์๋ค. **์คํธ๋ฆผ์์ ์์์ค์ธ ๋์์ ๋ซ๊ณ  ๋ฆฌ์์ค๋ฅผ ํด์ **ํ๋ ๊ฒ์ ์๋ฏธํ๊ณ  close() ๋ฉ์๋๋ฅผ ํธ์ถํ์ฌ ์ด์๋ ๋ฆฌ์์ค๋ฅผ ๋ซ์ ์ฃผ์ด์ผ ํ๋ค.

๋ฐ์ดํฐ๋ฅผ ์ฝ์ ๋๋ read() ๋ฉ์๋๋ฅผ ์ฌ์ฉํ๋ฉฐ ์ ์ผํ abstract ๋ฉ์๋๋ค.

<br>

**OutputStream**

```java
public abstract class OutputStream
extends Object
implements Closeable, Flushable
```

OutputStream์ ๋ฉ์๋๋ก๋ write(), flush(), close()๊ฐ ์๋ค.
write()์ ๊ฒฝ์ฐ ๋งค๊ฐ๋ณ์๋ก ๋ฐ์ ๋ฐ์ดํธ๋ฅผ ์ ์ฅํ๋ฉฐ, flush()๋ Flushable ์ธํฐํ์ด์ค์ ์ ์ธ๋์ด ์๋ ๋ฉ์๋๋ก ๋ฒํผ์ ๋๊ธฐํ๊ณ  ์๋ ๋ฐ์ดํฐ๋ฅผ ๊ฐ์ ๋ก ์ฐ๋๋ก ํ๋ค.