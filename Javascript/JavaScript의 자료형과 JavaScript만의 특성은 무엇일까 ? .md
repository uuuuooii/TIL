[블로그 가기](https://blog.naver.com/eunhey2717/222819175424)
## JavaScript의 자료형과 JavaScript만의 특성은 무엇일까 ? 


### Javascript 란?

- 자바스크립트(Javascript)는 객체 (Object) 기반의 스크립트 언어이다.

- HTML로는 웹의 내용을 작성하고, CSS로는 웹을 디자인하며, 자바스크립트로는 웹의 동작을 구현할 수 있다.

- 자바스크립트는 주로 웹 브라우저에서 사용되나, Node.js와 같은 프레임워크를 사용하면 서버 측 프로그래밍 에서도 사용할 수 있다.

​

### Javascript 특징

1. 자바스크립트는 객체 기반의 스크립트 언어이다.

2. 자바스크립트는 동적이며, 타입을 명시할 필요가 없는 인터프리터 언어이다.

-자바스크립트는 동적 타입 언어이기 때문에 런타임 속도는 빠르지만 타입 안정성이 보장되지 않는다.

-타입스크립트는 정적 타입 언어이기 때문에 컴파일 시간이 조금 걸리지만, 안정성이 보장된다.

3. 자바스크립트는 객체 지향형 프로그래밍과 함수형 프로그래밍을 모두 표현할 수 있다.

(자바스크립트는 웹 브라우저에 포함된 자바스크립트 인터프리터가 소스 코드를 직접 해석하여 바로 실행해 준다.)

​

​

### 느슨한 타입(loosely typed)의 동적(dynamic)언어

느슨한 타입은 타입 없이 변수를 선언하는 것입니다.

반면에 강력한 타입(strong typing)을 사용하는 언어는 타입과 함께 변수를 선언해야함 한다.
```javascript
// javascript (loose typing)
let a = 13; // Number 선언
let b = "thirteen" // String 선언

// java (strong typing )
int a = 13; // int 선언
String b = "thirteen" // String 선언
```
자바스크립트 예제에서 a와 b 둘 다 let type 으로 선언 되었다는 걸 기억하자.

하지만 이것이 타입이 없다거나 let 타입이라는 뜻은 아니다.

자바스크립트의 변수는 타입을 가지고 있지만, 내부적으로 정해질 뿐이다.

위의 예제에서는, a의 타입은 Number, b의 타입은 String이 될 것이다. 자바스크립트는 모두 5개의 Primitive type을 가지고 있는 데 위의 둘과 Boolean, Null, Undefined이다.

​

[문제점 & 보완할 수 있는 방법]

실행 도중에 변수에 예상치 못한 타입이 들어와 타입에러가 발생할 수 있다.

동적타입 언어는 런타임 시 확인할 수 밖에 없기 때문에, 코드가 길고 복잡해질 경우 타입 에러를 찾기가 어려워진다.

이러한 불편함을 해소하기 위해 타입스크립트나 Folw등을 사용할 수 있다.

### 타입 변환(Type Coercion)

타입 변환은 느슨한 타입과 아주 가까운 관계가 있는 주제이다.

내부적으로 타입이 관리되기 때문에, 종종 타입들이 내부적으로 바뀔 때도 있다.

타입 변환의 규칙을 아는 것은 아주아주 중요하다.

다음과 같은 표현식을 생각해보자.
```javascript
7 + 7 + 7; // = 21  
7 + 7 + "7"; // = 147  
"7" + 7 + 7; // = 777 
```
위의 예제에서 계산 식은 String을 만나기 전까지 정상적으로 계산된다.

일단 String을 만난 이후로는 모든 숫자가 String으로 변환되고 결헙(concatenate)된다.

​

타입 변환은 또한 값 비교를 할 때도 일어난다.

하지만 === 연산자를 써서 타입 변환을 막을 수 있다.
```javascript
1 == true; // = true  
1 === true; // = false  
  
7 == "7"; // = true  
7 === "7"; // = false
```
parseInt나 parseFloat 같은 명시적으로 타입 변환을 하는 함수도 존재한다.(둘 다 String에서 Number로 변환하는 함수이다.)

​

이중 부정 ( ! ! ) 을 사용해서 Number를 Boolean으로 변환할 수 있다.

다음의 예제를 보자

```javascript
true == !"0"; // = false
true == !!"0"; // = true
```

​

### ==, === 둘의 차이는?

1. == 연산자

자바스크립트는 타입 변환에 대해 유연하게 동작한다.

== 연산자는 두 피연산자의 값의 타입이 다를 경우 자동으로 일부 피연산자의 타입을 변환 후 값을 비교 한다.

​

타입을 비교하지 않으므로 === 연산자에 비해 느슨하다고 할 수 있다.

10 == 10    // true
10 == '10'  // true
true == 1   // true
true == '1' // true
true == 'true' // false

null == undefined // true
10 == '10 '

두 피연산자에서 하나가 숫자형이고 다른 하나가 문자열이면, 문자열을 숫자로 변환 후 값을 비교한다.

​

true == 1

두 피연산자에서 불리언 값이 존재하면, 불리언 값을 1로 변환 후 값을 비교한다.

​

ture == '1'

불리언 값을 1로 변환하면, 1 == '1'이 되는데, 문자열 '1'을 숫자로 변환 후 값을 비교한다.

즉, 1 == 1로 비교되며, true를 반환한다.

​

ture == 'true'

불리언 값을 1로 변환하면, 1 == 'ture'가 되는데, 문자열 'true'는 숫자로 변환 불가능 하다.

즉, 1== 'true'로 비교되며 false를 반환한다.

​

null == undefined

null 과 undefined는 엄연히 다르지만, == 연선자는 true를 반환한다.

​

2. === 연산자

== 연산자는 값을 비교하기 전에 타입이 다를 경우 타입을 변환 후 값을 비교했다.

하지만, === 연산자는 타입을 변환하지 않으므로 == 연산자에 비해 비교하는 방식이 엄격하다.

​

즉, == 연산자는 타입이 다르면, false를 반환한다.

10 === 10   // true

10 === '10' // false

true === 1  // false

true === 'true' // false

null === undefined // false

NaN === NaN // false
=== 연산자의 특징

NaN값은 자기 자신을 포함하여 어떠한 값과도 일치하지 않는다. 즉, === 연산자에 NaN 값이 존재하는 경우 항상 false 입니다.

정확한 문자열을 비교하기 위해서는 localeCompare 메서드를 사용하는 것이 좋다. 문자열은 눈으로 보았을 떄 , 동일하더라도 인코딩 방식이 다르게 되어있을 수 있기 대문이다.

​

​

### undefined와 null의 차이점

undefinde은 변수를 선언하고 값을 할당하지 않은 상태, null은 변수를 선언하고 빈 값을 할당한 상태(빈 객체)이다.

즉, undefined는 자료형이 없는 상태이다.

따라서 typeof를 통해 자료형을 확인해보면 null은 object로, undefined는 undefined가 출력되는 것을 확인할 수 있다.

​
```javascript
typeof null // 'object'
typeof undefined // 'undefined'
null === undefined // false
null == undefined // true
null === null // true
null == null // true
!null // true
isNaN(1 + null) // false
isNaN(1 + undefined) // true
```

[ undefined]

undefind는 원시값(Primitive Type)으로, 선언한 후에 값을 할당하지 않은 변수나 값이 주어지지 않은 인수에 자동으로 할당된다. 이 값은 전역 객체의 속성 중 하나로, 전역 스코프에서의 변수이기도 하다. 

따라서 undefined 변수의 초기 값은 undefined 원시 값이다.

​

아래의 경우에 변수가 undefined를 변환한다.

- 값을 할당하지 않은 변수 

- 메서드와 선언에서 변수가 할당받지 않은 경우

- 함수가 값을 return 하지 않았을 때

​

[ null ]

null은 원시값 (Primitive Type) 중 하나로, 어떤 값이 의도적으로 비어있음을 표현한다.

undefined 는 값이 지정되지 않은 경우를 의미하지만, null 의 경우에는 해당 변수가 어떤 객체도 가리키고 있지 않다는 것을 의미한다.

​

[알아부면 좋은 것]

- typeof undefined는 출력하면 undefined이다.

- typeof null은 출력하면 object 이다. 하지만 이는 여전히 원시 타입(primitive value)로, Javascript에서는 구현버그로 간주한다.

- undefined == null은 true이다.

​

​

​

​
