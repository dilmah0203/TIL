# ๐ก **Pass by value์ Pass by reference**

<br>

- "Pass by value"

  - ๊ฐ๋ง ์ ๋ฌ
  - ๊ธฐ๋ณธ ์๋ฃํ์ ๋งค๊ฐ๋ณ์๋ก ๋๊ฒจ์ค ๋

<br>

```java
public class Main {
  public void swap(int x, int y){
        int temp = x;
        x = y;
        y = temp;
  }

  public static void main(String[] args){
        Main m = new Main();
        
        int a = 3;
        int b = 5;

        System.out.println("a ="+a+","+"b ="+b);
        m.swap(a,b);
        System.out.println("a ="+a+","+"b ="+b);
  }
}
```

```java
> a =3,b =5
> a =3,b =5
```

<br>

- "Pass by reference"

  - ์ฐธ์กฐ(์ฃผ์)๋ฅผ ์ ๋ฌ
  - ๋ฉ์๋์์ ํ๋ผ๋ฏธํฐ ์์  ์ ์๋ณธ ๋ฐ์ดํฐ์๋ ์ํฅ์ด ์๋ค

<br>

```java
public class MemberDTO {
    public String name;
    public String phone;
    public String email;
    public MemberDTO(String name){
        this.name=name;
    }
}
```

```java
public class Main {
    public void callPassByReference(){
        MemberDTO member = new MemberDTO("Lee");
        System.out.println("before : "+member.name);
        passByReference(member);
        System.out.println("after : "+member.name);

    }
    public void passByReference(MemberDTO member){
        member.name = "Kim";
        System.out.println("In : "+member.name);
    }
    public static void main(String[] args){
        Main m = new Main();
        m.callPassByReference();
    }
}
```

```java
> before : Lee
> In : Kim
> after : Kim
```

