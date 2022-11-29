## ADB (안드로이드 디버그 브릿지)
- 기기와 통신할 수 있도록 지원하는 다목적 명령줄 도구
- Android SDK 플랫폼 도구 패키지에 포함 (설치 위치: android_sdk/platform-tools)
설치 페이지 (https://developer.android.com/studio/releases/platform-tools?hl=ko)

### 1. 기기 쿼리
> adb devices -l
- devices 명령어를 사용하여 연결된 기기 목록 생성

### 2. 앱 설치
> adb install path_to_apk
- adb를 사용하여 연결된 기기에 Install 명령어로 APK 설치

### 3. adb 서버 중지
> adb kill -server


## Dumpsys : 안드로이드 기기에서 실행되는 도구로, 디바이스의 정보와 상태 값을 알려줌
안드로이드 디버그 브릿지(ADB)를 사용해 명령줄에서 dumpsys를 호출하여 연결된 기기에서 실행되는 모든 시스템 서비스의 진단 출력을 가져올 수 있음

> adb shell dumpsys : 연결된 기기의 모든 시스템 서비스에 관한 정보를 제공
> adb shell dumpsys [얻고싶은 정보] : 연결된 기기의 특정 정보를 제공

### 1. 입력 진단 검사
> adb shell dumpsys input
- 키보드, 터치스크린과 같은 시스템 입력 장치의 상테와 입력 이벤트 처리를 덤프

### 2. UI 성능 테스트
> adb shell dumpsys gfxinfo package-name (framestats)
- gfxinfo 서비스를 지정하면 애니메이션 프레임과 관련된 성능 정보와 함께 출력이 제공됨
- framestats 옵션으로 더 자세한 프레임 타이밍 정보 제공 가능

### 3. 네트워크 진단 검사
> adb shell dumpsys netstats detail
- netstats를 통해 기기가 부팅되었을 때부터 수집된 네트워크 사용 통계가 제공

### 4. 배터리 진단 검사
> adb shell dumpsys batterystats options
- batterystats를 지정하면 UID로 구성된 기기의 배터리 사용량에 관한 통계 데이터가 생성됨

* 출력되는 정보
배터리 관련 이벤트 내역
기기의 전역 통계
UID 및 시스템 구성요소당 대략적인 전력 사용
각 앱의 패킷당 모바일 밀리초
집계된 시스템 UID 통계
집계된 앱 UID 통계

### 5. 메모리 할당 보기
- prostates (일정 기간동안 앱 메모리 사용량 검사) / meminfo (특정 시점의 사용량 검사)

(1) Prostates : 앱이 백그라운드에서 얼마나 오래 실행되는지, 그 기간동안 메모리 사용량 등 확인 가능
- 메모리 누수를 찾을 수 있음
> adb shell dump sys prostates --hours 3 //3시간 동안 메모리 사용량 통계를 가져옴

(2) Meminfo : 다양한 유형이 RAM 할당 사이에서 앱의 메모리가 나뉘는 방법을 기록
> adb shell dumpsys memento package_name|pid [-d]
[예시] adb shell dumpsys meminfo com.google.android.apps.maps -d

* 결과 항목 중 AppContexts 및 Activities
현재 프로세스에 있는 앱 Context 및 Activity 객체의 수
- 정적 참조로 인해 가비지 컬렉션될 수 없는 누수된 Activity 객체를 빠르게 식별하는 데 도움

* adb shell dumpsys activity : 현재 실행중인 액티비티의 이름을 얻을 수 있음
