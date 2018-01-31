# 자바스크립트 패턴과 테스트

## #1 기초다지기

### D3.js (Data Drivens Documents)


SVG 를 이용한 도표

``` javascript
<path d=”M19,130L100,60L190,160L,280,10”></path>
```

https://bl.ocks.org/mbostock/1044242
https://github.com/d3/d3-shape/blob/master/src/line.js

### 객체 조사 (상속, 프로퍼티)

if (something instanceof XYPair)

if (‘x’ in something)

if (something.hasOwnProperty('x'))

### 싱글 스레드

http://prashantb.me/javascript-call-stack-event-loop-and-callbacks/

### 대규모 시스템

통신 채널의 증가
클래스가 5개인 시스템보다 50개인 시스템에서 개발 및 유지 보수 난이도가 10이상 높다.

1. 스크립트는 모듈이 아니다.
   var myVariable = makeValue();

2. 스코프는 중첩 함수로 다스린다.
   클로져(closure) 이용

3. 규약을 지켜 코딩한다.

### SOLID 원칙

Single Responsibility Principle (단일 책임 원칙)
Open/Closed Principle (개방/폐쇄 원칙)
Liskov Substitution Principle (리스코프 치환 원칙)
Interface Segregation Principle (인터페이스 분리 원칙)
Dependency Inversion Principle (의존성 역전 원칙) 

### DRY 원칙

“반복하지 마라(Don’t Repeat Yourself)”

### 단위 테스트

단위 테스트는 미래를 위한 투자다.
단위 (Unit) : 함수 : 특정 조건에서 어떻게 작동해야 할지 정의

구성 : 준비(arrange), 실행(act), 단언(assert)
준비 : 단위를 실행할 조건
실행 : 테스트
단언 : 미리 정한 조건에 따라 예상대로 단위가 작동하는지 확인

테스트 꾸러미 (test suite) : 안정적인 애플리케이션 유지에 꼭 필요한 최선의 투자  

### Test-Driven Development, TDD

애플리케이션 코드를 짜기전 코드가 통과해야 할 단위 테스트를 먼저 작성
전체 단위 테스트 꾸러미를 만들어가는 TDD 방식을 따르면 단위 정의 와 인터페이스 설계에 도움이 된다. 

TDD 프로세스
1. 완벽히 변경하면 성공하나 그렇게 되기 전까지는 반드시 실패하는 단위 테스트 작성 (적색: red)
2. 테스트가 성공할 수 있을 만큼만 최소한으로 코딩 (녹색: green)
3. 애플리케이션 코드를 리팩토링 하며 중복 제거 (리팩터: refactor) 

“테스트 하기 쉬운 코드로 다듬어라.”

