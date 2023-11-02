---
layout: note
title: Clean Architecture Chapter 1 - 소개
date: 2023-11-02
---




## 1장. 설계와 아키텍처란?

- Architecture : 고수준의 무언가를 가리킬 때 흔시 사용됨
- Design : 저수준의 구조 또는 결정사항 등을 의미할 때가 많음

- Architecture와 Design은 차이가 없음
    - software 설계에 있어서도 저수준의 세부사항과 고수준의 구조는 모두 전체 설계의 구성 요소임
    - 고수준에서 저수준으로 향하는 의사결정의 연속성만이 있을 뿐

- 목표
    ```
    software architecture의 목표는 필요한 system을 만들고 유지보수하는 데 투입되는 인력을 최소화하는 데 있다.
    ```
    - 설계 품질을 재는 척도는 고객의 요구를 만족시키는 데에 드는 비용을 재는 척도와 같음
        - 비용이 낮고 system의 수명이 다할 때까지 낮게 유지할 수 있는 것이 좋은 설계
        - 새로운 기능을 출시할 때마다 비용이 증가한다면 나쁜 설계

- 빨리 가는 유일한 방법은 제대로 가는 것
    - code와 설계의 구조를 깔끔하게 만들려는 생각을 하지 않으면, 점점 비용이 높아지고 따라서 개발자의 생산성은 0에 수렴하게 됨
        - 엉망이 된 상황에 대처하는 데에 노력이 들어가기 때문


## 2장. 두 가지 가치에 대한 이야기

- software 개발자는 '행위(behavior)'와 '구조(structure)'의 두 가치를 모두 높게 유지해야 함

- 첫 번째 가치 : 행위
    - programmer가 sofrware를 만드는 이유는 기계가 이해관계자를 위해 수익을 창출하거나 비용을 절약하도록 만들기 위함
    - 따라서 개발자는 요구사항에 따라 개발하고 요구사항을 위반했을 때 debugging함
        - 그러나 이것이 개발자가 해야할 일의 전부는 아님

- 두 번째 가치 : 구조
    - software는 '부드러운(soft)'와 '제품(ware)'의 합성어
    - software를 만드는 이유 : 기계의 행위를 쉽게 변경할 수 있도록 하기 위함
    - 따라서 software는 변경하기 쉬워야 함
    - 변경사항을 적용하는 데에 드는 어려움은 변경되는 범위(scope)에 비례해야하며, 변경사항의 형태(shape)와는 관련 없어야 함
    - 나쁜 architecture는 범위가 비슷한 일련의 변경사항에도, code의 복잡도는 지속적으로 증가한 상태이기 때문에 뒤로 갈수록 같은 범위의 변경에 대해 비용이 많이 들게 됨
    - architecture가 특정 형태를 다른 형태보다 선호하면 할수록, 새로운 기능을 그 구조에 맞추는 것이 힘들어짐
    - architecture는 독립적이어야 하고, 그럴수록 더 실용적임

- 기능 (software의 동작) vs Architecture (software system 변경의 용이성)
    - 업무 관리자는 기능을 우선할 수 있지만, 개발자는 구조에 더 신경을 써야 함
    - ex) 두 program의 비교
        - 완벽하게 동작하지만 수정이 불가능한 program (변경에 드는 비용 >>>> 창출되는 수익)
            1. 요구사항이 변경될 때 동작하지 않음
            2. 결국 program이 돌아가도록 만들 수 없음
            3. 쓸모 없어짐
        - 동작은 하지 않지만 변경이 쉬운 program
            1. program이 돌아가도록 만들 수 있음
            2. 변경사항이 발생하더라도 여전히 동작하도록 유지보수할 수 있음
            3. 앞으로도 유용한 채로 남음

- 아이젠하워 Matrix
    | | |
    | - | - |
    | 중요O 긴급O | 중요O 긴급X |
    | 중요X 긴급O | 중요X 긴급X |
    - 우선 순위
        1. 긴급하고 중요한
        2. 긴급하지는 않지만 중요한
        3. 긴급하지만 중요하지 않은
        4. 긴급하지도 중요하지도 않은
    - 업무 관리자와 개발자가 흔히 하는 실수는 세 번쩨에 위치한 항목을 첫 번째로 격상시키는 것
    - 기능의 긴급성이 아닌 architecture의 중요성을 설득하는 일은 software 개발팀이 책임져야 함

- 개발자는 software를 안전하게 보호해야 할 책임이 있으며, 이것이 개발자가 고용된 중요한 이유 중 하나이기도 함




---




# Reference

- Clean Architecture (도서) - Robert C. Martin