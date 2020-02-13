# Design Pattern

디자인 패턴은 소프트웨어 속에서 공통적으로 발생하는 문제에 대해 재사용 가능한 해결책입니다. 이때 문제는 하나의 상황을 말하며, '음식을 주문하는 상황', '교통사고가 난 상황' 등의 일상 속의 상황과 유사한 의미를 가지고 있습니다.

공학적으로 풀어서 해석하면 '유저의 정보를 받아 암호화하고 이를 데이터베이스에 관리해야 한다'라는 문제를 디자인 패턴을 활용해 유저의 정보가 아닌 차량 정보를 암호화하는 등의 유사한 상황에서 활용할 수 있습니다.

다음과 같은 형태의 패턴이 대표적입니다.

## 종류

- 생성 패턴
  - 추상 팩토리
  - 빌더
  - 의존성 주입
  - 팩토리 메서드
  - 지연된 초기화
  - 멀티턴
  - 객체 풀
  - 프로토타입
  - 자원의 획득은 초기화이다(Resource Acquisition Is Initialization, RAII)
  - 싱글턴
- 구조 패턴
  - 어댑터, 래퍼(Wrapper), 변환기(Translator)
  - 브리지
  - 컴포지트
  - 데코레이터
  - 확장 객체(Extension object)
  - 퍼사드
  - 플라이웨이트
  - 프론트 컨트롤러
  - 마커
  - 모듈
  - 프록시
  - 트윈 [9]
- 행동 패턴
  - 블랙보드
  - 책임 연쇄
  - 커맨드
  - 인터프리터
  - 반복자
  - 중재자
  - 메멘토
  - 널 객체
  - 옵서버 또는 발행-구독 모델
  - 서번트
  - 사양(Specification pattern)
  - 상태
  - 전략
  - 템플릿 메소드
- 동시 실행 패턴

  - 비지터
  - 액티브 오브젝트
  - Balking
  - 바인딩 속성
  - 컴퓨트 커널
  - 더블 체크 라킹(Double checked locking)
  - 이벤트 기반 비동기
  - 가디드 서스펜션(Guarded suspension)
  - 조인
  - 락
  - 메시징 디자인 패턴 (MDP)
  - 모니터 객체
  - 반응자
  - 읽기-쓰기 락
  - 스케줄러
  - 스레드 풀
  - 스레드 특화 스토리지

- MVC
- MVP
- MVVM
- Flux

### MVC

Model View Controller의 약자로, 다음과 같은 구조로 정의됩니다.

![mvc](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2F7IE8f%2FbtqBRvw9sFF%2FAGLRdsOLuvNZ9okmGOlkx1%2Fimg.png)

- Model: 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하기 위한 부분 혹은 코드
- View: 사용자에게 보여지는 UI를 위한 부분 혹은 코드
- Controller: 사용자의 행동(Action)을 받아 처리하기 위한 부분 혹은 코드

#### MVC의 동작 순서

1. 사용자는 어플리케이션이 지정한 특정한 행동(Action)을 수행하고, 컨트롤러에 이벤트를 발생시킵니다.
2. 컨트롤러는 사용자의 특정한 행동을 확인하고, 행동에 맞는 코드를 실행해 모델을 업데이트합니다.
3. 행동에 맞는 코드 속에는 모델을 나타낼 뷰를 선택하는 코드가 포함되어 있습니다.
4. 뷰의 코드는 모델을 통해 얻은 데이터를 이용하여 화면을 나타냅니다.

MVC 패턴에서 뷰가 업데이트 되는 방법은 3가지가 대표적입니다.

1. 뷰가 모델을 이용하여 직접 업데이트 하는 방법
2. 모델에서 뷰에게 알람을 전달(Notify)하여 업데이트 하는 방법
3. 뷰가 폴링을 통해 주기적으로 모델의 변경을 감지하여 업데이트 하는 방법

#### MVC의 특징

- Controller는 여러개의 View를 선택할 수 있는 1:n 구조입니다.

Controller는 View를 선택할 뿐 직접 업데이트 하지 않습니다. (View는 Controller를 알지 못합니다.)

#### MVC의 장점

MVC 패턴의 장점은 널리 사용되고 있는 패턴이라는 점에 걸맞게 가장 단순합니다. 단순하다 보니 보편적으로 많이 사용되는 디자인패턴입니다.

#### MVC의 단점

MVC 패턴의 단점은 View와 Model 사이의 의존성이 높다는 것입니다. View와 Model의 높은 의존성은 어플리케이션이 커질 수록 복잡하지고 유지보수가 어렵게 만들 수 있습니다.

### MVP

