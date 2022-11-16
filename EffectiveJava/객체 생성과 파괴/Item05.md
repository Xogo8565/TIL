자원을 직접 명시하지 말고 의존 객체 주입을 활용하라
====

- 많은 클래스가 하나 이상의 자원에 의존한다
- 사용하는 자원에 따라 동작이 달라지는 클래스의 경우 정적 유틸리티 방식이나 싱글턴 방식이 적합하지 않다.
- 인스턴스를 생성할 때 생성자에 필요한 자원을 주입해주는 방식 고려

```java

public class SpellChekcer{
  private final Lexicon dictionary;
  
  public SpellChecker (Lexicon dictionary) {
    this.dictionary = Objects.requireNonNull(dictionary);
  }
  
  ...
}
```

- 규모가 큰 프로젝트의 경우 코드를 어지럽게 만들기도
- Dagger, Guice, Spring 등의 의존 객체 주입 프레임 워크를 통해 해소

