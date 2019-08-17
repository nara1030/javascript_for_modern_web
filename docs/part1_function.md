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
* 호출
* 매개변수
* 리턴

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
		* ㅇ

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
				* 자기 호출 함수(자기 실행 익명 함수)
					* 함수를 생성하자마자 호출
						* 다른 개발자에게 영향을 주지 않기 위한 의도  
					```javascript
					
					```
* 콜백 지옥 → Promise
	* 콜백 함수
	* 추후
		* [링크1](https://librewiki.net/wiki/%EC%BD%9C%EB%B0%B1_%EC%A7%80%EC%98%A5)
		* [링크2](https://medium.com/dream-youngs/callback-%EC%A7%80%EC%98%A5-%EA%B3%BC-%EA%B7%B8-%ED%95%B4%EA%B2%B0-2ab583b7607a)


##### [목차로 이동](#목차)

## 심화


##### [목차로 이동](#목차)

## 참고
* [MDN - 함수 가이드](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%ED%95%A8%EC%88%98)

##### [목차로 이동](#목차)
