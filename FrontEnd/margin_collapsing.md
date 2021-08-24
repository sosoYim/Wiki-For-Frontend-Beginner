# margin collapsing

- 두 개 이상의 블록 요소들의 상하 margin이 겹칠 때, 어느 한 쪽의 값만 적용되는(상쇄되는) 것을 말합니다.

- 그럼 구체적인 발생 상황을 알아보겠습니다.

## 발생 상황

### 인접 형제 요소

- 인접 형제 요소의 상하 margin이 겹칠 때, 두 margin의 값 중 큰 값으로 상쇄되어(작은 값이 아닌) 적용됩니다. 두 값이 동일할 경우 하나의 margin 값만 적용됩니다.

  <figure style = "display: block; text-align: center;">
    <img src = "https://media.vlpt.us/post-images/raram2/97e16a40-121f-11ea-aaba-65695302c179/01-margin-collapsing-sibling-case.png" alt="인접요소 상하 마진 상쇄">
    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [raram2님 blog](https://velog.io/@raram2/CSS-%EB%A7%88%EC%A7%84-%EC%83%81%EC%87%84Margin-collapsing-%EC%9B%90%EB%A6%AC-%EC%99%84%EB%B2%BD-%EC%9D%B4%ED%95%B4)>
    </figcaption>
  </figure>

- **예외** : 뒤에 오는 형제 요소가 floating 해제를 위한 요소라면 margin collapsing이 일어나지 않습니다. 반대로 말하면 float된 요소는 margin collapsing이 일어나지 않는다는 말과 같습니다.

- 아래 그림처럼 인접 요소 사이에 다른 요소가 있다면 margin collapsing은 발생하지 않습니다.

  <figure style = "display: block; text-align: center;">
    <img src = "https://raw.githubusercontent.com/freshhoe/freshhoe.github.io/develop/contents/HTML_CSS/0817/images/margin_3.PNG" alt="마진 상쇄가 발생하지 않는 경우">
    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)>
    </figcaption>
  </figure>

- 그렇다면 부모요소에 감싸진 자식요소는 어떨까요?

  <figure style = "display: block; text-align: center;">
    <img src = "https://raw.githubusercontent.com/freshhoe/freshhoe.github.io/develop/contents/HTML_CSS/0817/images/margin_4.PNG" alt="부모에게 감싸진 요소와의 마진 상쇄">
    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)>
    </figcaption>
  </figure>
- 부모요소에 감싸진다고 해서 margin collapsing을 방지할 수 있는건 아닙니다. 왜 그럴까요?

### 부모와 자식을 분리하는 컨텐츠의 유무
- 부모와 자식 요소를 분리하는 속성 또는 컨텐트로는 border, padding, inline이 있습니다. 부모 요소에 높이가 지정되어 있지 않고, 부모와 자식 요소 사이에 이러한 속성과 컨텐트가 없어 분리되어 있지 않다면 자식의 margin이 부모에게 이전되기 때문입니다.

- 비슷한 맥락으로 부모와 자식 요소끼리 발생하는 margin collapsing도 두 요소를 분리하는 컨텐츠가 없다면 부모 요소의 상단과 자식 요소의 상단, 또는 부모 요소의 하단과 자식 요소의 하단에서 margin collapsing이 발생합니다. 

- 아래 그림처럼 부모 요소에(또는 부모 요소와 자식 요소 사이에) border, padding 속성의 값이나 inline 컨텐츠가 없을 경우 margin collapsing이 발생하고, 상쇄된 margin은 부모 요소의 바깥으로 렌더링됩니다.

  <figure style = "display: block; text-align: center;">
    <img src = "https://raw.githubusercontent.com/freshhoe/freshhoe.github.io/develop/contents/HTML_CSS/0817/images/margin_2.PNG" alt="부모와 자식 요소의 마진 상쇄">

    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)>
    </figcaption>
  </figure>

- 아래 그림처럼 부모 요소에 padding이 존재한다면 margin collapsing은 발생하지 않습니다.

  <figure style = "display: block; text-align: center;">
    <img src = "https://raw.githubusercontent.com/freshhoe/freshhoe.github.io/develop/contents/HTML_CSS/0817/images/margin_1.PNG" alt="부모의 padding으로 인해 마진 상쇄가 발생하지 않는 경우">

    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)>
    </figcaption>
  </figure>

