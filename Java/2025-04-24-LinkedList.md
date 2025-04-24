# 📚 LinkedList (2025.04.24)
___

## 🌟 오늘 배운 내용
- LinkedList 개념
- 단방향 연결 리스트
- 양방향 연결 리스트
- LinkedList 생성
- LinkedList 메서드
- ArraysList vs LinkedList 

<br/>

## 🔎 요약 정리

___

### ✅ LinkedList 

자바의 컬렉션 중 하나로, 노드와 포인터로 이루어져 있는 클래스.

- 노드끼리의 주소포인터를 서로 가르키며 참조함으로써 이어지는 구조.
    - 여기서 노드는 하나의 객체라 보면된다.
- 객체 생성→ 노드끼리 주소 서로 참조 → 연결형태 구성
    - 객체가 생성될 때 주소도 생기게 된다.

```java
class Node{
	Node next;    // 다음 노드 주소 저장
	int data;     // 데이터
};
```




### ✅ 단방향 연결 리스트

다음 노드를 가리키기 위한 포인터 필드(next)만 가지고 있는 리스트
- 현재 요소에서 이전 요소로 접근해야할 때 매우 부적합하다



### ✅ 양방향 연결 리스트

단방향 연결 리스트에서 이전 노드 주소를 담고 있는 포인터 필드(prev)가 추가된 리스트
- 역순으로도 검색이 가능하다
- 각 요소에 대한 접근과 이동이 쉽기 때문에 기본적으로 많이 사용된다
    - ex) TV 채널 순회, 오디오 플레이어



### ✅ LinkedList 생성

- 먼저 아래 import문을 추가해야 한다.
    ```java
    import java.util.LinkedList;
    ```

- 객체 생성
    - 컬렉션을 포함하는 LinkedList객체를 생성할 수 있다



### ✅ LinkedList 메서드

- 데이터 추가
    - add는 단일 값, addAll은 컬렉션 추가라고 보면된다.
    - 인덱스를 지정안하면 맨 마지막에 추가한다.

    ```java
    list1.add(1);
    list1.add(2);
    list1.add(1, 4);
    
    list2.addAll(list1);
    list2.addAll(2, list1);
    ```

- 데이터 삭제

    ```java
    list1.remove(1);        // 인덱스 1의 데이터 삭제
    list1.remove("2");      // "2"인 데이터와 일치하는 데이터 삭제
    list1.removeAll(list2); // list1의 데이터에서 list2와 일치하는 데이터 삭제
    list1.clear();          // 완전히 삭제
    ```

- 데이터 조회
    - get는 지정된 위치에 저장된 객체 반환 메서드
    - indexOf는 지정된 객체가 저장된 위치를 반환하는 메서드
    - contains는 지정된 객체가 LinkedList에 포함되어 있는지 확인, containsAll은 모든 요소가 포함되어있는지 확인하는 메서드

    ```java
    System.out.println(list1.get(1));             // 인덱스 1에 저장된 객체 반환
    
    System.out.println(list1.indexOf("1"));       // list1안에 "1"의 위치를 반환한다.(앞에서부터 검색)
    System.out.println(list1.lastIndexOf("1"));       // list1안에 "1"의 위치를 반환한다.(뒤에서부터 검색)
    
    System.out.println(list1.contains("1"));      // list1안에 "1"이 있는지 확인
    System.out.println(list2.containsAll(list1)); // list2에 list1의 모든 노드가 포함되어 있는지 확인
    ```


- 그 외 메서드
    - int size() : 저장된 객체의 개수 반환
    - boolean isEmpty() : 비어있는지 확인
    - Object[] toArray() : 저장된 모든 객체들을 객체배열로 반환
    - Object element() : 첫 번째 노드를 반환
    - List subList(int fromIndex, int toIndex) : formIndex부터 toIndex 사이에 저장된 객체 List로 반환

    ```java
    LinkedList list3 = new LinkedList();
    list3 = list1.subList(1, 3);
    ```

    - ListIterator iterator() : LinkedList의 iterator객체를 반환
        - 인덱스를 매개변수로 넣으면 지정된 위치부터 시작해 반환



### ✅ ArraysList vs LinkedList

- List를 구현한 컬렉션이기 때문에 데이터의 저장순서가 유지되고 중복혀용한다.
- 중간 데이터를 추가/삭제 하는 경우에는 LinkedList가 빠르다.

|  | ArrayList | LinkedList |
| --- | --- | --- |
| 구조 | 배열 | 노드와 포인터 |
| 검색 | 인덱스로 빠르게 검색 가능하므로 LinkedList보다 빠르다 | 처음 또는 끝에서부터 순차적으로 검색 수행한다 |
| 추가/삭제 시 시간복잡도 | 데이터들을 한 칸씩 이동시켜야 하므로 O(n)이다 | 이전 노드와 이후 노드의 포인터만 연결하면 되므로 O(1)이다 |