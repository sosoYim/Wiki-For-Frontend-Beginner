# 말줄임표 사용하기 (text-overflow) + 크로스 브라우징

말줄임표를 사용하기 위해서는 반드시 넓이가 있는 block 요소여야 한다. 한 줄짜리 말줄임표 문장을 만들어보자.

## 한 줄 짜리 말줄임표

### 필수 속성 3가지

> overflow: hidden;

> white-space: nowrap;

> text-overflow: ellipsis;

[overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow)는 블록요소의 크기보다 내부 컨텐츠의 요소가 더 클 때, 즉, 내용이 범위를 넘칠 때 어떤식으로 처리해 줄지를 결정하는 속성이다. default값은 visible로, 넘치는 내용을 다 보여준다. 말줄임표 이후 내용을 보여주지 않기 위해 hidden 속성값을 주자.

[white-space](https://developer.mozilla.org/ko/docs/Web/CSS/white-space)는 공백문자(띄어쓰기, 줄바꿈 등)를 처리해주는 속성이다. 기본은 normal 로 연속공백을 하나로 합치고 넘칠 경우 줄바꿈을 한다. 여기선 지정한 width를 넘치는대로 둬야하기 때문에 줄바꿈을 하지 않는 nowrap을 설정한다.

[text-overflow](https://developer.mozilla.org/en-US/docs/Web/CSS/text-overflow)는 숨겨진 overflow요소들이 어떻게 보여줄지 결정하는 속성이다. overflow 속성에 대해 강제적으로 바꿔주지 않기 때문에, 먼저 제시한 두 속성값을 설정해 준 후 사용할 수 있다. default값은 clip이며 이는 글자 수가 넘치는 순간 바로 잘라버리는 속성값이다. 여기서는 말줄임표를 표시해주는 ellipsis를 사용했다.

### 예시

```
<div class="box">동해물과 백두산이 마르고 닳도록 하느님이 보우하사</div>
```

```
.box {
  width: 100px;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
```

## 2줄 이상 말줄임표 만들기

두 줄 이상의 말줄임표
만들기 위한 코드는 ...

### -webkit-line-clamp 이용 - working draft단계

-webkit-line-clamp는 블록 컨테이너의 콘텐츠를 지정한 줄 수 만큼으로 제한하는 것이다. display: -webkit-box로 지정해줘야 한다.

```html
<p>
  동해물과 백두산이 마르고 닳도록 하느님이 보우하사 우리 나라 만세 무궁화 삼천리
  화려강산 대한사람 대한으로 기리 보전하세
</p>
```

```css
width: 300px;
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3;
overflow: hidden;
```

### Cross browsing issue

웹킷을 이용하기 때문에 크롬과 사파리에서만 사용 가능하다. 핵심 기능이 특정 엔진만으로 사용할 수 있어 심각한 크로스 브라우징 이슈가있다.
W3C 표준화 제정 단계도 아직 working draft 초안 단계이기 때문에 아직까진 권장할 수 없는 속성이다.

이에 대한 대안으로 플러그인을 많이 쓰는 듯 하다.

> [multi-clamp](https://github.com/jackyr/multi-clamp#readme)
> MIT 라이센스

> [dotdotdot.js](https://dotdotdot.frebsite.nl/)
> 자바스크립트 플러그인. 비상업적 용도로 사용시 무료.

## 같이 보기

- WIKI 내 관련 내용 없음

## 참고 자료

[MDN overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow)

[MDN white-space](https://developer.mozilla.org/ko/docs/Web/CSS/white-space)

[MDN text-overflow](https://developer.mozilla.org/en-US/docs/Web/CSS/text-overflow)

[MDN -webkit-line-clamp]()
