# this

- 객체 = 프로퍼티(상태) + 메서드(동작) 
- 메서드는 객체의 상태를 참조하고 변경할 수 있어야 한다.
- 객체의 프로퍼티를 참조하기 위해 자신이 속한 객체를 가리키는 식별자를 참조할 수 있어야 한다.

```jsx
// 객체 리터럴
const circle = {
  radius = 5; // 프로퍼티
  getDiameter() { // 메서드
    return 2 * circle.radius;
  }
}
```
- 메서드가 호출되기 전에 객체가 생성되었고, circle 식별자에 객체가 할당되어 참조 가능

```jsx
// 생성자 함수로 인스턴스 생성
function Circle(radius) {
  ???.radius = radius;
}

Circle.prototype.getDiameter = function () {
  return 2 * ???.radius;
}

const circle = new Circle(5);
```
- 생성자 함수를 호출해야 인스턴스가 생성
- 인스턴스 생성 전엔 인스턴스를 가리키는 식별자를 알 수 없다.
- 이 때 필요한 특별한 식별자가 **this**
- **this**는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수

```jsx
// 객체 리터럴
const  circle = {
  radius = 5; // 프로퍼티
  getDiameter() { // 메서드
    return 2 * **this**.radius;
  }
}

// 생성자 함수
function Circle(radius) {
  this.radius = radius;
}

Circle.prototype.getDiameter = function () {
  return 2 * this.radius;
}

const circle = new Circle(5);
```
## this 바인딩

```jsx
// this 바인딩은 함수 호출 시점에 결정
console.log(this); // 전역 : window

function square(number) {
  console.log(this); // 일반 함수 내부 : window (strict mode에선 undefined)
  return number * number
}

var name = 'John';
const person = {
  name: 'Lee',
  getName() {
    console.log(this); // 메서드 내부 : 메서드가 호출한 객체 { name: 'Lee', getName: ƒ getName() }
    console.log(this.name); // 'Lee'
    function nothing() {
        console.log(this); // 메서드 내의 중첩 함수 : window
        console.log(this.name); // 'John'
        // 중첩함수, 콜백함수의 this를 메서드 this 바인딩과 일치시키기 위해 that 사용
        // 또는 .bind 메서드나 화살표 함수 사용
        console.log(that.name); // 'Lee'
     }
  }
}

function Person(name) {
  this.name = name;
  console.log(this); // 생성자 함수 내부 : 인스턴스 Person { name: 'Lee' }
}
```

### 일반 함수와 메서드 호출
- this의 값은 함수 호출을 하는 방법에 의해 결정된다. ⇒ 누가 this를 호출했나?
```jsx
const person = {
  name: 'Joy',
  callName() {
    console.log(this.name);
  }
}

// 누가 callName()을 불렀냐, 호출한 객체는 person
person.callName(); // 'Joy'

// 일반 함수로 호출, 브라우저가 호출한 셈
const callName = person.callName
callName(); // ''
```
결론적으로, callName 함수 객체는 person 객체에 포함된 것이 아닌 독립적으로 존재하는 객체 ⇒ **호출한 객체**에 바인딩
1. 다른 객체의 프로퍼티에 할당되어 다른 객체의 메서드가 될 수 있다.
```jsx
const anotherPerson = {
  name: 'Chandler'
}
// 메서드 할당
anotherPerson.callName = person.callName;
// 이번에 호출한 객체는 anotherPerson
anotherPerson.callName(); // 'Chandler'
```
2. 일반 변수에 할당해 일반 함수로 호출될 수 있다.
```jsx
// 메서드를 변수에 할당하고
const callName = person.callName
// 일반 함수로 호출
callName(); // ''
```

### 생성자 함수 호출
- 미래에 생성되는 인스턴스가 바인딩
```jsx
function Circle(radius) {
  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  }
}

const circle1 = new Circle(5); // this.radius => 5
const circle2 = new Circle(10); // this.radius => 10
```

### apply, call, bind 메서드에 의한 간접 호출
- apply, call 메서드는 함수를 호출하고
- 객체를 호출한 함수의 this에 바인딩한다.

```jsx
function getThisBinding(){
  return this;
}

const thisArg = { a: 1 };

getThisBinding(); // window
// getThisBinding 함수 호출 + 인수로 전달하는 객체를 this에 바인딩
getThisBinding.apply(thisArg); // { a: 1 }
getThisBinding.call(thisArg); // { a: 1 }
```

- 차이점은 함수의 인수를 전달하는 형식
```jsx
const thisArg = { a: 1 };

getThisBinding.apply(thisArg, [1, 2]); // 배열로 전달
getThisBinding.call(thisArg, 1, 2); // 쉼표로 구분한 리스트로 전달
```

- Bind 메서드는 함수를 호출하지 않는다.
```jsx
function getThisBinding(){
  return this;
}

const thisArg = { a: 1 };

// getThisBinding 바인딩 교체 함수 생성
getThisBinding.bind(thisArg); // getThisBinding 함수를 새롭게 생성
// 별도 호출 필요
getThisBinding.bind(thisArg)(); // { a: 1 }
```

| 함수 호출 방식 | this 바인딩 |
| --- | --- |
| 일반 함수 | 전역 객체(브라우저 window, node undefined) |
| 메서드 | 메서드를 호출한 객체 |
| 생성자 함수 | 생성자 함수가 생성할 인스턴스 |
| 메서드 간접 호출 | 첫번째 인수로 전달한 객체 |
