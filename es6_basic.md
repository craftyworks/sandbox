# ES6

## 용어
  * value
  * literal
    * 값을 프로그램 안에서 직접 지정
  * expression
  * statement
  * undefined
  * identifier
    * 식별자. 변수와 상수, 함수의 `이름`
  * primitive
    * 원시 타입. 
    * 숫자, 문자열, 불리언, null, undefined, *Symbol*
    * 위 6가지 원시 타입 외에는 Object type 이다.
    * 원시 타입은 불변(immutable)

### 숫자는 double

> javascript 에서 숫자형 데이터 타입은 `double` 하나다. `float`, `int` 이딴 거 없다.

```javascript
console.log(0.1 + 0.2)
// 0.30000000000000004
```
### 숫자로 형변환 하기

**Number 생성자**
```javascript
const str = '33.3'
const num = Number(str)
```

**parseInt**
> 10진수 등 기수를 파라미터로 지정 가능하다. 숫자뒤에 문자열이 붙은 경우, 숫자로 판단 가능한 부분 까지만 숫자로 변환 해준다.

```javascript
parseInt('16 volt') //16
parseInt('15.5 kwh') // 15.5
parseInt('Hy 2002') // NaN
```

### String wrapper 는 일시적으로 생성 후 파괴된다.

> . 연산자로 접근 시 임시로 생성된 후 바로 파괴된다.

```javascript
const str = 'hello'
str.property_name = 'james'
console.log(str.property_name) // <- undefined
```
### Array
  * 크기가 고정되지 않는다. 언제든 추가, 삭제 가능
  * ArrayIndexOutOfBoundException 같은거 없다.

```javascript
const arr = []
arr[10] = 'a'
arr.length == 11
```

### Symbol
> ES6 에서 새로 나옴

### null & undefined
> null 은 프로그래머에게 허용된 데이터 타입이고 undefined 는 자바스크립트 자체에서 사용한다.

### 문자열 template
> 보간법(interporation). 문자열의 정해진 위치에 값을 채워 넣는다. 백틱(`) 을 사용한다.

```javascript>
let currentTemp = 19.5
const message = `The current temperature is ${currentTemp}`
```

## const & let

### const
> 재할당이 불가능한 상수 선언. 선언된 오브젝트나 배열의 내부 변경은 OK

가능하면 변수대신 상수를 사용한다. 일단 상수로 선언하고, 변경되어야 하면 변수로 수정한다.

### let
> Block scope 을 가지는 변수

### var
> function scope 를 가지는 변수. 이젠 쓰지 마라.

```javascript
var a = 100
function print2() {
    if(true) {
        var a = 10
        console.log(a)
    }
    console.log(a)
}
```
> 위 코드 실행 결과 `10` 이 두 번 찍힌다.

## Arrow Function

```
// ES5
var sum = funcion(a, b) {
  return a + b
}

// ES6 Arrow Function Style
const sum = (a, b) => {
    return a + b
}
```

> One line statement 인 경우 `{` 와 `}` 생략 가능하다. 이 경우 `return` 키워드는 생략된다.

```javascript>
const sum = (a, b) => a + b
```

> 파라미터가 하나 인 경우는 `(` 와 `)` 생갹 가능하다.

```javascript
var cube = (num) => num * num * num

var cube = num => num * num * num
```



