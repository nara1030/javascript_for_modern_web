기본 문법
=====
[강의](https://www.youtube.com/watch?v=FOli-PU8tTo&list=PLBXuLgInP-5kLy13XLuK8iBWVFDBJygYr&index=3)는 링크를 통해 확인할 수 있다.
- - -
## 목차
1. [요약](#요약)
	* [기본용어](#기본용어)
	* [자료형](#자료형)
		* 종류
		* 변환
		* 연산자
	* [변수](#변수)
2. [참고](#참고)

## 요약

### 기본용어
* 표현식
	* 자바스크립트에서 값을 만들어내는 간단한 코드  
		```javascript
		273
		10 + 20 + 30 * 2
		'RintIanTta'
		```
* 문장
	* 하나 이상의 표현식이 모인 것으로, 문장 끝에는 세미콜론을 찍어 문장의 종결을 알림  
		```javascript
		10 + 20 + 30 * 2;
		var rintiantta = 'Rint' + 'Ian' + 'Tta';
		alert('Hello JavaScript');
		273;
		```
	* 사실 자바스크립트 문장 끝에 세미콜론을 입력하지 안하도 프로그램 실행 시 문제 없지만 관례상 입력함
* 키워드
	* 자바스크립트가 처음 만들어질 때 정해진 특별한 의미가 있는 단어
	* 예  
		`break	else	instanceof	true	case`
* 식별자
	* 자바스크립트에서 이름을 붙일 때 사용하는 단어(ex. 변수명, 함수명)
		* 식별자를 사용하면 안 됨
		* alpha, beta처럼 의미 없는 단어보다 input, output 같은 의미 있는 단어 사용 권장
		* 식별자로 한글이나 한자, 일본어 같은 언어를 모두 사용할 수 있으나 알파벳을 사용하는 것이 개발자 사이의 관례
	* 예  
		```javascript
		alpha
		alpha10
		_alpha
		$alpha
		AlPha
		```
	* 외 관례(식별자의 의미를 더 명확하게 하려고 사용하는 규칙)
		* 생성자 함수의 이름은 항상 대문자로 시작
		* 변수와 인스턴스, 함수, 메서드의 이름은 항상 소문자로 시작
		* 여러 단어로 이루어진 식별자는 각 단어의 첫 글자를 대문자로 작성
	* 구분
		* **alert**('Hello World');			→ 함수
		* Array.**length**					→ 속성
		* **input**							→ 변수
		* **prompt('Message', 'Defstr');	→ 함수
		* Math.**PI**						→ 속성
		* Math.**abs**(-273)				→ 메서드
* 주석
	* 프로그램 코드를 설명하는 데 사용
	* 프로그램을 진행하는 데 전혀 영향을 주지 않음
	* HTML 주석  
		```html
		<!DOCYTPE html>
		<html>
		<head>
			<!-- 주석입니다. -->
			<script>
			</script>
		</head>
		<body>
			<!-- <h1>주석입니다.</h1> -->
		</body>
		</html>
		```
	* 자바스크립트 주석  
		```javascript
		<script>
			// 주석은 코드 실행에 아무 영향을 미치지 않습니다.
			/*
			alert('Hello JavaScript');
			alert('Hello JavaScript');
			alert('Hello JavaScript');
			*/
		</script>
		```
##### [목차로 이동](#목차)
		
### 자료형


##### [목차로 이동](#목차)

## 참고


##### [목차로 이동](#목차)