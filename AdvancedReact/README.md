# Advanced React

리액트를 개발하는 훌륭한 방법들은 검색을 통해 쉽게 찾을 수 있습니다. 이 자료에서는 쉽게 찾을 수 있는 자료들에서는 담지 않는, 보다 깊은 React 개발을 위해 React의 메커니즘, 동작원리 등을 알아보도록 하겠습니다.

- Functional Component with Hooks
- Server Side Rendering with Next.js
- Route Masking with Next.js
- Lazy Import(Module, Component) with Next.js

## Functional Component with Hooks

React Hooks는 React v16.8에 추가된 차세대 컴포넌트 정의 방법입니다. 중요한 점은 React 팀에서 Class를 제거할 계획이 없기 때문에 Class 문법보다 '좋은 것'이라고 이해하는 것보다 컴포넌트를 정의할 수 있는 하나의 형태라고 이해하는 것이 바람직합니다. 다만, Class보다 '좋은 것'이 존재하고, 마찬가지로 '좋지 않은 점'도 존재하기에 이에 대한 차이를 명확하게 아는 것이 좋습니다.

우선, React에서 컴포넌트를 선언하는 방식은 'Class' 혹은 'Function'을 이용하는 2가지가 존재합니다. 각각에 대한 설명은 Hooks의 일부에 대한 설명이 되기도 합니다. 그 이유는 Hooks가 Function 기반 컴포넌트에서만 사용할 수 있기 때문입니다.

우선 컴포넌트는 다음과 같이 정의할 수 있습니다.

> 컴포넌트를 통해 UI를 재사용 가능한 개별적인 여러 조각으로 나누고, 각 조각을 개별적으로 살펴볼 수 있습니다.
>
> 개념적으로 컴포넌트는 JavaScript 함수와 유사합니다. “props”라고 하는 임의의 입력을 받은 후, 화면에 어떻게 표시되는지를 기술하는 React 엘리먼트를 반환합니다.

Class와 Function을 이용한 컴포넌트 정의 방법의 가장 큰 차이는 개발 방법에 대한 차이와 동일합니다. Class 기반 컴포넌트 정의 방법은 OOP를 기반으로 한 기존의 개발 방법을 그대로 이어받아 OOP적인 특성과 장점을 그대로 컴포넌트에 적용할 수 있어 개발에 용이합니다. 마찬가지로 Function 기반 컴포넌트 정의 방법은 FP적인 특성과 장점을 그대로 컴포넌트에 적용할 수 있습니다.

따라서 둘의 차이는 성능보다는 각각의 개발 방법론의 관점으로 바라봐야 한다는 것을 이해하고 다음의 비교를 살펴봅시다.

Functional은 다음과 같은 특징을 가집니다.

- Functional Programming style
- Can't have state
- Can have partial lifecycle with Hooking
- Can have refs with Hooking
- Minimal boilerplate(Clean and Simple)

Class-based는 다음과 같은 특징을 가집니다.

- Object Oriented Programming style
- Can have state
- Can have lifecycle methods with Inheritance
- Can have refs with DOM elements

둘을 가지고 Performance optimisation에 대한 이슈를 다루는 글은 상당히 많습니다. 둘은 분명 성능적인 차이가 존재합니다. 과거의 경우 Functional Component에서는 shouldComponentUpdate를 사용하거나 PureComponent를 정의하는 게 불가능했지만, 현재는 가능하고, 보다 다양한 방법으로 앱의 성능을 최적화할 수 있기 때문에 둘의 성능적 차이는 상대적으로 중요하지 않습니다. 성능적인 이슈에 관심을 가지기보다는 둘의 사용처를 분명하게 아는 것이 중요한 것입니다.

우리가 자주 만나게 될 Hooking과 Hook은 다음과 같은 특징을 가지고 있습니다.

> Hooking은 소프트웨어 구성 요소 간에 발생하는 함수 호출, 메시지, 이벤트 등을 중간에서 바꾸거나 가로채는 명령, 방법, 기술이나 행위입니다. 이때 이러한 간섭된 함수 호출, 이벤트 또는 메시지를 처리하는 코드를 Hook이라고 부릅니다.

React Hooks도 React를 사용하는 과정에서 발생하는 함수 호출, 메시지, 이벤트 등을 준간에서 바꾸거나 가로채는 역할을 합니다. React Hooks를 이용하면 React 앱이 동작하는 과정에서 State를 만들거나 삽입하거나 변경하는 게 가능하고, life cycle을 통해 정의해둔 Event를 활용할 수도 있습니다.

하나의 Components를 통해 Hooks가 어떻게 활용되는지 살펴봅시다.

```javascript
// Functional Component
import React, { useState, useEffect } from "react";

const App = () => {
  const [isLoading, setIsLoading] = useState(true);
  const [count, setCount] = useState(0);

  // like componentDidMount and ComponentDidUpdate
  useEffect(() => {
    // ... events
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
    setIsLoading(false);

    // like componentWillUnmount
    return () => {
      // ... events
      // for cleanup function
    };
  });

  if (isLoading) {
    return (
      <div>
        <p>Now Loading...</p>
      </div>
    );
  }

  return (
    <div>
      <p>Working Now!</p>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
};

export default App;
```

```javascript
// Class-based Component
import React, { Component } from "react";

class App extends Component {
  constructor(props) {
    super(props);
    this.state = { isLoading: true, count: 0 };
  }

  componentDidMount() {
    document.title = `You clicked ${count} times`;
    this.setState({ isLoading: false });
  }

  componentDidUpdate() {
    document.title = `You clicked ${this.state.count} times`;
  }

  componentWillUnmount() {
    // ... events
    // for cleanup function
  }

  render() {
    if (isLoading) {
      return (
        <div>
          <p>Now Loading...</p>
        </div>
      );
    }

    return (
      <div>
        <p>Working Now!</p>
        <p>You clicked {this.state.count} times</p>
        <button
          onClick={() => {
            this.setState({ count: this.state.count + 1 });
          }}
        >
          Click me
        </button>
      </div>
    );
  }
}

export default App;
```

React v16.12.0를 기준으로 기본적으로 제공되는 React Hooks가 모든 life cycle을 대체하지는 않습니다. [Hooks FAQ](https://ko.reactjs.org/docs/hooks-faq.html)를 살펴보면 아직 getSnapshotBeforeUpdate와 componentDidCatch은 대체하지 않는 것을 알 수 있습니다.
