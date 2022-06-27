# [Javascript] 02. basic2

## 연산자

### 비교연산자

`>`, `<`, `>=`, `<=`, `===`, `!==`을 쓴다.

파이썬과 다르게 `===`, `!==` 등호가 하나 더들어간다.



### 논리연산자

- and연산 : `&&`

- or연산 : `||`

- not연산 : !를 붙이고 사용.
  - 예) `console.log(!true)` -> `false`



### typeof 연산자

사용한 자료형이 무엇인지 알려주는 연산자.
사칙연산보다 연산자 우선순위가 높다.

```javascript
console.log(typeof 10);
console.log(typeof "str")
console.log(typeof true)
```

```
//출력
number
string
boolean
```

> javascript는 1과 1.0을 구분하지 않고 number라고 한다. (int, float이런거 없나봄?)
>
> 문자열은 ' ', " ", \` \` 사용 가능





## 형변환 (Type Conversion)

`String()`, `Number()`, `Boolean()` 함수로 형변환하면 된다.



### 자동 형변환

서로 다른 자료형이더라도 자바스크립트는 알아서 자동으로 형변환을 통해 연산을 수행한다.

이는 장점이 될 수도 있지만 단점일 수도 있다. 어디서 잘못된 형변환이 일어나 연산되는지를 알 수 없기 때문이다. 그래도 규칙은 있으니 규칙을 알아보자.

- 산술 연산자
  - `+` : 문자+숫자 -> 문자열
  - `-` : 숫자-불리언 -> 숫자
  - `/` : 숫자/문자 -> 숫자
  - `**` : 문자**불리언 -> 숫자
  - `%` : 숫자%문자 -> NaN

- 비교 연산자
  - 보통 비교연산자인 경우 숫자로 변환해서 참거짓을 따진다.
- 같음 연산자 (==, ===, !=, !==)
  - ===, !== : 일치, 불일치 -> 형변환 안일어남
  - ==, != : 동등, 부등  -> 형변환이 일어남



## 탬플릿 문자열 (Template String)

파이썬의 f-string과 같은 기능

주의) `'`작은 따옴표가 아니라 ` `` `(backtick)를 써야한다.

```javascript
let year = 2022;
let month = 6;
let day = 23;

console.log(`오늘의 날짜는 ${year}년 ${month}월 ${day}일 이다.`)
// 파이썬 : print(f'오늘의 날짜는 {year}년 {month}월 {day}일 이다.')과 동일
```



## null & undefined

둘 다 `값이 없다`를 의미

- null : 의도적으로 표현할 때 사용하는 값
  - 예로 변수를 선언 할 때 `let myVar=null;` 처럼 지정해서 초기화해주는 것(값이 없다는 것을 의미)
- undefined : 값이 없다는 것을 확인하는 값
  - 예로 변수를 선언했는데 값으로 초기화를 안해줬을 때 undefined가 뜸





## 참고

### 연산자 우선순위

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Operator_Precedence
