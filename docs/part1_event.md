이벤트
=====
## 목차
1. [용어](#용어)
2. [고전 이벤트 모델](#고전-이벤트-모델)
3. [인라인 이벤트 모델](#인라인-이벤트-모델)
4. [디폴트 이벤트 제거](#디폴트-이벤트-제거)
5. [이벤트 전달](#이벤트-전달)
6. [참고](#참고)

## 용어
```javascript
<script>
    window.onload = function() {
        // 변수 선언
        var header = document.getElementById('header');

        // 이벤트 연결
        function whenClick() {
            alert('CLICK');
        }
        header.onclick = whenClick;
    };
</script>
```

* 이벤트 이름/타입
	* load
	* click
* 이벤트 속성
	* onload
	* onclick
* 이벤트 리스너/핸들러
	* funcion()
	* whenClick()

이처럼 문서 객체에 이벤트를 연결하는 방법을 **이벤트 모델**이라 한다. DOM Level에 따라 총 네 가지 방법으로 이벤트를 연결할 수 있다.

* DOM Level 0
	* 인라인 이벤트 모델
	* 기본(고전) 이벤트 모델
* DOM Level 2
	* 마이크로소프트 인터넷 익스플로러 이벤트 모델
	* 표준 이벤트 모델

##### [목차로 이동](#목차)

## 고전 이벤트 모델
* 고전 이벤트 모델을 사용한 이벤트 연결  
	```javascript
	<script>
	    window.onload = function() {
			// 변수 선언
			var header = document.getElementById('header');

			// 이벤트 연결
			header.onclick = function() {
				alert('CLICK');
			};
		};
	</script>
	```
* 고전 이벤트 모델을 사용한 이벤트 제거  
	```javascript
	<script>
	    window.onload = function() {
			// 변수 선언
			var header = document.getElementById('header');

			// 이벤트 연결
			header.onclick = function() {
				alert('CLICK');

				// 이벤트 제거
				header.onclick = null;
			};
		};
	</script>
	```

고전 이벤트 모델은 이벤트 하나에 이벤트 리스너 하나만 연결할 수 있다.

##### [목차로 이동](#목차)

## 인라인 이벤트 모델
```html
<!DOCTYPE html>
<html>
<head>
	<script>
		function whenClick(e) {
			alert('클릭');
		}
	</script>
</head>
<body>
	<h1 onclick = "whenClick(event)"></h1>
</body>
</html>
```

##### [목차로 이동](#목차)

## 디폴트 이벤트 제거
일부 HTML 태그는 이미 이벤트 리스너가 있다. 예를 들어 a 태그는 클릭하면 다른 페이지로 이동하는데, 이것이 a 태그가 가진 디폴트 이벤트이다. 그렇다면 디폴트 이벤트를 왜 제거하는가?

```javascript

```

##### [목차로 이동](#목차)

## 이벤트 전달
이벤트 전달이란 어떤 이벤트가 먼저 발생하고 어떤 순서로 전파될지 정하는 것을 말한다. 즉, 이벤트가 발생했을 때, 브라우저가 이벤트 리스너를 실행시킬 대상 요소를 결정하는 과정을 의미한다. 만약 이벤트의 대상이 단일 객체라면 이벤트 전파는 일어나지 않는다. 이벤트 전파 방식은 두 가지로 구분된다.

* 이벤트 버블링
* 이벤트 캡쳐

- - -
* [이벤트 전달](https://codedragon.tistory.com/5738)
* [이벤트 버블링, 이벤트 캡쳐, 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)

##### [목차로 이동](#목차)

## 참고


##### [목차로 이동](#목차)
