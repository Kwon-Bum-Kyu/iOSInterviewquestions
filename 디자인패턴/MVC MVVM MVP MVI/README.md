1. [MVC](#MVC)
2. [MVP](#MVP)
3. [MVVM](#MVVM)
3. [MVI](#MVI)

# MVC

MVC 패턴은 Model + View + Controller를 합친 용어입니다.

1.  구조

    <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F7IE8f%2FbtqBRvw9sFF%2FAGLRdsOLuvNZ9okmGOlkx1%2Fimg.png" width=600 />

    Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분

    View: 사용자에게 보여지는 UI 부분
    Controller: 사용자의 입력을 받고 처리하는 부분입니다.

2.  동작

    MVC 패턴의 동작 순서는 다음과 같습니다.

        1. 사용자의 Action 들은 Controller에 들어오게 됩니다.

        2. Controller는 사용자의 Action을 확인하고, Model을 업데이트 합니다.

        3. Controller는 Model을 나타내줄 View를 선택합니다.

        4. View는 Model을 이용하여 화면을 나타냅니다.

3.  특징

    Controller는 여러개의 View를 선택할 수 있는 1:n 구조입니다.

    Controller는 View를 선택할 뿐 직접 업데이트 하지 않습니다. (View는 Controller를 알지 못함.)

4.  장점

    가장 단순합니다.

5.  단점

    View와 Model 사이의 의존성이 높습니다. View와 Model의 높은 의존성은 어플리케이션이 커질수록 복잡해지고 유지보수가 어렵게 만들 수 있습니다.

# MVP

    MVP 패턴은 Model + View + Presenter를 합친 용어입니다. Model과 View는 MVC 패턴과 동일하고, Controller 대신 Presenter가 존재합니다.

1. 구조

   <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FclZlsT%2FbtqBTLzeUCL%2FIDA8Ga6Yarndgr88g9Nkhk%2Fimg.png" width=600 />

   Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분

   View: 사용자에게 보여지는 UI 부분

   Presenter: View에서 요청한 정보로 Model을 가공하여 View에게 전달해주는 부분입니다. View와 Model을 붙여주는 브릿지 역할을 합니다.

2. 동작

   1. 사용자의 Action들은 View를 통해 들어오게 됩니다.

   2. View는 데이터를 Presenter에 요청합니다.

   3. Presenter는 Model에게 데이터를 요청합니다.

   4. Model은 Presenter에서 요청받은 데이터를 응답합니다.

   5. Presenter는 View에게 데이터를 응답합니다.

   6. View는 Presenter가 응답한 데이터를 이용하여 화면을 나타냅니다.

3. 특징

   Presenter는 View와 Model의 인스턴스를 가지고 있어 둘을 연결하는 브릿지 역할을 합니다.

   Presenter와 View는 1:1 관계입니다.

4. 장점

   MVP 패턴의 장점은 View와 Model의 의존성이 없다는 것입니다. MVP 패턴은 MVC 패턴의 단점이었던 View와 Model의 의존성을 해결하였습니다. (Presenter를 통해서만 데이터를 전달 받기 때문에..)

5. 단점

   MVC 패턴의 단점인 View와 Model 사이의 의존성은 해결되었지만, View와 Presenter 사이의 의존성이 높은 가지게 되는 단점이 있습니다.

# MVVM

1. 구조

   <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCiXz0%2FbtqBQ1iMiVT%2FstaXr7UO95opKgXEU01EY0%2Fimg.png" width=600>

   Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분

   View: 사용자에게 보여지는 UI 부분

   ViewModel: View를 표현하기 위해 만든 View를 위한 Model입니다.  
   View를 나타내 주기 위한 Model이자 View를 나타내기 위한 데이터 처리를 하는 부분입니다.

2. 동작

   1. 사용자의 Action들은 View를 통해 들어오게 됩니다.

   2. View 에 Action이 들어오면 **Command 패턴**으로 View Model에 Action을 전달합니다.

   3. View Model은 Model에게 데이터를 요청합니다.

   4. Model은 View Model에게 요청받은 데이터를 응답합니다.

   5. View Model은 응답 받은 데이터를 가공하여 저장합니다.

   6. View는 View Model과 **Data Binding**하여 화면을 나타냅니다.

3. 특징

   MVVM 패턴은 [Command 패턴](https://ko.wikipedia.org/wiki/%EC%BB%A4%EB%A7%A8%EB%93%9C_%ED%8C%A8%ED%84%B4) 과 [Data Binding](https://en.wikipedia.org/wiki/Data_binding) 두 가지 패턴을 사용하여 구현되어 View와 View Model 사이의 의존성을 없앴습니다.

   View Model과 View는 1:n 관계입니다.

4. 장점

   MVVM 패턴은 View와 Model 사이의 의존성이 없습니다. 또한 Command 패턴과 Data Binding을 사용하여 View와 View Model 사이의 의존성 또한 없앤 디자인패턴입니다. 각각의 부분은 독립적이기 때문에 모듈화 하여 개발할 수 있습니다.

5. 단점

   설계가 쉽지 않다

# MVI

   MVI 패턴은 자바스크립트 생태계에서 탄생했으며 MVC에서 파생된, 능동적인 Controller 대신 Intent라고 불리는 Reactive 요소를 이용한 아키텍처 패턴입니다.
   
1. 구조

   <img src="//t1.daumcdn.net/thumb/R1280x0/?fname=http://t1.daumcdn.net/brunch/service/user/1OLd/image/JHTtx7AD-xlDJHdutxQBnUdnXQo.png" width=600 />
   
   Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분

   View: 사용자에게 보여지는 UI 부분

   Intent: View에서 액션을 입력받고 모델의 상태를 변화시켜 그 변환된 상태의 모델을 뷰에 전달하는 부분

2. 동작

   1. Intent로 User의 정보를 가져온다 (Android의 인텐트와 다름)

   2. Intent는 Model에서 처리해야 하는 동작(Intended action)을 제공합니다.

   3. Model은 Intent로부터 동작을 가져옵니다. 
   (MVI의 Model은 단순 데이터뿐만 아니라, Application 상태(State)와 Business Logic을 관리합니다.)

   4. Model은 View에 표시할 새로운 모델을 생성합니다.
   (Immutability 한 모델을 생성합니다.)

   5. View는 Model로부터 새로운 모델을 가져와 표시합니다.

   6. View는 Presenter가 응답한 데이터를 이용하여 화면을 나타냅니다.

3. 특징

   MVI 는 Model - View - Intent 로 구성되어 있는 단방향(Uni-Directional) 아키텍쳐이다.

   MVVM 의 경우 VM 이 Model 과 View 의 사이에서 양방향으로 통신하기 때문에 자칫 잘못하다간 VM 이 비대해지는 부작용이 발생할 수가 있지만 단방향 아키텍쳐는 그러한 이슈가 발생하지 않는다.

4. 장점

   단방향, 불변성 데이터를 이용해 예측 가능한 상태이다.

   서로간 의존성이 없다.

5. 단점

   RxSwift와 같은 Observable 한 외부 라이브러리를 이용해야 함
   

   

