1. [MVC](#MVC)

# MVC

MVC 패턴은 Model + View + Controller를 합친 용어입니다.

1. 구조

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F7IE8f%2FbtqBRvw9sFF%2FAGLRdsOLuvNZ9okmGOlkx1%2Fimg.png" width=600 />

Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분

View: 사용자에게 보여지는 UI 부분

Controller: 사용자의 입력을 받고 처리하는 부분입니다.

2. 동작

MVC 패턴의 동작 순서는 다음과 같습니다.

    1. 사용자의 Action 들은 Controller에 들어오게 됩니다.

    2. Controller는 사용자의 Action을 확인하고, Model을 업데이트 합니다.

    3. Controller는 Model을 나타내줄 View를 선택합니다.

    4. View는 Model을 이용하여 화면을 나타냅니다.

3. 특징

Controller는 여러개의 View를 선택할 수 있는 1:n 구조입니다.

Controller는 View를 선택할 뿐 직접 업데이트 하지 않습니다. (View는 Controller를 알지 못함.)

4. 장점

가장 단순합니다.

5. 단점

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
