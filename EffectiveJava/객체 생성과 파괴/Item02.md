Item 2 선택적 매개변수가 많다면 빌더를 고려하라
===============================================

- 객체를 생성할때, 주로 사용되던 방법이 점층적 생성자 패턴
- 점층적 생성자 패턴도 쓸 수는 있지만 **매개변수가 많아지면 클라이언트 코드를 작성하거나 읽기가 어려워진다.**
- 이를 해결하기위해 JBeans setter를 사용할수도 있지만 
- 메서드를 여러 개 호출해야 하는 문제점
- 객체가 완전히 생성되기 전까진 Consistency를 확립할 수 없는 문제점이 존재 => 클래스를 불면으로 만들수 없다.

### Builder 패턴으로 해결하자
빌더 패턴 코드 예시
```java
class Example<T> {
     	private T foo;
     	private final String bar;

 	private Example(T foo, String bar) {
 		this.foo = foo;
 		this.bar = bar;
 	}

 	public static <T> ExampleBuilder<T> builder() {
 		return new ExampleBuilder<T>();
 	}

 	public static class ExampleBuilder<T> {
 		private T foo;
 		private String bar;

 		private ExampleBuilder() {}

 		public ExampleBuilder foo(T foo) {
 			this.foo = foo;
 			return this;
 		}

 		public ExampleBuilder bar(String bar) {
 			this.bar = bar;
 			 return this;
 		}


 		public Example build() {
  	return new Example(foo, bar);
 		}
 	}
}
```
- 객체를 직접 만드는 대신 필수 매개변수만으로 빌드 객체를 얻고, 빌더 객체가 제공하는 Setter 메서드를 통해 선택 매개변수를 설정(Method Chaining).
- 이후, build()를 호출하여 필요한 객체를 얻는 방식.

### Sample
- https://github.com/Xogo8565/Java-etc/tree/master/Java/Builder

- ps. Lombok 사용시 빌더를 더욱 간편하게 사용할 수 있다.
- https://projectlombok.org/features/Builder
