# 자바스크립트 패턴과 테스트

## 2 도구다루기

### 테스팅 프레임워크

Jasmine
<https://jasmine.github.io/>
<https://jasmine.github.io/setup/nodejs.html>
<http://karma-runner.github.io/>

describe : 테스트 꾸러미
function() : 구현부
it : 단위 테스트

```javascript
describe('무엇을 테스트 할지 서술',  function() {
it('단위 테스트 내용 서술', function() {
  /* 단위 테스트 구현부 */
}
});
```

### TDD

잘못된 코드 발견하기
테스트성을 감안하여 설계하기
꼭 필요한 코드만 작성하기
안전한 유지 보수와 리팩토링
실행 가능한 명세

### Jasmine

행위기반 테스트 (behavior-based)
BDD (Behavior-Driven Development) : 일상 언어로 기술
TDD

it : 함수 각자의 개별 단위 테스트
expect : 검사
tobe 기대값

beforeEach/afterEach : 테스트 이전 이후 작업

### 기대값과 매쳐

expect : 검사
tobe 기대값

expect(testReservation.passengerInformation).tobe(testPassenger);

매쳐 확장
<https://github.com/velesin/jasmine-jquery>

### 스파이

스파이 : 테스트 더블 (test double)
함수/객체의 볼래 구현부를 테스트 도중 다른 코드로 대체한 것을 말한다. 웹서비스 같은 외부 자원과의 의존 관계를 없애고 단위 테스트의 복잡도를 낮출 목적으로 사용된다. DI

더미(dummy), 틀(stub), 스파이(spy), 모의체(take), 모형(mock)

### 의존성 주입 프레임워크 (dependency injection)

<DI: Dependency Injection>

```javascript
// 운영환경
var attendee = new Attendee(new ConferenceWebSvc(), new Messenger(), id);

// 개발(테스트) 환경
var attendee = new Attendee(fakeService, fakeMessenger, id);
```

```javascript
DiContainer = function() {
};

// 인젝터블명, 의존성 명을 담은 배열, 인젝터블 객체를 반환하는 함수
DiContainer.prototype.register = function(name, dependencies, func) {
  // 처음 버전이라 하는 일이 없다.
};
```

### 의존성 주입이 필요한 상황

객체 또는 의존성 중 어느 하나라도 DB, 설정 파일, HTTP, 기타 인프라 등의 외부 자원에 의존하는가?
객체 내부에서 발생할지 모를 에러를 테스트에서 고려해야 하나?
특정한 방향으로 객체를 작동시켜야 할 테스트가 있는가?
서드파티(third-party) 제공 객체가 아니라 온전히 내가 소유한 객체인가?

### 의존성 주입 프로세스

1. 애플리케이션이 시작되자마자 각 인젝터블(injectable)명을 확인하고 해당 인젝터블이 지닌 의존성을 지칭하며 순서대로 DI 컨테이너에 등록한다.
2. 객체가 필요하면 컨테이너에 요청한다.
3. 컨테이너는 일단 요청받은 객체와 그 의존성을 모두 재귀적으로 인스턴스화 한다. 그런다음 요건에 따라 필요한 객체에 각각주입한다.

### call, apply

```javascript
this 바인딩

call(this, 인자)
apply(this, [배열])
```

### 의존성 주입 프레임워크 활용

var attendee = new Attendee(new ConferenceWebSvc(), new Messenger(), id)

### 애스팩트 툴킷 (Aspect Toolkit)

어드바이스(advice) : 배포할 코드 조각
애스펙트 (aspect) or 횡단관심사 (cross-cutting concern) : 어드바이스가 처리할 문제

Aop.around('getSuggestedTicket', cacheAspectFactory())

### AOP

함수를 단순하게 유지
코드를 DRY하게 해줌

핵심 : 함수 실행타겟을 가로채 다른 함수(어드바이스)를 실행하기 직전 이나 직후, 또는 전후에 실행하는 것

### AOP Concept

"AOP Concept"

함수를 단순하게 유지
코드를 DRY하게 해줌

핵심 : 함수 실행타겟을 가로채 다른 함수(어드바이스)를 실행하기 직전 이나
직후, 또는 전후에 실행하는 것

### 코드 검사도구

JS Hint
<www.jshint.com>
