# babel4newbie

웹 엔지니어를 위한 babel 가이드

## 들어가기 전에

바벨이 무엇인지를 살펴보기 전에 바벨을 사용하는 이유를 알아야 합니다. 바벨은 (트랜스컴파일러)transcompiler 혹은 트랜스파일러(transpiler)라고 부를 수 있습니다.
이 트랜스파일러의 역할은 고급 언어를 저급 언어로 변환하는 기존의 컴파일로와는 다르게 동일한 추상화 레벨의 언어로 치환합니다. 따라서 트랜스파일러는 하나의 프로그래밍 언어로 작성된 소스 코드를 입력으로 받아 다른 프로그래밍 언어로 동일한 기능의 소스 코드를 출력합니다.

## Babel

바벨은 다음과 같이 설명할 수 있습니다.

```text
Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers or environments.
```

더불어 바벨을 사용해 다음과 같은 작업을 할 수 있습니다.

- Transform syntax
- Polyfill features that are missing in your target environment (through @babel/polyfill)
- Source code transformations (codemods)
- And more! (check out these videos for inspiration)

> Polyfill은 웹 개발에서 기능을 지원하지 않는 웹 브라우저 상의 기능을 구현하는 코드를 말합니다.

```javascript
// Babel Input: ES2015 arrow function
[1, 2, 3].map(n => n + 1);

// Babel Output: ES5 equivalent
[1, 2, 3].map(function(n) {
  return n + 1;
});
```

더 자세한 설명은 [바벨의 공식 문서](https://babeljs.io/docs/en/)를 참고합시다.
