# iOSInterviewquestions
iOS개발자들에게 필요한 자료들을 정리하고 있는 중입니다.

면접때 받은 질문이나 공부한내용들

수정해야할 내용이나 추가해야할 내용은 언제든지 PR날려주세요!

```
답이 적혀있지 않은 이유는 해당 내용을 암기식으로 외우기 보다 찾아보고 공부하면서 습득 하시는게 좋기때문입니다.
해당내용을 찾아보면서 관련된 내용들 까지 같이 공부하시면서 해당 내용을 본인의 것으로 얻으시기 바랍니다.
```

모두의 힘을 모아봅시다 👯‍♀️👯‍♂️
감사합니다:)

# Required
아래 내용들은 최대한 많이 공부해놓는것이 좋습니다 📝

+ 면접시기가 wwdc이후 (7월~11월)이라면 해당년도 wwdc세션들을 봐 두시면 매우매우매우 좋습니다.

[Apple All Videos](https://developer.apple.com/videos/all-videos/)

## iOS
- Bounds 와 Frame 의 차이점을 설명하시오.
```
   - Frame: SuperView(상위뷰)의 좌표시스템안에서 View의 위치와 크기를 나타냅니다.
   - Bounds: View의 위치와 크기를 자신만의 좌표시스템안에서 나타냅니다.
   - 뷰의 Frame 값을 변경시키면, 해당 뷰의 위치가 변하지만,
   - 뷰의 Bounds 값을 변경시키면 해당 뷰를 중심으로 보이는 시각이 바뀐다. (scrollView)
```

- 실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오.
- 앱의 콘텐츠나 데이터 자체를 저장/보관하는 특별한 객체를 무엇이라고 하는가?
   - Core Data
   ```
   디바이스에서 데이터를 유지 or 캐시하고 실행 취소를 지원하는 프레임워크
   영구 데이터 저장 즉 데이터 베이스 기능은 Core Data 기능의 일부분으로 데이터 베이스 기능을 포괄하는 프레임워크이다
   ```
- 앱 화면의 콘텐츠를 표시하는 로직과 관리를 담당하는 객체를 무엇이라고 하는가?
   - ViewController
   ```
   앱 구조의 뼈대, 모든 앱에 반드시 하나 이상의 view controller로 이루어져 있음,
   모든 view controller 들의 상위 클래스
   ```
- App thinning에 대해서 설명하시오.

   ```
   애플리케이션이 디바이스에 설치될 때, 앱 스토어와 운영체제가 디바이스의 특성에 맞게 설치되도록 하는 설치 최적화 기술을 의미합니다.
   ```
###
- 앱이 시작할 때 main.c 에 있는 UIApplicationMain 함수에 의해서 생성되는 객체는 무엇인가?
   - UIApplication 싱글턴 객체
   ```
   응용 프로그램 객체 및 응용 프로그램 이벤트 주기를 설정합니다. 
   ```
- @Main에 대해서 설명하시오.

   ```
   UIKit 기반 앱의 main entry point 
   ```
- 앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있나요?
   ```
   Foreground mode는 메모리 및 기타 시스템 리소스에 높은 우선순위를 가지며 시스템은 이러한 리소스를 사용할 수 있도록 필요에 따라 background 앱을 종료합니다.
   
   Background mode는 가능한 적은 메모리공간을 사용해야함(시스템 리소스 해제, 메모리에서 해제 후 데이터를 디스크에 작성)
   ```
- 상태 변화에 따라 다른 동작을 처리하기 위한 앱델리게이트 메서드들을 설명하시오.
```
//애플리케이션이 실행된 직후 사용자의 화면에 보여지기 직전에 호출 
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool	

//애플리케이션이 최초 실행될 때 호출되는 메소드 
func application(_ application: UIApplication, willFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey : Any]? = nil) -> Bool		

//애플리케이션이 InActive 상태로 전환되기 직전에 호출  task 일시정지, 타이머 비활성화, 일시정지(게임)
func applicationWillResignActive(_ application: UIApplication)	

//애플리케이션이 백그라운드 상태로 전환된 직후 호출

func applicationDidEnterBackground(_ application: UIApplication)	

//애플리케이션이 Active 상태가 되기 직전, 화면에 보여지기 직전에 호출 
func applicationWillEnterForeground(_ application: UIApplication)	

//애플리케이션이 Active 상태로 전환된 직후 호출
func applicationDidBecomeActive(_ application: UIApplication)

//애플리케이션이 종료되기 직전에 호출 
func applicationWillTerminate(_ application: UIApplication)	
```
- 앱이 In-Active 상태가 되는 시나리오를 설명하시오.
```
App switcher 로 전환될때
다른 앱의 알림으로 이벤트를 수신하지 못할떄
```
- scene delegate에 대해 설명하시오.
```
iOS 13부터 AppDelegate의 책임이 AppDelegate와 SceneDelegate로 분리되었다.
App Delegate → 애플리케이션 생명주기 및 설정 담당
   App Life Cycle
   Session Life Cycle
Scene Delegate → 화면에 표시되는 내용(Windows 또는 Scenes)을 처리하고 앱이 표시되는 방식을 관리
   window → scene
```

- UIApplication 객체의 컨트롤러 역할은 어디에 구현해야 하는가?
```
UIApplication 객체는 UIApplicationMain(_:_:_:_:) 함수에서 Singleton 객체로 생성된다. 그리고 이 함수는 @main이 선언되어 있는 App Delegate 에서 실행된다.
```
- App의 Not running, Inactive, Active, Background, Suspended에 대해 설명하시오.
```
Not Running은 앱이 아직 실행되지 않았거나, 완전히 종료되어 동작하지 않는 상태.

Inactive는 app이 실행중이지만 사용자로부터 event를 받을 수 없는 상태. multitasking window로 진입하거나 app 실행중 전화, 알림 등에 의해 app을 사용할 수 없게 되는 경우 이 상태로 진입.

Active는 app이 실제 실행중이고 사용자 event를 받아서 상호작용할 수 있는 상태.
(바로 Active가 되지 않고 Inactive 상태를 거쳐 Active상태가 된다.)

Background는 홈화면으로 나가거나 다른 app으로 전환되어 현재 app이 실질적인 동작을 하지 않는 상태.

Suspended는 app을 다시 실행했을 때 최근 작업을 빠르게 로드하기 위해 메모리에 관련 데이터만 저장되어있는 상태
app이 background 상태에 진입했을 때 다른 작업을 하지 않으면 Suspended 상태로 진입하게 됩니다
Suspended 상태의 app들은 iOS의 메모리가 부족해지면 가장 먼저 메모리에서 해제됨.
따라서 app을 종료시킨 적이 없더라도 app을 다시 실행하려고 하면 처음부터 다시 실행됩니다.
```
###
- NSOperationQueue 와 GCD Queue 의 차이점을 설명하시오.
```
멀티스레딩을 위한 API
쉽고 편한 멀티 스레딩 처리를 위해 애플은 두가지의 API를 제공하고 있다.

GCD(Grand Central Dispatch)라는 C기반의 저수준 API와 NSOperation이라는 Obj-C 기반으로 만들어진 고수준 API가 있다. NSOperation은 GCD보다 약간의 오버헤드가 더 발생되고 느리지만 GCD에서는 직접 처리해야 하는 작업들을 지원 하고 있기 때문에 (KVO관찰, 작업취소 등등) 그정도는 감수하고 사용할만하다.

GCD는 백그라운드에서 스레드를 관리하면서 동시적으로 작업을 실행시키는 저수준 API를 제공하는 라이브러리이다.

- Dispatch Queues: 디스패치 큐는 FIFO 순서로 작업을 실행시키는 역할을 담당
- Serial Dispatch Queue: 시리얼 디스패치 큐는 한번에 한 작업만 실행
- Concurrent Dispatch Queue: 컨커런트 디스패치 큐는 시작한 작업이 끝나는것을 기다리지 않고 가능한 많은 작업을 실행
- Main Dispatch Queue: 앱의 메인 스레드에서 작업을 실행할 수있는 전역에서 사용가능한 시리얼 큐


```
- GCD API 동작 방식과 필요성에 대해 설명하시오.
```
GCD는 백그라운드에서 스레드를 관리하면서 동시적으로 작업을 실행시키는 저수준 API를 제공하는 라이브러리이다. 용어에는 다음이 있다.
- Dispatch Queues, 디스패치 큐는 FIFO 순서로 작업을 실행시키는 역할을 담당한다.
- Serial Dispatch Queue, 시리얼 디스패치 큐는 한번에 한 작업만 실행시킨다.
- Concurrent Dispatch Queue, 컨커런트 디스패치 큐는 시작한 작업이 끝나는것을 기다리지 않고 가능한 많은 작업을 실행시킨다.
- Main Dispatch Queue, 앱의 메인 스레드에서 작업을 실행할 수있는 전역에서 사용가능한 시리얼 큐
- 앱을 실행하면 시스템이 자동으로 메인스레드 위에서 동작하는 Main 큐(Serial Queue)를 만들어서 작업을 수행하고, 그 외에 추가적으로 여러 개의 Global 큐(Cuncurrent Queue)를 만들어서 큐를 관리

필요성
- Thread 를 직접 생성하고 관리하는 것에 비해 관리 용이
- 이미지 다운로드와 같이 오래 걸리는 작업을 동기로 처리하게 되면 해당 작업이 끝날때까지 화면이 멈추게 됨. 따라서 비동기로 백그라운드에서 동시에 작업을 처리해주는 것이 필요함
```
- Global DispatchQueue 의 Qos 에는 어떤 종류가 있는지, 각각 어떤 의미인지 설명하시오.
```
## GCD

큐마다 서로 다른 특징을 가지고 있어 원하는 특징에 맞게 큐에 보내면 된다

1) Main 큐 - 메인쓰레드 Serial 

2) Global 큐 - Defalut Concurrent(여러개 스레드로 분산처리) 

```
![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2df7c4c1-6850-4552-8dfc-b663a8a495e6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2df7c4c1-6850-4552-8dfc-b663a8a495e6/Untitled.png)
```
3) Private 큐 - 커스텀 큐

Global 큐 Qos

DispatchQueue.global(qos: .userInteractive) - 즉시
에니메이션, UI 업데이트
메인큐도 userInteractive 이지만, userInteractive 큐라고 해서 항상 메인큐인것은 아니다. 

DispatchQueue.global(qos: .userinitiated) - 몇초
유저가 즉시 필요하지만, 비동기적으로 처리할 작업 (파일 다운로드, 열기)

DispatchQueue.global() - Default

DispatchQueue.global(qos: .utility) - 몇초 ~ 몇분 
Progress indicator와 함께 길게 실행되는 작업 ex Networking , IO, 계산 

DispatchQueue.global(qos: .background)
DB 가져오기 / 유지

DispatchQueue.global(qos: .unspecifed)
```
###
- iOS 앱을 만들고, User Interface를 구성하는 데 필수적인 프레임워크 이름은 무엇인가?
- Foundation Kit은 무엇이고 포함되어 있는 클래스들은 어떤 것이 있는지 설명하시오.
- Delegate란 무언인가 설명하고, retain 되는지 안되는지 그 이유를 함께 설명하시오.
- NotificationCenter 동작 방식과 활용 방안에 대해 설명하시오.
- UIKit 클래스들을 다룰 때 꼭 처리해야하는 애플리케이션 쓰레드 이름은 무엇인가?
- App Bundle의 구조와 역할에 대해 설명하시오.
- 모든 View Controller 객체의 상위 클래스는 무엇이고 그 역할은 무엇인가?
- 자신만의 Custom View를 만들려면 어떻게 해야하는지 설명하시오.
- View 객체에 대해 설명하시오.
- UIView 에서 Layer 객체는 무엇이고 어떤 역할을 담당하는지 설명하시오.
- UIWindow 객체의 역할은 무엇인가?
- UINavigationController 의 역할이 무엇인지 설명하시오.
- TableView를 동작 방식과 화면에 Cell을 출력하기 위해 최소한 구현해야 하는 DataSource 메서드를 설명하시오.
- 하나의 View Controller 코드에서 여러 TableView Controller 역할을 해야 할 경우 어떻게 구분해서 구현해야 하는지 설명하시오.
- setNeedsLayout와 setNeedsDisplay의 차이에 대해 설명하시오.
###
- NSCache와 딕셔너리로 캐시를 구성했을때의 차이를 설명하시오.
- URLSession에 대해서 설명하시오.
- prepareForReuse에 대해서 설명하시오.
- 다크모드를 지원하는 방법에 대해 설명하시오.
- ViewController의 생명주기를 설명하시오.
- TableView와 CollectionView의 차이점을 설명하시오.

## Autolayout
- 오토레이아웃을 코드로 작성하는 방법은 무엇인가? (3가지)
- hugging, resistance에 대해서 설명하시오.
- Intrinsic Size에 대해서 설명하시오.
- 스토리보드를 이용했을때의 장단점을 설명하시오.
- Safearea에 대해서 설명하시오.
- Left Constraint 와 Leading Constraint 의 차이점을 설명하시오.

## Swift
- struct와 class와 enum의 차이를 설명하시오.
- class의 성능을 향상 시킬수 있는 방법들을 나열해보시오.
- Convinience init에 대해 설명하시오.
- Anyobject에 대해 설명하시오.
- Optional 이란 무엇인지 설명하시오.
- Struct 가 무엇이고 어떻게 사용하는지 설명하시오.
- Subscripts에 대해 설명하시오.
- instance 메서드와 class 메서드의 차이점을 설명하시오.
- Delegate 패턴을 활용하는 경우를 예를 들어 설명하시오.
- Singleton 패턴을 활용하는 경우를 예를 들어 설명하시오.
- KVO 동작 방식에 대해 설명하시오.
- Delegates와 Notification 방식의 차이점에 대해 설명하시오.
- 멀티 쓰레드로 동작하는 앱을 작성하고 싶을 때 고려할 수 있는 방식들을 설명하시오.
- MVC 구조에 대해 블록 그림을 그리고, 각 역할과 흐름을 설명하시오.
- 프로토콜이란 무엇인지 설명하시오.
- Hashable이 무엇이고, Equatable을 왜 상속해야 하는지 설명하시오.
- mutating 키워드에 대해 설명하시오.
- 탈출 클로저에 대하여 설명하시오.
- Extension에 대해 설명하시오.
- 접근 제어자의 종류엔 어떤게 있는지 설명하시오
- defer란 무엇인지 설명하시오.
- defer가 호출되는 순서는 어떻게 되고, defer가 호출되지 않는 경우를 설명하시오.
- property wrapper에 대해서 설명하시오.
- Generic에 대해 설명하시오.
- Result타입에 대해 설명하시오.
- Codable에 대하여 설명하시오.

## ARC
- ARC란 무엇인지 설명하시오.
- Retain Count 방식에 대해 설명하시오.
- Strong 과 Weak 참조 방식에 대해 설명하시오.
- 순환 참조에 대하여 설명하시오.
- 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오.

## Functional Programming
- 함수형 프로그래밍이 무엇인지 설명하시오.
- 고차 함수가 무엇인지 설명하시오.
- Swift Standard Library의 map, filter, reduce, compactMap, flatMap에 대하여 설명하시오.

## Architecture
- MVVM, Ribs, VIP 등 자신이 알고있는 아키텍쳐를 설명하시오.
- 의존성 주입에 대하여 설명하시오.

# Optional
아래부터는 추가로 공부를 하면 좋을 내용들입니다.

Objective-c나 rx는 회사, 팀마다 사용하는곳이 차이가있고 신입이나 주니어기준으로 필수라고 여겨지지않기에 옵셔널에 추가하였습니다.

## SwiftUI

## Combine
- PassthroughSubject에 대해서 설명하시오
- @Published에 대해서 설명하시오
- Anycancleable에 대해서 설명하시오
- sink에 대해서 설명하시오

## Rx
- Reactive Programming이 무엇인지 설명하시오.
- RxSwift에서 Hot Observable과 Cold Observable의 차이를 설명하시오.
- Subject와 drive의 차이를 설명하시오.

## MRC
- ARC 대신 Manual Reference Count 방식으로 구현할 때 꼭 사용해야 하는 메서드들을 쓰고 역할을 설명하시오.
- retain 과 assign 의 차이점을 설명하시오.
- 특정 객체를 autorelease 하기 위해 필요한 사항과 과정을 설명하시오.
- Autorelease Pool을 사용해야 하는 상황을 두 가지 이상 예로 들어 설명하시오. 
- 다음 코드를 실행하면 어떤 일이 발생할까 추측해서 설명하시오.
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];

