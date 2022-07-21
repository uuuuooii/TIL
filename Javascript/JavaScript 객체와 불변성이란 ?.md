[블로그 가기](https://blog.naver.com/eunhey2717/222821345831)
### 기본형 데이터와 참조형 데이터

자바스크립트가 데이터를 처리하는 과정이

Primitive Type (기본형 타입)    / Reference Type (참조형 타입) ​​이 있다.

​

​

[ Primitive Type ]

기본형은 값을 그대로 할당한다.

- Number (숫자)

- String (문자)

- Boolean(불리언)

- null

- undefined 

- Symbol(ES6에 추가, 객체 속성을 만드는 데이터 타입)

​

[  Reference Type ]

- 값이 저장 된 주소값을 할당

- Object (객체)

- Array (배열)

- Function (함수)

- Date (날짜)

- RegExp(정규표현식) 등

​

+ ES6에서 Map, WeakMap, Set, WeakSet 등 추가됨.

객체의 하위 분류에 속한다.

​

​

[ 기본형 VS 참조형 ]

기본형은 불변성을 뛴다.

기본형은 값이 담긴 주솟값을 바호 복제

참조형은 값이 담신 주솟값들로 이루어진 묶음을 가리키는 주솟값을 복제

​

[ 데이터 타입이 왜 필요할까? ]

값을 지정할 때 확보해야 하는 메모리 공간의 크기를 결정하기 위해

값을 참조할 때 한 번에 읽어 들여야 할 메모리 공간의 크기를 결정하기 위해

메모리에서 읽어 들인 2진수를 어떻게 해석할지 결정하기 위해

​

​

[ 불변 객체를 만드는 방법 ]

불변( immutability )이란 뭘까? 단어에서 유추해볼 수 있다시피 '변하지 않는 뜻'이라고 생각하면 된다.

그럼 '불변 객체'란? '변하지 않는 객체' 즉 이미 할당된 객체가 변하지 않는다는 뜻을 가지고 있다.

자바스크립트에서 불변 객체를 만들 수 있는 방법은 기본적으로 2가지 인데 const와 Object.freeze()를 사용하는 껏이다.

​

​

[ const ]

자바스크립트 키워드 중 하나인 const이다.

ES6 문법부터 let 과 const를 지원한다.

​

const키워드는 변수를 상수로 선언할 수 있다.

일반적으로 상수로 선언된 변수는 값을 바꾸지 못하는 것으로 알려져 있다.

그렇다면 상수로 선언한 객체는 불변 객체일까?

```javascript
const test = {};
test.name = "apple"
console.log(test); // {"apple"}
```
ES6에서의 const는 할당된 값이 상수가 되는 것이 아닌 바인딩된 값이 상수가 되는, 즉 test변수가 상수가 되기 때문에 const 키워드로 선언된 test 변수에는 객체 재할당은 불가능하지만 객체의 속성은 변경 가능하다.

​

재할당이 불가능 한 이유는 변수와 값(객체) 사이의 바인딩 자체가 변경이 되기 때문에 상수인 test변수는 재할당이 불가능 한 것이고

객체의 속상이 변경가능 한 이유는 실제 객체가 변경은 되지만 ({} -> name: "apple") 객체와 변수 (test)사이의 바인딩은 변경이 되지 않기 때문에 객체의 속성은 변경 가능한 것이다.

​

때문에 비록 재할당은 불가능하지만 객체의 속성을 변경함으로 인해 변수에 바인딩된 객체의 내용까지 변경이 되기 때문에 불변객체라고 하기는 힘들다.

따라서 Object.freeze()라는 JS내장 메소드도 살펴보도록 하겠다.

​

​

[Object.freeze()]

자바스크립트에서 기본적으로 제공하는 메소드인 Object.freeze() 메소드이다. 공식 문서에서는 "객체를 동결하기 위한 메소드"라도 적혀 있다.

​

그렇다면 이 메소드를 사용하면 불변 객체를 만들 수 있을까? 먼저 이 메소드의 사용법부터 알아보면,

```javascript
let test = {
    name : 'kim'
}
Object.freeze(test);
```
사용법은 간단하다. test변수에 key value를 가진 객체를 바인딩 후 Object.freeze(test)를 사용해 바인딩된 변수를 동결 객체로 만들었다.때문에 test객체는 객체의 속성을 변경하는 시도는 불가능 하다.

​
```javascript
test.name = 'Jung';
console.log(test) //{name: 'kim'}
```
위와 같이 객체의 속성을 변경하는 시도는 무시된다.

그러나 Object.freeze()는 동결된 객체를 반환하지만 객체의 재할당은 가능하다.

​
```javascript
test = {
    age : 15
};
console.log(test); // {age: 15}
```
위와 같이 객체의 재할당은 가능하다. 

때문에 Object.freeze()도 불변 객체라고 할 수 는 없을 것 같다.

그럼 결국 불변 객체는 어떻게 만들 수 있냐면

​

const와 Object.freeze()를 조합하여 만들 수 있다.

(const의 재할당불가 + Object.freeze()의 객체 속성 변경 불가)

​

그렇다면 아래 코드와 같이 사용하면 된다.

``` javascript
const test = {
    'name' : 'jung'
}; 
Object.freeze(test);
```
먼저 const 키워드로 바인딩 된 변수를 상수화 시킨 다음, Object.freeze()로 해당 변수를 동결 객체를 만들면 객체의 재할당과 객체의 속성 둘 다 변경 불가능한 불변 객체가 된다.

​

얕은 복사와 깊은 복사

[ 얕은 복사 (Shallow copy)]

우리가 흔히 알고 있듯이, 객체가 담겨 있는 변수를 다른 변수에 할당하면 calll by reference(데이터 복사가 아닌 참조)가 일어나게 되어, 한 변수의 데이터를 변경하면 다른 변수의 데이터도 함께 변경이 된다.

```javascript
const personq1 = {name:'inyong'};

const person2 = person1;

person1.name = 'jung';

// result

person2.name // 'jung'
```

person1 === person2; // true - 같은 데이터 주소를 바라보고 있는 두 변수
데이터가 그대로 하나 더 생성된 것이 아닌 해당 데이터의 메모리 주소를 전달하게 돼서, 결국 한 데이터를 공유하게 되는 것이다.

​

[ 깊은 복사 (Depth copy) ]

한 데이터의 공유가 아닌, 똑같은 구조의 객체를 하나 더 생성하여 따로 사용하고자 할 때가 있다.

​

이럴 때 우리는 '깊은 복사'라는 개념을 사용한다.

​
```javascript
const person1 = { name : "inyong"};

const person2 = Object.assign({}, person1);

person1.name = "jung";

//result
```

person2.name // 'inyong' - 전혀 다른 메모리 주소의 데이터이므로,
person2의 값은 변하지 않음.

person1 === person2 // false - 형태만 같고, 각자 다른 메모리 주소에 저장되어 있는 데이터다.
데이터 참조가 아닌 객체의 형태를 그대로 복사하게 함으로써, 한 객체가 변경되도 다른 객체의 데이터에는 영향이 없게 된다.

​

​

​

​

​


