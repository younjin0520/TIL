## 1. Reachability
### 가비지 컬렉터는 객체를 참조 가능한 객체와 참조 불가능한 객체로 나눔
- Reference의 강약에 따라 참조 가능한 객체를 제외하고 모두 쓰레기로 생각
- Reference는 참조의 강약에 따라 (강)Strong, Soft, Weak, Phantom Reference(약)로 나눔

## 2. Strong Reference
### new를 이용해 생성된 객체를 의미
GC에서 무조건 제외되기 때문에 메모리 누수를 방지하기 위해서는 주의해야함
(이 참조를 지워주지 않으면 GC에 의해 수거되지 않기 때문에 메모리 누수 유발)

## 3. Soft Reference
### 이 참조는 메모리가 충분하다면 GC에 의해서 수거되지 않고 *메모리에 여유가 없다면* GC에 의해 수거
- 안드로이드의 경우 weak reference와 비슷하게 동작 (모바일 기기 특성상 메모리가 적음)
[예제]
```java
SoftReference<Type> object = new SoftReference<Type>(new Object());
```

## 4. Weak Reference
### WeakReference는 GC가 발생되기 전까지는 참조를 유지하고 *GC가 발생하면 무조건 회수*
- 짧은 시간에 자주 쓰일 수 있는 객체를 이용할 때 유용하게 사용가능
[예제]
```java
WeakReference<Type> object = new WeakReference<Type>(new Object());
```
