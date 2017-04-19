# Developer tool by Chrome

크롬 개발자 도구란 무엇인가?

HTML CSS JS 삼총사는 컴파일 과정 없이 브라우저에서 런타임으로 해석되고 동작한다.

크롬 개발자 도구는 브라우저가 대부분의 과정을 투명하게 개발자가 분석 가능한 수준으로 공개하고 있다.

결국 개발자는 문제의 원인을 더 빨리 찾을 수 있다.

크롬 개발자 도구에서는 HTTP 통신과정, HTML 구조, CSS 스타일, Javascript 디버깅, 프로파일링, 성능 진단 등을 할 수 있으며 그 기능이 다양하고 많아지고있다.

크롬 개발자 도구와 같은 것은 브라우저 제조사마다 비슷한 기능으로 제공하고 있다.



### Elements 탭

HTML, CSS를 어떻게 해석하고 화면에 표시했는지 실제 브라우저의 렌더링 결과를 보여준다

결과 뿐만 아니라 HTML 구조나 CSS 속성을 다양한 방법으로 추가/삭제/변경 할 수 있어 빠르게 디버깅을 할 수 있다.

주로 DOM Inspection(검사). CSS Style 변경을 하는 용도로 활용한다.

computed탭으로 최종 렌더링 된 스타일을 확인 할 수 있다.

Event Listeners로 어느 요소에 어느 이벤트가 걸려있는지 확인 할 수 있다.

HTML 속성 변경에 브레이크 포인트를 걸어 디버깅을 하려면 해당 부분 우클릭을 통해 브레이크 온을 걸어준다.



### Console 탭

Javascript를 이용해 간단한 코딩을 하거나 해당 페이지를 조작할 수 있다.

```Js
//console 탭에 관련된 내용은 아니지만 몰랐던 내용...

console.time("a")
for(){...}
console.timeEnd("a") 
//a의 time부터 timeEnd까지의 실행이 걸린 시간을 구할 수 있다.
```



### Source 탭

Javascript 디버깅을 할 수 있는 가장 중요한 기능

Element 탭에서도 브레이킹 포인트를 걸어 소스탭에서 디버깅이 가능하다. (HTML 속성 변경에 브레이크 포인트를 걸어 디버깅을 하려면 해당 부분 우클릭을 통해 브레이크 온을 걸어준다.)

소스코드를 확인할때 uglify가 되어있는 코드라면 `{}` pretty print 버튼을 눌러 보기 좋게 정렬된다.

브레이크 포인트를 걸어 디버깅할때 스코프의 변수들을 확인 할 수 있다. 해당 타이밍에서 지역변수의 값을 확인하는 것이 유용하게 쓰인다.

Watch에서 지속적으로 관찰하고 싶은 변수를 적어 해당 변수의 값 변화를 트래킹할 수 있다.

ESC 누를 시 console 탭이 나온다, 여기서 js를 이용하여 변수 확인을 하거나 조작을 해볼 수 있다.

XHR Breakpoints에서 추가를 하는데 그냥 빈칸으로 추가하게 되면 모든 AJAX 통신에 브레이크 포인트를 걸어 확인해볼 수 있다.

- Javascript 실행 중에 Breakpoints 를 걸어 그 시점의 scope 내 변수를 확인 할 수 있다.
- DOM이 변경되거나 XHR 통신을 하는 시점에 Breakpoints를 걸어 디버깅을 할 수 있다.
- Breakpoints 가 걸리면 watch나 console탭을 통해서 궁금한 값을 확인하고 javascript 표현식을 통해서 디버깅 할 수 있다.



### Network 탭

HTTP 통신과정을 들여다볼 수 있다.

DOMContentLoded 와 같은 이벤트 시간을 확인해 볼 수 있다.

Capture screenshots 를 이용하여 시간에 따른 시각적인 변화가 어떻게 일어나는지 알 수 있다.

---

### Reference

- http://tryhelloworld.co.kr/courses/%ED%8A%B9%EA%B0%95-%ED%81%AC%EB%A1%AC%EC%9D%84-%ED%99%9C%EC%9A%A9%ED%95%9C-%ED%94%84%EB%A1%A0%ED%8A%B8%EC%97%94%EB%93%9C-%EB%94%94%EB%B2%84%EA%B9%85