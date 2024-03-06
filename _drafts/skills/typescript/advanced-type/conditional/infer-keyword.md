---
layout: skill
title: TypeScript Conditional Type - 'infer' Keyword (infer)
date: 2024-03-03
---




## `infer` Keyword


`infer` 키워드는 TypeScript의 강력한 기능 중 하나로, 조건부 타입(Conditional Types) 내에서 타입을 동적으로 추론할 수 있는 방법을 제공합니다. 이 글에서는 `infer` 키워드의 작동 방식, 사용 사례, 그리고 이를 사용함으로써 얻을 수 있는 이점에 대해 자세히 설명하겠습니다.

### `infer` 키워드란?

`infer` 키워드는 TypeScript 2.8에서 도입되었으며, 조건부 타입을 정의할 때 내부적으로 타입을 추론할 수 있도록 해줍니다. 주로 제네릭 타입의 일부를 추론하고자 할 때 사용되며, 이를 통해 복잡한 타입 연산과 조건부 로직을 간결하게 표현할 수 있습니다.

### 작동 방식

`infer` 키워드는 `extends` 키워드와 함께 사용되며, 조건부 타입의 조건식 내에서만 사용됩니다. `T extends U ? X : Y` 형태의 조건부 타입에서 `U` 부분에 `infer`를 사용하여 `T`에서 추론하고자 하는 타입을 지정할 수 있습니다.

### 사용 예

**함수 반환 타입 추론하기**

```typescript
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;
```

위 예제에서 `ReturnType` 타입은 함수 타입 `T`의 반환 타입을 추론합니다. 만약 `T`가 함수 타입이 아니라면, `never` 타입을 반환합니다.

**프로미스에서 해결되는 타입 추론하기**

```typescript
type UnwrapPromise<T> = T extends Promise<infer U> ? U : T;
```

이 예제에서 `UnwrapPromise` 타입은 `T`가 `Promise`로 감싸진 타입일 경우, 그 `Promise`가 해결(resolve)되는 값의 타입을 추론합니다.

**배열 요소의 타입 추론하기**

```typescript
type ElementType<T> = T extends (infer U)[] ? U : never;
```

`ElementType` 타입은 배열 `T`의 요소 타입을 추론합니다. `T`가 배열이 아닌 경우, `never`를 반환합니다.

### 이점

- **복잡한 타입의 간결한 표현:** `infer` 키워드를 사용하면 복잡한 타입 연산을 간결하게 표현할 수 있으며, 코드의 가독성을 높일 수 있습니다.
- **재사용 가능한 타입 유틸리티:** `infer`를 사용하여 정의한 타입 유틸리티는 다양한 상황에서 재사용할 수 있어, 코드 중복을 줄이고 효율성을 높일 수 있습니다.
- **타입 안정성 향상:** 동적 타입 추론을 통해 타입스크립트의 타입 시스템을 보다 정확하고 안전하게 사용할 수 있습니다.

### 결론

`infer` 키워드는 TypeScript에서 제공하는 강력한 타입 추론 기능으로, 조건부 타입의 사용을 통해 개발자가 복잡한 타입 조작을 쉽고 간결하게 수행할 수 있도록 돕습니다. 이를 통해 코드의 가독성과 재사용성을 높이며, 타입 안정성을 강화할 수 있습니다. `infer` 키워드의 도입은 TypeScript의 타입 시스템을 보다 유연하고 강력하게 만들어주는 중요한 발전입니다.








`infer` 키워드의 사용과 이해를 심화시키기 위해, 타입스크립트에서 `infer`를 활용한 고급 패턴과 이를 사용할 때의 주의점, 그리고 실제 개발 환경에서의 응용 사례를 추가로 탐색할 수 있습니다.

### 고급 패턴

- **복합 타입에서의 추론**

  `infer` 키워드는 함수의 반환 값뿐만 아니라, 튜플, 객체 리터럴과 같은 복합 타입에서도 특정 부분의 타입을 추론하는 데 사용할 수 있습니다. 예를 들어, 튜플 타입에서 첫 번째 요소의 타입을 추론하는 유틸리티 타입을 정의할 수 있습니다.

  ```typescript
  type FirstElement<T> = T extends [infer U, ...any[]] ? U : never;
  ```

- **조건부 타입 내에서의 다중 `infer` 사용**

  하나의 조건부 타입 내에서 여러 개의 `infer` 선언을 사용하여 복수의 타입을 동시에 추론할 수 있습니다. 이는 복잡한 데이터 구조나 함수 시그니처를 분해하고 분석할 때 유용합니다.

  ```typescript
  type FunctionArgsAndReturn<T> = T extends (...args: infer A) => infer R ? { args: A, returnType: R } : never;
  ```

### 주의점

- **성능 고려사항**: 복잡하고 중첩된 조건부 타입은 타입스크립트 컴파일러에 부하를 줄 수 있습니다. `infer` 사용이 많은 복잡한 타입은 컴파일 시간을 증가시킬 수 있으므로, 성능과 가독성 사이에서 적절한 균형을 찾는 것이 중요합니다.

- **가독성 유지**: 고급 타입 추론 로직은 코드의 가독성을 저하시킬 수 있습니다. `infer`를 사용할 때는 타입의 명확성과 유지보수성을 위해 충분한 주석과 문서화를 고려해야 합니다.

### 실제 개발 환경에서의 응용

- **라이브러리와 프레임워크 개발**: 타입스크립트로 라이브러리나 프레임워크를 개발할 때, `infer`를 사용하면 사용자가 제공하는 콜백 함수나 컴포넌트 프롭스의 타입을 정교하게 추론하고, 이를 기반으로 타입 안전한 API를 설계할 수 있습니다.

- **타입 추론 강화**: 기존 자바스크립트 프로젝트를 타입스크립트로 마이그레이션하는 과정에서, `infer`를 사용하여 동적으로 변화하는 데이터 구조의 타입을 보다 정확하게 추론하고 타입 안전성을 향상시킬 수 있습니다.

`infer` 키워드는 타입스크립트의 타입 시스템을 깊게 이해하고 활용하려는 개발자에게 강력한 도구를 제공합니다. 적절히 사용될 때, `infer`는 타입스크립트의 고급 기능과 타입 안전성을 최대한 활용할 수 있게 해주며, 복잡한 타입 조작을 간결하고 효율적으로 처리할 수 있도록 돕습니다.













---



## Reference

- <https://inpa.tistory.com/entry/TS-📘-타입스크립트-조건부-타입-완벽-이해하기>

