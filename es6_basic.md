# ES6

## 변수, 상수, 타입

### expression vs statement

**expression**
> 값으로 평가될 수 있는 문. 결과가 값인 문장. 할당에 사용할 수 있다.
> 변수와 상수, 리터럴은 그 자체로 expression
  
### identifier

>식별자. 변수와 상수, 함수의 `이름`

### primitive type

> 원시 타입. 

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
### 연산자 === 를 써라
> 일치 연산자 `===` 는 두 값이 같은 객체를 가리키거나, 같은 타입이고 값도 같은 경우에만 true 를 반환한다.
> 항상 일치 연산자 `===`, `!==` 를 써라

```javascript
const n = 5
const s = '5'

n === s // false
n == s // true <- 이러니 쓰지 마라
```

### 참과 거짓

> javascript 에서 다음은 `거짓`으로 판정된다. 이들 외에는 모두 `참` 이다.
* undefined
* null
* false
* 0
* NaN
* ''(빈문자열)

### OR 표현식을 이용한 할당

> 할당이 목적인 if 문을 OR 표현식을 써서 간결하게 표현이 가능

```javascript
if (!options) options = {}
```
> 위 코드는 아래와 같이 변경이 가능
```javascript
options = options || {}
```

논리 연산자는 피 연산자가 Boolean 이 아닌 경우, 그 결과를 **결정** 한 값을 리턴한다. 이 성질을 이용해서 null 이나 undefined 가 아닌 값을 할당 해야 할 때 OR 연산자를 이용하면 간결한 표현이 가능하다.

```javascript

// paramA, paramB, paramC 순으로 null 이 아닌 경우 할당을 시도. 
// 모두 null 이면 디폴트 값 {} 을 적용
const option = paramA || paramB || paramC || {}

```

### typeof 연산자

expression | result 
---|---
typeof undefined | 'undefined'
typeof null | **'object'** 💥
typeof {} | 'object'
typeof true | 'boolean'
typeof 1 | 'number'
typeof '' | 'string'
typeof Symbol() | 'symbol'
typeof function() {} | 'function'

> `typeof` 는 연산자 이므로 괄호 불필요

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


## 해체 할당 ( destructuring assignment )

### Object

> 객체를 해체하여 객체의 프로퍼티 이름과 동일한 이름을 가진 변수에 값을 할당

```javascript

const obj = {b: 2, c: 3, d: 4}

const {a, b, c} = obj

a // undefined
b // 2
c // 3
```
### 배열

> 배열 요소의 순서에 따라 할당

```javascript
const arr = [1, 2, 3]

let [x, y] = arr
x // 1
y // 2
```

### Function Argument

```javascript
// Object 파라미터 해체
function getTest( {artifact, module, version} ) {
  return `${artifact}.${module}.${version}`
}

const info = {artifact: 'java', module: 'io', version: '1.0'}
getTest(info) // 'java.io.1.0'

// 배열 파라미터 해체
function getTest( [artifact, module, version] ) {
  return `${artifact}.${module}.${version}`
}

const arr = ['java', 'io', '1.0']
getTest(arr) // 'java.io.1.0'
```

## Function

### Basic

> 함수는 함수명만 사용 시 해당 함수에 대한 참조형이 된다. 함수명은 변수나 객체의 프로퍼티, 배열의 요소등에 할당이 가능하다. 할당된 함수에 대한 참조는 괄호를 사용하여 호출이 가능하다.

```javascript
function test() { console.log('test') }

const f = test
f() // 'test'

const o = {}
o.f = test
o.f() // 'test'

const arr = []
arr[0] = test
arr[0]() // 'test'
```

> `값` 또는 `expression` 뒤에 괄호를 쓰면 javascript 는 그 `값`을 `fuction` 으로 간주하고 함수 호출을 시도한다.

**Overloading 없다**
> 동일한 함수명을 사용하고 파라미터 리스트에 따라 구분되는 그딴거 javascript 에는 없다.

### 가변 파라미터 ...
> ES5 에서 사용하던 `arguments` 변수 대신 사용할 수 있는 spread 연산자 `...` 을 파라미터에 정의하여 사용할 수 있다. 가변 파라미터를 배열로 받을 수 있다.

```javascript

function test(infix, ...words) {
  let sb = ''
  for(str in words) {
    sb += str + infix
  }
  return sb.slice(0, -1 * infix.length)
}

test('_', 'a', 'b', 'c') // 'a_b_c'
```

### default parameter value

> 선언된 파라미터가 전달되지 않으면 `undefined`로 할당된다. ES6 에서는 default 값을 설정할 수 있다.

```javascript
function test(a, b = 10) {
  return a * b
}

test(5) // 50
```
### Method

> 객체의 프로퍼티인 함수를 `Method` 라고 부른다. ES6 에서 `Method` 를 간편하게 선언할 수 있는 문법이 추가되었다.

```javascript
const obj = {
  name: 'james',
  log: function() {
    console.log(`name: ${this.name}`)
  },
  log2() {
    this.log()
  }
}
```


### Arrow Function

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