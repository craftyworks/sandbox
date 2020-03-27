# ES6

## const & let

### const
> 재할당이 불가능한 상수 선언. 선언된 오브젝트나 배열의 내부 변경은 OK

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



