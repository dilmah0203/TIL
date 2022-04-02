# 💡 **File 클래스**

Java 7 부터는 java.nio.file 패키지에 있는 Files 클래스에서 File 클래스의 메소드를 대체하여 제공한다.
**File 클래스**는 객체를 생성하여 데이터를 처리하는 반면, **Files 클래스**는 모든 메소드가 **static**으로 선언되어 있어 별도의 객체를 생성하지 않아도 된다.

<br>

**File 클래스의 파일 경로**

C:\java\text와 같이 경로를 나타낼 때에는 두 개의 역슬래시를 연달아서 \\로 사용해야 한다. 디렉터리 구분의 모호함을 없애기 위해 File 클래스에 seperator 라는 static 변수가 존재한다. 

```java
String pathName = File.seperator + "java" + File.seperator + "text";
```

