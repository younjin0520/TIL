# Java Grammar
## 1. Optional
#### Optional<T>는 null이 올 수 있는 값을 감싸는 Wrapper 클래스 (NullPointerException을 방지)
- Optional.ofNullable() : 값이 NULL일 수도 있는 경우 Optional 객체 생성
  ```java
  public Optional<Member> findById(Long id) {
    return Optional.ofNullable(store.get(id));
  }
  ```
  이 경우 orElse 메소드를 이용해서 안전하게 값을 가져올 수 있음
  ```java
  Optional<String> optional = Optional.ofNullable(getName());
  String name = optional.orElse("blank"); // 값이 없다면 "blank" 를 리턴
  ```
- Oprional.of() : 값이 NULL이 아닌 경우 Optional 객체 생성 (NULL을 저장하려고 하면 NPE 발생)
  
```java
  Optional<String> optional = Optional.of("Java");
```
  
- get(), isPresent() : 객체에 저장된 값에 접근
  
  - get()으로 접근했을 때 Optional 객체에 저장된 값이 null이면 *NoSuchElementException* 발생
  - get()으로 접근하기 전에 isPresent() 메소드를 사용하여 Null인지 확인하고 호출해야함
  
```java
  private void validateDuplicateMember(Member member) {
    memberRepository.findByName(member.getName())
            .ifPresent(m -> {
                throw new IllegalStateException("이미 존재하는 회원입니다.");
            });
 }
```
  
## 2. Map과 HashMap

## 3. Map 함수
- map.remove(key) : 특정 key 값을 가지고 있는 item 삭제
- map.clear() : map 전체 내용 삭제
- map.ketSet() : map에 있는 모든 key 값들을 반환 (Collection 객체) 
- map.values() : map에 있는 모든 value 값들을 반환 (Collection 객체)

```java
@Override
public List<Member> findAll() {
    return new ArrayList<>(store.values());
}
```
  
## 4. stream()
  
## 5. findAny()
  
## 6. throws
- IllegalStateException
  
## 7. final
  변수, 메서드, 클래스에 사용 가능
  
  #### 7.1 변수에 사용되었을 때
  
  수정할 수 없는 변수라는 의미 (Kotlin의 val과 같음)
  - 기본형 변수: 값 변경 불가
  - 참조형 변수: 가리키는 객체 변경 불가 (객체 내부 값은 변경 가능)
  
  #### 7.2 메서드에 사용되었을 때
  
  override를 제한
  
  #### 7.3 클래스에 사용되었을 때
  
  클래스 상속을 제한
  
## 8. static
  
