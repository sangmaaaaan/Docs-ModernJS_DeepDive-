# let, const 키워드와 블록 레벨 스코프

## var 키워드로 선언한 변수의 문제점

### 변수 중복 선언 허용함

- var 키워드로 선언한 변수는 오로지 함수의 코드블록만을 지역 스코프로 인정한다.따라서 함수 외부에서 var키워드로 선언한 변수는 코드 블록 내에서 선언해도 모두 전역 변수가 된다.
- for문의 변수 선언문에서 var 키워드로 선언한 변수도 전역변수다.
- 변수 호이스팅에 의해 var 키워드로 선언한 변수는 변수 선언문 이전에 참조할 수 있다.

### let 키워드

- 변수 중복 선언 금지
- var 과 다르게 let은 키워드로 이름이 같은 변수를 중복 선언하면 문법 에러가 발생한다.
- 블록레벨 스코프 : let 키워드로 선언한 변수는 모든 코드 블록을 지역 스코프로 인정하는 블록 레벨 스코프를 따른다.

```javascript
let i = 10;
function foo() {
  let i = 100;

  for (let i = 1; i < 3; i++) {
    console.log(i); // 1 2
  }

  console.log(i); // 100
}

foo();

console.log(i); // 10
```

위 예제에 대한 출력값을 주석으로 써놓았다. 위에서부터
전역스코프 > 함수 레벨 스코프 > 블록레벨 스코프

- let 키워드로 선언한 변수는 선언단계 + 초기화단계로 분리되어 진행한다.
  스코프의 시작지점부터 초기화시점까지 변수를 참조할 수 없는 구간을 일시적 사각지대(TDZ)라고 부른다.

- let 키워드도 결국 변수 호이스팅이 발생한다.

- 전역객체와 let : let 키워드로 선언한 전역 변수는 전역 객체의 프로퍼티가 아니다. window.foo와 같이 접근할 수 없다.

### const 키워드

- const 키워드로 선언한 변수는 반드시 선언과 동시에 초기화해야 한다.그렇지 않으면 문법에러가 발생함
- const 키워드로 선언한 변수는 블록레벨 스코프를 가지며, 변수 호이스팅이 발생하지 않는 것처럼 동작함
- 재할당 금지 : var, let 키워드로 선언한 변수는 재할당이 자유로우나 const 키워드는 금지
- 상수 : 상수는 재할당이 금지된 변수
- const 키워드로 선언된 변수에 객체를 할당한 경우 값을 변경할수있다.

#### 결론 : var은 거의 쓰지 않고, 재할당이 필요한 경우에만 let을 사용하고 변경이 발생하지 않고 읽기전용으로 사용하는 원시 값고 객체에는 const 키워드를 사용하자.
