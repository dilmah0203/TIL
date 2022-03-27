# 💡 **List**

**배열**

동일한 자료형의 데이터를 연속된 공간에 저장하는 구조로, 다음과 같은 단점이 있다.

- 자료형이 같아야한다
- 크기가 고정되어 있다

이러한 단점을 보완하기 위해 자바에서 자료구조를 제공하며 다음과 같이 분류할 수 있다.

<br>

![img](https://media.vlpt.us/images/rssungjae/post/c50f0388-f6b6-4eff-aecf-2469b14aec87/image.png)

<br>

**List**

데이터가 순서가 있으며 중복을 허용한다

**ArrayList**

- 내부적으로 배열을 이용하여 데이터를 저장한다
- 생성자를 통해 배열의 크기를 설정할 수 있다
- Thread safe하지않다

<br>

ArrayList 객체 선언 시 초기 크기는 10이다. 예를들어 String인 객체를 담는 크기가 30인 ArrayList를 생성할 때에는 다음과 같이 사용한다.

```java
ArrayList<String> list = new ArrayList<String>(30);
```

<br>

list2를 list로 치환할 경우, list2가 list의 값과 주소까지 사용하게 된다.

```java
 ArrayList<String> list = new ArrayList<String>();
        list.add("A");

        ArrayList<String> list2 = list;
        list.add("B");
        for (String data : list2) {
            System.out.print(data); //A B
        }
```

<br>

ArrayList 객체에 있는 데이터를 배열로 뽑아낼 경우 toArray()메소드를 사용한다. 매개 변수가 없는 toArray() 메소드는 Object 타입 배열로만 리턴을 하기 때문에 제네릭을 사용하여 선언한 ArrayList 객체는 매개변수로 타입을 정해준다.

```java
  ArrayList<String> list = new ArrayList<>();
        list.add("C");
        list.add("D");
        String[] array = new String[0];
        String[] array2 = list.toArray(array);

        for (String data : array2) {
            System.out.print(data);
        }
```
ArrayList 객체의 크기가 매개변수로 넘어간 배열 객체의 크기보다 클 경우 배열의 모든 값이 null이 된다. 따라서 toArray() 메소드에 크기가 0인 배열을 넘겨주는 것이 좋다.