### 빈 블록 요소
- `height`, `min-height`, `max-height`, `padding`, `border` 등과 같이 요소에 높이를 만드는 속성 값을 명시적으로 부여하지 않거나, 내부에 inline 콘텐츠가 없어 높이가 0인 경우 **빈 블록** 상태가 됩니다. 
- 상하 경계가 없기 때문에 자기 자신의 위쪽 margin과 아래쪽 margin 값 중 더 큰 값의 margin만 상쇄되어 적용됩니다. 두 값이 동일할 경우 하나의 margin 값만 적용됩니다.
- 따라서 아래 그림과 같이 인접 블록 요소들 사이에 빈 요소가 존재하면 여러 번의 margin collapsing이 발생합니다.

  <figure style = "display: block; text-align: center;">
    <img src = "https://media.vlpt.us/post-images/raram2/ffac75c0-121f-11ea-aaba-65695302c179/02-margin-collapsing-emptybox-case.png" alt="빈 블록 요소의 마진 상쇄">

    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [raram2님 blog](https://velog.io/@raram2/CSS-%EB%A7%88%EC%A7%84-%EC%83%81%EC%87%84Margin-collapsing-%EC%9B%90%EB%A6%AC-%EC%99%84%EB%B2%BD-%EC%9D%B4%ED%95%B4)>
    </figcaption>
  </figure>

- 첫 번째 그림에서 빈 요소의 margin-top(60)과 margin-bottom(30)의 값 중에서 margin-top 의 값이 크기 때문에 margin-bottom의 값은 상쇄됩니다.
- 두 번 째 그림에서 빈 요소 상단 인접 요소의 margin-bottom(30)과 빈 요소의 margin(60) 값 중에서 빈 요소의 margin 값이 크기 때문에 상단 인접 요소의 margin-bottom 값이 상쇄됩니다.
- 마지막 그림에서 빈 요소 하단 인접 요소의 margin-top(30)과 빈 요소의 margin(60) 값 중에서 빈 요소의 margin 값이 크기 때문에 하단 인접 요소의 margin-top 값이 상쇄됩니다.


### 음수 마진 상쇄
- negative margin 도 positive margin 과 비슷합니다.
- 두 인접 요소 상단과 하단에 각각 negative margin이 존재한다면 더 작은 값으로 상쇄되어 적용됩니다. 따라서 더 작은 margin을 가진 요소의 margin 크기만큼 겹치게 됩니다.

  <figure style = "display: block; text-align: center;">
    <img src = "./images/margin_7.PNG" alt="음수 마진의 상쇄">

    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)>
    </figcaption>
  </figure>

- 아래 그림의 상단 블록 요소는 negative margin-bottom을 가지고 있고, 하단 블록요소는 positive margin-top을 가지고 있습니다. 이 경우에도 예외없이 margin collapsing이 발생하게 됩니다.

  <figure style = "display: block; text-align: center;">
    <img src = "https://raw.githubusercontent.com/freshhoe/freshhoe.github.io/develop/contents/HTML_CSS/0817/images/margin_5.PNG" alt="음수와 양수 마진의 상쇄">

    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)>
    </figcaption>
  </figure>

- 이런 경우 결국 두 블록 요소의 상단과 하단에 margin이 없는 경우와 같습니다.

  <figure style = "display: block; text-align: center;">
    <img src = "https://raw.githubusercontent.com/freshhoe/freshhoe.github.io/develop/contents/HTML_CSS/0817/images/margin_6.PNG" alt="마진이 없는 경우">

    <figcaption style = "text-align: center; font-size: 12px; color: #808080">

    <출처 : [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)>
    </figcaption>
  </figure>

### 예외사항
- 위의 세 가지 상황에 해당하더라도 아래와 같은 속성이 적용된 요소는 margin collapsing이 발생하지 않습니다.

  - `position: absolute` 가 적용된 요소
  - `float` 이 적용된 요소
  - `display: flex` 가 적용된 요소의 내부 item들
  - `display: grid` 가 적용된 요소의 내부 item들

- 즉, margin collapsing은 normal flow에서만 발생합니다.


### 정리
- margin collapsing은 블록 요소가 쌓이는 방향의 상단 또는 하단에서만 발생한다.
- 다시 말해, 아래와 같이 `writing-mode: vertical-lr`로 요소가 쌓이는 흐름이 바뀔 경우에도 margin collapse가 가능합니다. 이 때, 요소는 쌓이는 방향이 수평이므로 수평 margin collapse가 발생하고, 수직 margin collapse는 발생하지 않습니다.
- **참고** : `writing-mode` 를 활용해 block 요소를 수직(vertically)이 아닌 수평(horizontally)으로 쌓을 수 있습니다.

  ```html
  <!-- html -->
  <p>p1</p>
  <p>p2</p>
  ```

  ```css
  /* css */
  html {
    writing-mode: vertical-lr;
  }
  p {
    display: block;
    margin-block-start: 20px;
    margin-block-end: 20px;
  }
  ``` 
- 인접 요소간에 발생하며, 부모 요소에 감싸지더라도 부모와 자식 요소를 구분짓는 속성이나 컨텐츠가 없다면 자식의 margin이 부모의 margin에 영향을 미친다.
- 빈 요소의 경우 자기 자신의 margin-top, margin-bottom 중 큰 값으로 상쇄된다.
- 음수 margin도 양수 margin과 비슷한 원리가 적용된다.

<hr>

## 더 알아보면 좋을 것들
- [Block Format Context(블록 서식 맥락)](https://developer.mozilla.org/ko/docs/Web/Guide/CSS/Block_formatting_context)
- [Negative Margin(음수 마진) : 관련 내용 Wiki 정리글](https://github.com/sosoYim/Wiki-For-Frontend-Beginner/blob/main/CSS/negative-margin.md)

<hr>

## 참조링크
이미지 및 정보 출처
- [MDN 마진 상쇄](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)
- [joshwcomeau blog](https://www.joshwcomeau.com/css/rules-of-margin-collapse/)
- [raram2님 blog](https://velog.io/@raram2/CSS-%EB%A7%88%EC%A7%84-%EC%83%81%EC%87%84Margin-collapsing-%EC%9B%90%EB%A6%AC-%EC%99%84%EB%B2%BD-%EC%9D%B4%ED%95%B4)
