함수
=====
[강의](https://www.youtube.com/watch?v=FOli-PU8tTo&list=PLBXuLgInP-5kLy13XLuK8iBWVFDBJygYr&index=3)는 링크를 통해 확인할 수 있다.
- - -
## 목차
1. [개요](#개요)
	* [함수란](#함수란)
	* [용어](#용어)
	* [종류](#종류)
	* [이슈](#이슈)
2. [심화](#심화)
3. [참고](#참고)

## 개요

### 함수란
* 함수란
	* 코드의 집합(괄호 내부에 코드를 넣기 때문)
* 사용 이유
	* 코드를 묶고 이름을 붙여 재사용하기 위해
		* 현대 프로그래밍 언어들은 `코드를 좀 더 쉽게 작성하기 위해, 좀 더 깔끔하게 만들기 위해` 다양한 개념을 도입
	* 조건문, 반복문만 사용한 코드에 비해 가독성 향상
		* 따라서 유지보수성도 좋아짐
		* 주석 굳이 필요 없음
		* break, continue 키워드 사용 빈도 감소

##### [목차로 이동](#목차)

### 용어
기본적인 의미를 넘어, 자바스크립트 한정해서 개념을 기록한다.

* 함수 호출(≠ 함수 선언)
	* 함수는 호출될 때 범위 내에 있어야 함
		* 그러나 함수의 선언은 아래 예에서와 같이 `호이스팅`될 수 있음(호출 아래에 선언문 존재)  
			```javascript
			console.log(square(5));
			/* ... */
			function square(n) {
				return n * n;
			}
			```
			* 함수의 범위는 함수가 선언된 곳이거나, 전체 프로그램에서의 최상위 레벨(전역)에 선언된 곳임
		* 하지만 `함수 호이스팅`은 함수 선언과 함께 작동하고 함수 표현식에서는 동작 않음  
			```javascript
			console.log(square);		// square는 초기값으로 undefined를 가지고 호이스트된다.
			console.log(square(5));	// TypeError: square는 함수가 아니다.
			square = function(n) {
				return n * n;
			}
			```
	* 함수 호출의 다양한 방법들 존재
		* 동적 호출
		* 가변 인수
		* 함수 호출의 맥락이 런타임에서 결정된 특정한 객체로 설정될 필요가 있는 경우
			* 함수가 그 자체로 객체이고 이들 객체는 차례로 메서드([`Function`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function) 객체를 참조)를 갖고 있음
			* [`apply()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) 메서드
* 매개변수
	* 기본 자료형인 경우
		* 예를 들어 `number`와 같은 경우 **값으로** 함수에 전달
		* 그리고 함수가 매개변수의 값을 바꾸더라도 이는 **전역적으로** 또는 **함수를 호출하는 곳**에는 반영되지 않음  
			```javascript
			function square(number) {
				return number * number;
			}
			```
	* 기본 자료형이 아닌 경우
		* 예를 들어 `Array`나 `사용자가 정의한 객체`와 같은 것을 전달
		* 함수가 객체의 속성을 변하게 하는 경우에, 다음의 예처럼 그 변화는 **함수 외부**에서 볼 수 있음  
			```javascript
			function myFunc(theObject) {
				theObject.make = "Toyota";
			}
			
			var mycar = {make: "Honda", model: "Accord", year:1998};
			var x, y;
			
			x = mycar.make;		// x의 값은 "Honda" 입니다.
			
			myFunc(mycar);
			y = mycar.make;		// y의 값은 "Toyota" 입니다(make 속성은 myFunc에서 변경됨).
			```
* 함수의 범위
	* 함수가 정의된 범위 내에서 정의된 모든 변수나 함수는 액세스 가능
		* 즉, 전역 함수는 모든 전역 변수를 액세스 가능
		* 다른 함수 내에 정의된 함수는 부모 함수와 부모 함수가 액세스할 수 있는 다른 변수에 정의된 모든 변수 액세스 가능
	* 함수 내에서 정의된 변수는 변수가 함수의 범위에서만 정의되어 있기 때문에, 함수 외부에서 액세스 가능  
	```javascript
	// The following variables are defined in the global scope
	var num1 = 20,
		num2 = 3,
		name = "Chamahk";
	
	// This function is defined in the global scope
	function multiply() {
		return num1 * num2;
	}
	
	multiply();		// Return 60
	
	// A nested function example
	function getScore() {
		var num1 = 2,
		 num2 = 3;
		
		function add() {
			return name + " scored " + (num1 + num2);
		}
		
		return add();
	}
	
	getScore();		// Return "Chamahk scored 5"
	```

##### [목차로 이동](#목차)

### 종류
* 두 가지로 구분
	* 익명 함수  
		```javascript
		var 함수 = function() { };
		```
		* 함수지만 이름이 없으므로 `익명 함수`라 부름
		* 이름이 없기 때문에 변수에 넣어 사용해야 함
	* 선언적 함수  
		```javascript
		function 함수() {
		
		}
		```
		* 이름이 있는 함수를 `선언적 함수`라 부름
* 차이점
	* 실행 순서: 웹 브라우저는 script 태그 내부의 내용을 한 줄씩 읽기 전에 선언적 함수부터 읽음
		* 익명 함수의 재정의 - 오류 발생  
			```javascript
			<script>
				함수();
				var 함수 = function() { alert('함수A'); };
				var 함수 = function() { alert('함수B'); };
			</script>
			```
		* 선언적 함수의 재정의 - 실행  
			```javascript
			<script>
				함수();
				function 함수() { alert('함수 A'); }
				function 함수() { alert('함수 B'); }
			</script>
			```
		* 선언적 함수와 익명 함수의 실행 순서  
			```javascript
			<script>
				// 함수를 생성합니다.
				var 함수 = function() { alert('함수 A'); }
				function 함수() { alert('함수 B'); }
				
				// 함수를 호출합니다.
				함수();
			</script>
			```
			* 실행 결과는 함수 A가 출력됨
	* 사용
		* 익명 함수는 함수를 다른 함수의 매개변수로 전달할 때 편리  
			```javascript
			// 익명 함수(함수 표현식)로 정의된 함수를 인자로 받아,
			// 2번째 인자인 배열의 모든 요소에 대해 함수 실행
			function map(f, a) {
				var result = [];	// Create a new Array
				var i;			// Declare variable
				for(i = 0; i != a.length; i++) {
					result[i] = f(a[i]);
				}
				return result;
			}
			
			var f = function(x) {		// 익명 함수
				return x * x * x;
			}
			
			var numbers = [0, 1, 2, 5, 10];
			var cube = map(f, numbers);
			console.log(cube);		// 결과: [0, 1, 8, 125, 1000]
			```
		* 추가적으로, JavaScript에서 함수는 조건에 의해 정의될 수 있는데 두 가지 방법으로 정의 가능
			* 익명 함수 사용  
				```javascript
				// 다음 함수는 오직 num이 0일 경우에만 myFunc을 정의
				var myFunc;
				if(num == 0) {
					myFunc = function(theObject) {
						theObject.make = "Toyota";
					}
				}
				```
			* 생성자 사용
				* [`eval()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/eval)과 같이 런타임에 문자열에서 함수들을 만들기 위해 [`Function`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function) 생성자를 사용할 수 있음
				* 객체 내의 한 속성이 함수인 경우 [메서드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Working_with_Objects)라 부름

* 참고
	* 웹 브라우저 내장 함수들의 소스코드는 볼 수 없게 막아놓음  
		```javascript
		<script>
			alert(alert);
			alert(prompt);
		</script>
		```
	* 함수: 매개변수와 리턴값
		* 예: [prompt() 함수](https://developer.mozilla.org/ko/docs/Web/API/Window/prompt)  
			```javascript
			// 사용자가 입력한 문자열 메시지를 문자열 자료형 값(또는 null)으로 변환
			String prompt([String message], [String default])
			```
		* 매개변수: 함수를 호출하는 쪽과 함수를 연결하는 매개가 되는 변수
			* 정의(선언)된 매개변수의 수와 다르게 사용하는 경우
				* 선언할 수 있는 매개변수보다 많은 수를 선언: 추가된 매개변수는 무시
				* 선언할 수 있는 매개변수 숫자보다 적게 선언: 지정하지 않는 매개변수는 undefined로 입력
			* 가변 인자 함수(매개변수가 동적인 함수; ex. `Array()`)
				* `arguments` 사용
					* 변수 arguments는 매개변수의 배열(객체)
					* 자바스크립트의 모든 함수는 내부에 기본적으로 변수 arguments 존재
				* 가변 매개변수 함수 생성 예  
					```javascript
					<script>
						function 이렇게함수() {
							// 매개변수의 개수를 가져옵니다.
							var length = arguments.length;
							
							// 조건을 나누어줍니다.
							if(length == 0) {
								// 매개변수가 없을 때
							} else if() {
								// 매개변수가 한 개일 때
							} else {
								// 매개변수가 두 개일 때
							}
						}
					</script>
					```
		* 리턴값
			* return 키워드
				* 원래 return 키워드는 함수가 실행되는 도중에 함수를 호출한 곳으로 돌아가라는 의미
				* 따라서 return 키워드를 사용하면 값을 지정하지 않아도 함수를 호출한 곳으로 돌아감

##### [목차로 이동](#목차)

### 이슈
* 협업 관련 이슈 → 내부 함수
	* 설명
		* 프로그램의 규모가 커질수록 여러 충돌 발생
		* 내부 함수는 이러한 충돌을 막는 방법 중 하나
	* 코드
		* 충돌 코드  
			```javascript
			<script>
				/* 윤 씨가 만든 함수 */
				// 제곱을 구하는 함수
				function square(x) {
					return x * x;
				}
				
				// 피타고라스 함수
				function pythagoras(width, height) {
					return Math.sqrt(square(width) + square(height));
				}
				
				// 피타고라스 함수를 호출합니다.
				alert(pythagoras(3, 4));
				
				/* 연 씨가 만든 함수 */
				// 삼각형이 직각인지 확인하는 함수
				function square(width, height, hypotenuse) {
					if(width * width + height * height == hypotenuse * hypotenuse) {
						return true;
					} else {
						return false;
					}
				}
			</script>
			```
			* 윤 씨의 square() 함수는 연 씨의 square() 함수에 덮어씌어짐
			* 따라서 pythagoras() 함수 내부에서는 연 씨의 square() 함수를 사용하게 됨
		* 해결 코드(내부 함수)  
			```javascript
			<script>
				// 피타고라스 함수
				function pythagoras(width, height) {
					function square(x) {
						return x * x;
					}
				
					return Math.sqrt(square(width) + square(height));
				}
			</script>
			```
			* 내부 함수는 내부 함수를 포함하는 함수에서만 사용 가능
			* 따라서 pythagoras() 함수 외부에서는 square() 함수 사용 불가
			* 추가
				* jQuery는 선언적 함수 대부분을 내부 함수로 작성!
				* 자기 호출 함수([자기 실행 익명 함수](https://fedev.tistory.com/26))
					* 개념
						* 함수를 생성하자마자 호출
						* 즉, 함수명을 지정하거나 함수를 변수에 저장하지도 않고 함수를 바로 실행
					* 필요성
						* 변수 스코프를 제어하는데 사용하며, 변수가 코드 외부로 노출되지 않게 해줌
							* 이런 이유로 자바스크립트 플러그인 개발에 유용하게 활용
						* 다른 개발자에게 영향을 주지 않기 위한 의도  
							```javascript
							(function() {
								var private_var = "private";
							})();
							
							// 변수 private_var가 선언되지 않았다는 에러가 출력된다.
							console.log(private_var);
							```
					* 활용
						* 변수 덮어쓰기를 차단해야 하는 사례로 다음 코드처럼 `$` 파라미터를 사용하는 자기 실행 익명 함수로 jQuery 변수를 전달하면 함수 내에서 `$`가 프로토타입 라이브러리에 의해 바뀌는 것을 방지 가능  
							```javascript
							(function($) {
								console.log($);
							})(jQuery);
							```
* 콜백 지옥 → Promise
	* 콜백 함수
	* 추후
		* [링크1](https://librewiki.net/wiki/%EC%BD%9C%EB%B0%B1_%EC%A7%80%EC%98%A5)
		* [링크2](https://medium.com/dream-youngs/callback-%EC%A7%80%EC%98%A5-%EA%B3%BC-%EA%B7%B8-%ED%95%B4%EA%B2%B0-2ab583b7607a)


##### [목차로 이동](#목차)

## 심화
* 범위와 함수 스택
	* 재귀
	* 중첩된 함수와 클로저
		* 변수의 보존
		* 다중 중첩 함수
		* 이름 충돌

##### [목차로 이동](#목차)

## 참고
* [MDN - 함수 가이드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%ED%95%A8%EC%88%98)

##### [목차로 이동](#목차)
