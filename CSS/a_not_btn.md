# 링크(a) 와 버튼(button)은 다릅니다.

a는 링크연결, button은 기능 동작을 위한 HTML 요소다.

## 공통점과 차이점

### 공통점은 클릭 가능한 특성 뿐

CSS를 이용해 똑같은 모양으로 만들 수 있어 햇갈릴 수 있다. 하지만 semantic HTML 측면에서 둘은 전혀 다른 기능을 가지고 있다.

### a 태그는 '링크 연결'

`<a href="a_tag">a태그 바로가기</a>` 는 특정 URL, 같은 페이지의 요소, 이메일 주소, 전화번호 등의 **링크로 '연결'**하는 태그다.

또한 href 속성이 있을 경우 웹접근성 측면에서 보조기기가 '링크'라고 인식한다. 따라서 a 태그 안의 문구는 연결된 링크의 내용과 관련된 내용으로 작성해야 한다.

### button 태그는 '기능 동작'

`<button>확인</button>`

버튼은 **클릭 가능한 요소**이며 특정 **반응(기능)을 동작**하게 하는 태그다.

기본적인 button 의 type 속성 값은 submit 이다. 즉, form 안의 양식 내용을 제출하는 것이다. 하지만 form 밖 문서 어디서나 사용할 수 있으며 이 때는 `type='button'` 으로 속성을 바꿔줘야 한다.

웹접근성 측면으로 보면, `role="button"`과 같은 역할을 맡는다. 보조기기는 '버튼'이라고 인식한다.

## 예시

- Q. 회원가입 버튼은 a 태그로 해야할까, button 태그로 해야할까?

- A. HTML 구조 내에서 해당 버튼의 기능을 생각해보면 된다. 다른 회원가입 페이지로 이동하게 하는 기능이라면 a 태그를 사용하는 것이 맞다. 반면에 숨어있던 모달창을 띄우게 한다면 기능을 동작시키는 button이 더 적합할 수 있다.

- 스크린 리더가 읽는 법 :

`<a href='#'>회원가입</a>`   ->  '회원가입 링크'

`<button>회원가입</button>`  ->  '회원가입 버튼'

## 같이 보기

- WIKI 내 관련 내용 없음

## 참고 자료

[MDN <a>](https://developer.mozilla.org/ko/docs/Web/HTML/Element/a)

[MDN <button>: 버튼 요소](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Button)

[ARIA: button role](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles/button_role)