Model View Presenter의 약자로, 다음과 같은 구조로 정의됩니다.

![mvp](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FclZlsT%2FbtqBTLzeUCL%2FIDA8Ga6Yarndgr88g9Nkhk%2Fimg.png)

- Model : 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분입니다.
- View : 사용자에서 보여지는 UI 부분입니다.
- Presenter : View에서 요청한 정보로 Model을 가공하여 View에 전달해 주는 부분입니다. View와 Model을 붙여주는 접착제..? 역할을 합니다.

#### MVP의 동작 순서

1. 사용자의 행동들은 뷰를 통해 들어오게 됩니다.
2. 뷰는 데이터를 프레젠터에 요청합니다.
3. 프레젠터는 모델에게 데이터를 요청합니다.
4. 모델은 프레젠터에서 요청받은 데이터를 응답합니다.
5. 프레젠터는 뷰에게 데이터를 응답합니다.
6. 뷰는 프레젠터가 응답한 데이터를 이용하여 화면을 나타냅니다.

#### MVP의 특징

Presenter는 View와 Model의 인스턴스를 가지고 있어 둘을 연결하는 접착제 역할을 합니다. Presenter와 View는 1:1 관계입니다.

#### MVP의 장점

MVP 패턴의 장점은 View와 Model의 의존성이 없다는 것입니다. MVP 패턴은 MVC 패턴의 단점이었던 View와 Model의 의존성을 해결하였습니다. (Presenter를 통해서만 데이터를 전달 받기 때문에..)

#### MVP의 단점

MVC 패턴의 단점인 View와 Model 사이의 의존성은 해결되었지만, View와 Presenter 사이의 의존성이 높은 가지게 되는 단점이 있습니다. 어플리케이션이 복잡해 질 수록 View와 Presenter 사이의 의존성이 강해지는 단점이 있습니다.

### MVVM

MVVM 패턴은 Model + View + View Model를 합친 용어입니다. Model과 View은 다른 패턴과 동일합니다. MVVM 패턴의 구조, 동작, 특징, 장점, 단점을 이야기하겠습니다.

![mvvm](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FCiXz0%2FbtqBQ1iMiVT%2FstaXr7UO95opKgXEU01EY0%2Fimg.png)

- Model : 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분입니다.
- View : 사용자에서 보여지는 UI 부분입니다.
- View Model : View를 표현하기 위해 만든 View를 위한 Model입니다. View를 나타내 주기 위한 Model이자 View를 나타내기 위한 데이터 처리를 하는 부분입니다.

#### MVVM 패턴의 동작 순서

1. 사용자의 Action들은 View를 통해 들어오게 됩니다.
2. View에 Action이 들어오면, Command 패턴으로 View Model에 Action을 전달합니다.
3. View Model은 Model에게 데이터를 요청합니다.
4. Model은 View Model에게 요청받은 데이터를 응답합니다.
5. View Model은 응답 받은 데이터를 가공하여 저장합니다.
6. View는 View Model과 Data Binding하여 화면을 나타냅니다.

#### MVVM의 특징

MVVM 패턴은 Command 패턴과 Data Binding 두 가지 패턴을 사용하여 구현되었습니다.

Command 패턴과 Data Binding을 이용하여 View와 View Model 사이의 의존성을 없앴습니다.

View Model과 View는 1:n 관계입니다.

#### MVVM의 장점

MVVM 패턴은 View와 Model 사이의 의존성이 없습니다. 또한 Command 패턴과 Data Binding을 사용하여 View와 View Model 사이의 의존성 또한 없앤 디자인패턴입니다. 각각의 부분은 독립적이기 때문에 모듈화 하여 개발할 수 있습니다.

#### MVVM의 단점

MVVM 패턴의 단점은 View Model의 설계가 쉽지 않다는 점입니다.

### Flux

MVC 패턴의 문제점을 해결하기 위해 페이스북에서 고안한 소프트웨어 아키텍처입니다.

#### MVC의 문제점

페이스북에서 이야기 하는 MVC의 가장 큰 단점은 양방향 데이터 흐름이었습니다.