## Advanced
- method swizzling이 무엇이고, 어떨 때 사용하는지 설명하시오.
- NSCoder 클래스는 어떤 상황에서 어떻게 써야 하는지 설명하시오.
- Responder Chain 구조에 대해 설명하고, First Responder 역할에 대해 설명하시오.
- NSObject부터 UIButton 까지 상속 과정의 계층과 역할을 설명하시오.
- shallow copy와 deep copy의 차이점을 설명하시오.
- Push Notification 방식에 대해 설명하시오.
- Foundation 과 Core Foundation 프레임워크의 차이점을 설명하시오.
- NSURLConnection 에서 사용하는 Delegate 메서드들에 대해 설명하시오.
- Synchronous 방식과 Asynchronous 방식으로 URL Connection을 처리할 경우의 장단점을 비교하시오.
- Plist 파일 구조와 Plist 파일에 저장된 데이터를 다루기 적합한 클래스를 설명하시오.
- Core Data와 Sqlite 같은 데이터 베이스의 차이점을 설명하시오.
- JSON 데이터를 처리하는 방식과 파서, 객체 변환 방식에 대해 설명하시오.
- 웹 서버와 HTTP 연결을 사용해서 데이터를 주거나 받으려면 사용해야 하는 클래스와 동작을 설명하시오.
- Protocol에서는 왜 var만 되는지 설명하시요.

