개요
=====
책보다는 강의를 통해서 훑었다.  
[강의](https://www.youtube.com/watch?v=4hCiz6aU-7Q&list=PLBXuLgInP-5kLy13XLuK8iBWVFDBJygYr&index=2)는 링크를 통해 확인할 수 있다.
- - -
## 목차
1. [요약](#요약)
2. [참고](#참고)

## 요약

가장 초반부기에 강의에선 자바스크립트의 역사, 개념 등 추상적 개념보다는 아래 세 가지를 언급했다.  

* 개발환경 구축
	* [Visual Studio 2015 Express for Web 설치](https://visualstudio.microsoft.com/ko/vs/express/)
* HTML 파일 생성
	* `파일 → 브라우저 보기` 혹은 `Ctrl + Shift + W`로 브라우저에서 실행 가능
* 오류 확인 방법
	* 개발자 도구(콘솔) 활용
		* 크롬의 경우 `F12` 혹은 `Ctrl + Shift + I` 사용
	* 경고 화면 사용
		* 인터넷 익스플로러(IE)의 경우 `스크립트 디버깅 사용 안 함` 체크 해제
			* `설정 → 인터넷 옵션 → 스크립트 디버깅 사용 안 함(Internet Explorer)` 체크 해제
		* 단, 이 방법은 일반 웹 사이트 접속 어려울 수 있으므로 개발자 도구 활용을 권장

책에 언급되어 있는 부분 중 알아야 할 부분을 추가한다.  

* 자바스크립트의 표준 명칭은 ECMAScript임
	* 자바스크립트가 많은 곳에서 사용되자 유럽 컴퓨터 제조 협회가 표준화
	* 다만 자바스크립트라는 용어를 더 오래 사용해왔으므로 많이 쓰이는 것 뿐
* 자바스크립트를 사용하는 분야에 따라 사용할 수 있는 버전(2016.06 - ECMAScript 7)이 달라짐
	* 최신 브라우저들은 ECMAScript7까지의 기능 대부분 지원(하지만 인터넷 익스플로러의 점유율이 높음)
		* 최신 브라우저는 마이크로소프트의 엣지, 구글의 크롬, 모질라의 파이어폭스, 애플의 사파리 등
	* ECMAScript 6과 7에서 추가된 기능은 대부분 `기존의 어려운 문법을 쉽게 사용할 수 있게 간략화하는 것`임
		* 따라서 ECMAScript 5를 통해 문법 구조와 기능을 확실히 익히는 것이 중요
		
##### [목차로 이동](#목차)

## 참고
* [JavaScript - 나무위키](https://namu.wiki/w/JavaScript)
	* [좀 더 자세히](#좀-더-자세히)
* [비동기를 사랑하는 오픈소스 개발자, 이희승](https://engineering.linecorp.com/ko/blog/line-developer-interview-3/)
	* [공개SW 컨트리뷰톤](https://www.oss.kr/contributhon_overview?fbclid=IwAR0kr5SQNteicPva3I0V5747ya21iUMvVqeLAJAf-XCvhWfJCVoMLrAREhc)

### 좀 더 자세히
나무 위키의 내용 중 중요하다고 생각하는 부분을 발췌한다.

* 자바스크립트란
	* 프로그래밍 언어로, 스크립트 언어([Script Language](https://namu.wiki/w/%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20%EC%96%B8%EC%96%B4))에 속함
		* 스크립트 언어는 소스코드를 한줄 한줄 읽어 바로 실행하는 인터프리터 방식에 사용하기 위해 발명(cf. 컴파일 방식)
			* 수정이 빈번하게 일어나 컴파일 타임을 많이 잡아먹는 부문에 사용
		* 기존 자바스크립트 엔진들은 이처럼 실시간 인터프리팅을 했지만 최근 JIT 컴파일 방식 도입
	* 특수한 목적이 아닌 이상 모든 웹 브라우저에 인터프리터가 내장되어 있음
		* ~~흔히 하는 오해인데~~ JVM을 이용해 돌리는 Java와, 브라우저 내에 스크립트 엔진(인터프리터)이 존재하는 JavaScript는 완전히 다름
		* 웹 브라우저의 각 벤더 사에서 필수적으로 구현할만큼 성장
* 자바스크립트는 ~~변태적인~~ 특이한 언어로
	* 짧은 동작들의 경우 절차적 프로그래밍을 해 잘 돌아가는 것처럼 보이지만 긴 코드의 경우 골치 아픔
		* JS는 동적 타이핑, 약타입 언어로 쉽다고도 이야기 되지만, 깊이 들어가보면 그렇지 않음
	* [비동기 프로그램 구현 작성 시]()
* 오늘날 자바스크립트가 가장 널리 쓰이는 분야는
	* 클라이언트용 인터페이스임
	* 이 때 주로 자바스크립트는 웹 브라우저에서 제공되는 DOM API로 사용됨
		
##### [목차로 이동](#목차)