![mvc's problem](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FALrHe%2FbtqBTMSuHfN%2FZlW9i9ET34e90APgCRChk1%2Fimg.png)

MVC 패턴에서 Controller는 Model의 데이터를 조회하거나 업데이트하는 역할을 합니다. Model이 업데이트 되면, View는 화면에 반영합니다. View가 Model을 업데이트 할 수도 있습니다. Model이 업데이트 되어 View가 따라서 업데이트 되고, 업데이트 된 View가 다시 다른 Model을 업데이트 한다면, 또 다른 View가 업데이트 될 수 있습니다.

복잡하지 않은 어플리케이션에서는 양방향 데이터 흐름이 문제가 크지 않을 수 있습니다. 하지만 어플리케이션이 복잡해 진다면 이런 양방향 데이터 흐름은 새로운 기능이 추가 될 때에 시스템의 복잡도를 기하급수적으로 증가 시키고, 예측 불가능한 코드를 만들게 됩니다. 개발자가 만든 어플리케이션이 개발자도 예측 못할 버그들을 쏟아 내게 됩니다.

![facebook header](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FAeyYk%2FbtqBO7RutbO%2FjF8wxI6kwsXxKk2Qg6D5dk%2Fimg.png)

페이스북에서 이야기하는 MVC의 양방향 데이터 흐름이 만들어 낸 예측하기 어려운 버그 중 하나는 알림 버그입니다. 페이스북에 로그인 했을 때, 화면 위 메시지 아이콘에 알림이 떠 있지만, 그 메시지 아이콘을 클릭하면 아무런 메시지가 없는 버그를 보신 적이 있으실 겁니다.

이 버그를 수정하고 얼마동안은 괜찮았지만 어플리케이션을 업데이트 하다 보면, 곧 다시 알림 버그가 나타나고 다시 버그를 수정하는 일이 반복되었습니다. 페이스북에서 이 문제의 해결 방법을 단방향 데이터 흐름으로 어플리케이션을 예측 가능하도록 만드는 방법에서 찾았습니다.

#### Flux로 해결

페이스북은 알람 버그의 원인을 양방향 데이터 흐름으로 보고, 단방향 데이터 흐름인 Flux를 도입했습니다.

![flux](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FlmfPW%2FbtqBQnTPgIs%2FZ1jmHHdNcOTNiu93kQ9gMk%2Fimg.png)

Flux의 가장 큰 특징은 단방향 데이터 흐름입니다. 데이터 흐름은 항상 Dispatcher에서 Store로, Store에서 View로, View는 Action을 통해 다시 Dispatcher로 데이터가 흐르게 됩니다. 이런 단방향 데이터 흐름은 데이터 변화를 휠씬 예측하기 쉽게 만듭니다. Flux를 크게 Dispatcher, Store, View 세 부분으로 구성됩니다.

- Dispatcher

Dispatcher는 Flux의 모든 데이터 흐름을 관리하는 허브 역할을 하는 부분입니다. Action이 발생되면 Dispatcher로 전달되는데, Dispatcher는 전달된 Action을 보고, 등록된 콜백 함수를 실행하여 Store에 데이터를 전달합니다. Dispatcher는 전체 어플리케이션에서 한 개의 인스턴스만 사용됩니다.

- Store

어플리케이션의 모든 상태 변경은 Store에 의해 결정이 됩니다. Dispatcher로 부터 메시지를 수신 받기 위해서는 Dispatcher에 콜백 함수를 등록해야 합니다. Store가 변경되면 View에 변경되었다는 사실을 알려주게 됩니다. Store은 싱글톤으로 관리됩니다.

- View

Flux의 View는 화면에 나타내는 것 뿐만이나라, 자식 View로 데이터를 흘려 보내는 뷰 컨트롤러의 역할도 함께 합니다.

- Action

Dispatcher에서 콜백 함수가 실행 되면 Store가 업데이트 되게 되는데, 이 콜백 함수를 실행 할 떼 데이터가 담겨 있는 객체가 인수로 전달 되어야 합니다. 이 전달 되는 객체를 Action이라고 하는데, Action은 대채로 액션 생성자(Action creator)에서 만들어집니다.

#### Flux에 관한 고찰

많이 이용해 보았다 할 수는 없지만.. 하지만 간단하지 않은 서비스에서 사용했다 자신있게 이야기 할 수 있습니다. MVC 패턴을 사용하면서 MVC의 양방향 데이터 흐름으로 기하급수력으로 증가하는 복잡도 때문에 고생한 경험은 없습니다. 또 전통적인 MVC 패턴 구조를 본다면, MVC 패턴은 양방향 데이트 흐름이 발생 하지 않아야 하는 것으로 이해가 됩니다.

([디자인패턴] MVC, MVP, MVVM 비교 참고) 페이스북에서 MVC 패턴을 잘못 사용하고 있었던 것은 아닐까.... 라는 생각이 조심스럽게 듭니다. 이것은 저의 고찰일 뿐이지만.... 저의 이런 생각이 [이 글](https://www.infoq.com/news/2014/05/facebook-mvc-flux/)을 읽고 자신을 얻게 되었습니다.