## Objective-C
- Swift의 클로저와 Objective-C의 블록은 어떤 차이가 있는가?
- Mutable 객체과 Immutable 객체는 어떤것이 있는지 예를 들고, 차이점을 설명하시오.
- dynamic과 property 의미와 차이를 설명하시오.
- @property로 선언한 NSString* title 의 getter/setter 메서드를 구현해보시오.
- @property에서 atomic과 nonatomic 차이점을 설명하고, 어떤것이 안전한지, 어느것이 기본인지 설명하시오.
- @property로 선언한다는 것의 의미를 설명하고, .h에 넣을 경우와 .m에 넣을 경우 차이점을 설명하시오.
- -performSelector:withObject:afterDelay: 메시지를 보내면 인자값의 객체는 retain되는가? 그 이유를 함께 설명하시오.
- Objective-C 에서 캡슐화된 데이터를 접근하기 위한 방법들을 설명하시오.
- Fast Enumeration 이란 무엇인지 설명하시오. 
- unnamed category 방식에 대해 설명하시오.
- Category 확장과 Subclass 확장의 차이점을 설명하시오.
- Category 방식에 대해 설명하시오.
- Objective-C 에서 Protocol 이란 무엇인지 설명하시오.
- Objective-C++ 방식이 무엇인지 설명하고, 어떤 경우 사용해야 하는지 설명하시오.
