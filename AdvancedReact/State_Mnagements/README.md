# State Managements

[State Pattern](https://dev-momo.tistory.com/entry/State-Pattern-%EC%8A%A4%ED%85%8C%EC%9D%B4%ED%8A%B8-%ED%8C%A8%ED%84%B4)이란, 일련의 규칙에 따라 객체의 상태(State)를 변화시켜, 객체가 할 수 있는 행위를 바꾸는 패턴입니다.

상태에 따라 행동이 변화하는 객체엔 모두 적용할 수 있습니다. State 패턴의 핵심은 상태를 인터페이스로 분리시키는 것입니다. 따라서 상태들을 유연하게 관리할 수 있기 때문에 유지 보수에 효율적입니다.

```js
interface State {
  clock: Clock;
  toNormal?: (clock: Clock) => void;
  toSpecial?: (clock: Clock) => void;
}

class Clock {
  private state: State;

  constructor(defaultState) {
    this.state = defaultState;
  }

  public setState(state: State) {
    this.state = state;
  }

  public toNormal() {
    this.state.toNormal(this);
  }

  public toSpecial() {
    this.state.toSpecial(this);
  }
}

class NormalState implements State {
  public clock: Clock;

  constructor() {
    console.log("Normal State");
  }

  public toSpecial(clock: Clock) {
    clock.setState(new SpecialState());
  }
}

class SpecialState implements State {
  public clock: Clock;

  constructor() {
    console.log("Special State");
  }

  public toNormal(clock: Clock) {
    clock.setState(new NormalState());
  }
}

const clock = new Clock(new NormalState());
clock.toSpecial();
clock.toNormal();
```

## React에서의 상태 관리

보편적으로 React에서의 상태 관리는 앞선 State 패턴에 기반하여 [Flux 패턴](https://facebook.github.io/flux/)을 통해 하게 됩니다. 하지만, React에서 기본적으로 제공하는 상태 관리는 UI의 상태(State)가 빈번하게 변경되는 어플리케이션에서 사용하기엔 너무 복잡했습니다. 이를 해결하기 위해 [Redux](https://redux.js.org/)를 사용할 수 있습니다.

리덕스는 [motivation](https://redux.js.org/introduction/motivation)에 적혀있는 것처럼 복잡해지는 UI를 상태를 통해 관리하기 위해 만들어졌습니다.

원활한 진행을 위해 우리는 [리덕스 공식 한글 문서](https://lunit.gitbook.io/redux-in-korean/)를 통해 리덕스에 대해 알아봅시다.

### [Action](https://redux.js.org/basics/actions)

### [Reducer](https://redux.js.org/basics/reducers)

### [Store](https://redux.js.org/basics/store)
