# 📚 ArraysList (2025.04.23)
___

## 🌟 오늘 배운 내용
- 컬렉션 프레임웍
- ArraysList 개념
- ArraysList 생성
- ArraysList 메서드

<br/>

## 🔎 요약 정리

___

### ✅ 컬렉션 프레임웍

- 데이터 그룹을 저장하는 클래스들을 표준화한 설계
- 핵심 인터페이스
    - List : 순서가 있는 데이터의 조합. 데이터 중복 허용.
    - Set : 순서를 유지하지 않는 데이터의 조합.
    - Map : 키와 값의 쌍으로 이루어진 데이터의 조합.
        - 키는 중복 X, 값은 중복 허용.
- List와 Set은 비슷한 부분이 많아 공통 부분을 뽑아 Collection 인터페이스로 정의 가능하다

### ✅ ArraysList

- 자바에서 가장 많이 사용되는 컬렉션 클래스.
- List 인터페이스를 구현 → 데이터 저장순서 유지, 중복 허용한다
- Object 배열을 이용해서 데이터를 순차적으로 저장한다.
    - 객체의 최고조상인  Object이기 때문에 모든 종류의 객체를 담을 수 있다.
- 배열을 이용하므로 인덱스를 이용해 요소에 빠르게 접근 가능하다
    - 삽입/삭제보다는 조회에 사용하는 것이 좋다.
        - 데이터 사이에 빈 공간을 허락하지 않는다
- 크기가 가변적이다.
- 적은 양의 데이터만 쓸 경우에는 배열을 이용하는 것이 좋다.
    - 객체를 데이터로 사용하기 때문에 배열에 비해 메모리가 커진다.

### ✅ArrayList 생성

- 먼저 패키지를 추가해야 한다.

```java
import java.util.ArraysList;
```

- 아래와 같이 생성할 수 있다.

```java
ArrayList<Integer> list1 = new ArrayList<Integer>(); // 타입 지정
ArrayList<Integer> list2 = new ArrayList<>(); // 타입 생략 가능
ArrayList<Integer> list3 = new ArrayList<>(10); // 초기 용량(Capacity) 설정
ArrayList<Integer> list4 = new ArrayList<>(list1); // 다른 Collection값으로 초기화
ArrayList<Integer> list5 = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5)); // Arrays.asList()
```

### ✅ ArraysList 메서드

- 데이터 추가
    - add는 단일 값, addAll은 컬렉션을 받아서 그 안에 요소들을 한 번에 추가해주는 메서드.

    ```java
    list1.add(1);              // 데이터 추가
    list1.add(2, 5);           // 2번째에 5 저장
    
    list2.addAll(list5);       // list5의 모든 요소를 list2 끝에 추가
    list2.addAll(2, list5);    // 인덱스 2 위치에 list5의 요소들을 순서대로 삽입
    ```

- 데이터 삭제
    - remove는 지정된 위치 삭제, clear는 완전히 삭제하는 메서드.

    ```java
    list1.remove(1);                 //2번 인덱스의 데이터 삭제
    list1.remove(list.indexOf(1));   //1을 가지고 있는 인덱스를 리턴하여 삭제
    list1.clear();                   //리스트의 모든 데이터 삭제
    ```

- 데이터 조회
    - get는 지정된 위치에 저장된 객체 반환 메서드

    ```java
    System.out.println(list.get(3));    //3번 인덱스에 위치한 값 출력
    ```

- 데이터 포함 확인
    - indexOf는 지정된 객체가 지정된 위치를 반환, contains는 포함되어있는지 확인하는 메서드

    ```java
    int index = list.indexOf(2);          //원하는 값의 인덱스를 리턴, 없는 경우 -1 리턴, 1
    boolean contains = list1.contains(3);  // 특정 값이 있는지 확인, true
    ```

- 데이터출력
    - iterator는 ArraysList의 iterator객체를 반환하는 메서드

    ```java
    System.out.println(list5);             //list 전체 출력
    System.out.println(list5.get(3));      //3번 인덱스에 위치한 값 출력
    
    for (int item: list5) {          
    	System.out.print(item + " ");          //1 2 3 4 5 
    }
    
    Iterator iter = list5.iterator();           //Iterator를 사용하는 경우
    while (iter.hasNext()) {
    	System.out.print(iter.next() + " ");   //1 2 3 4 5 
    }
    ```

- 그 외 메서드
    - int size() : 저장된 객체의 개수 반환
    - void sort(Comparator c) : 지정된 정렬기준(c)으로 ArraysList를 정렬
    - Object[] toArray() : ArraysList에 저장된 모든 객체들을 객체배열로 반환
    - Object[] toArray(Object[] a) : ArraysList에 저장된 모든 객체들을 객체배열 a에 담아 반환