불필요한 객체 생성을 피하라
======
- 똑같은 기능의 객체를 매번 생성하기 보다는 개체 하나를 재사용하는 편이 낫다.
- 생성자 대신 정적 팩토리 메서드를 제공하는 불변클래스에서는 정적 팩토리 메서드를 사용해 객체 생성을 피할 수 있다.</br>
  ex_ Boolean < Boolean.valueOf(String)
- 비싼 객체를 반복해서 사용해야 하는 경우 캐싱하여 재사용하기를 권장한다</br>
> ex_ Pattern 샘플 코드
> ```java
> publc Class RomanNumerals{
>   private static final Pattern ROMAN = Pattern.compile(
>   "...")
> static boolean isromanNumeral(String s){
>       return ROMAN.matcher(s).matches();
>   }
> }
> ```
- 박싱된 기본 타입보다는 기본 타입을 사용하고 의도치 않은 오토박싱이 숨어들지 않도록 주의하자.
- 

