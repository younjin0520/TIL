## Memory Leak이란?
GC가 사용되지 않는 객체의 메모리를 수거할 수 없는 것
[예시]
안드로이드의 경우 Activity 인스턴스는 onDestroy() 호출 이후 더 이상 필요없게 되지만 어딘가에서 해당 Activity의 인스턴스를 강하게 참조하고 있다면 GC에서 수거되지 않아 Memory Leak 발생

## 문제점
APP 버벅거림, APP 중지

## Memory Leak 디버깅 방법
1. 안드로이드 스튜디오 메모리 프로파일러 사용
2. 
앱 실행 > 메모리 프로파일러 > (+) Dump Java heap 클릭

객체를 보려면 package로 정렬한 다음 > 현재 Activity로 이동(Memory Leak이 예상되는 행동 수행) > 메모리 사용 중인 것을 확인할 수 있음

Activity 닫기 > GC 다시 실행 후 > 다시 Dump Java heap를 클릭하여 메모리가 수거되었는지 확인

* 참고 자료
https://www.youtube.com/watch?v=4Wnu_2meZaI
https://www.youtube.com/watch?v=LGVbpobV-Yg
https://www.youtube.com/watch?v=v4kCRZ_O4Lc


2. LeakCanary 사용 (https://square.github.io/leakcanary/)


## Todo:: Memory Leak이 발생할 수 있는 원인
