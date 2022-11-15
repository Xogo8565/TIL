인스턴스화를 막으려거든 private 생성자를 사용하라
==========================
- 정적 메서드와 정적 필드만을 담은 클래스를 만들게 될 경우, **private 생성자를 이용해 인스턴스화를 방지**하자.

```java
public class UtilityClass {
  private UtilityClass(){
    throw new AssertionError();
  }
  ...
}
```
- 다만 직관적이지는 않으므로, //기본 생성자가 막아지는 것을 막는다(인스턴스화 방지용) 과 같은 적절한 주석을 달아주도록 하자.
