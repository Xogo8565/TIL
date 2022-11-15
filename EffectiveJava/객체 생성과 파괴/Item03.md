Item 3 privat 생성자나 열거 타입으로 싱글턴임을 보장하라
===================================
#### 멤버 필드를 이용한 방식
```Java
public class Elvis {
  public static final Elvis Instance = new Elvis();
  private Elvis () { ... }

  public void leaveTheBuilding() { ... }
}
```
- 리플렉션 API 를 통한 private 생성자 호출 문제 존재.
- 생성자 수정 -> 두번째 객체가 생성되면 예외를 던지도록

#### 정적 팩토리를 이용한 방식
```Java
public class Elvis {
  private static final Elvis Instance = new Elvis();
  private Elvis () { ... }
  public static Elvis getInstance() { return INSTANCE; }

  public void leaveTheBuilding() { ... }
}

```
- API 를 변경하지 않고도 싱글턴이 아니게 변경 가능
- 정적 팩토리를 제네릭 싱글턴 팩토리로 만들 수 있다

#### 열거타입을 이용한 방식
```Java
public class Elvis {
  INSTANCE;
  
  public void leaveTheBuilding() { ... }
}

```
- 대부분의 상황에서는 원소가 하나뿐인 열거 타입이 싱글턴을 만드는 가장 좋은 방법. 단, 만드려는 싱글턴이 Enum 외의 클래스를 상속해야 한다면 사용 불가(열거 타입이 다른 인터페이스를 구현하도록 선언할 수는 있다).
