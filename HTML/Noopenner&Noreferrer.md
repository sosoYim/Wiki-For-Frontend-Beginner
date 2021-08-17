# noopenner & noreferrer

**사용 예제**
```html
<a href="[연결할 페이지의 URL]" target="_blank" rel="noopener noreferrer nofollow">
```
## noopenner

- `<a>` 뿐만 아니라 `<area>` 및 `<form>` 요소의 `rel` 속성에 대한 값으로 부여할 수 있습니다. `noopener` 키워드는 브라우저가 열려 있는 창에서 `Window.opener` 속성을 설정하지 않게 합니다(null을 반환함).

- A 페이지에서 `window.open()` 을 통해 B 페이지에 방문했을 때, `Window.opener`를 통해 B 페이지에서 A 페이지를 제어할 수 있습니다. 따라서 원래 페이지에 열려 있던 신뢰할 수 있는 페이지가 새로 열린 페이지로 대체되는 피싱 공격이 발생할 수 있습니다.

- 따라서 현재 페이지가 다른 페이지에 연결되거나 다른 페이지에 의해 만들어지지 않은 경우 null을 반환하게 되는데, `noopener`는 이것을 강제합니다.

- 그러나 여전히 **Referer HTTP header**를 제공은 합니다. **Referer HTTP header** 는 사람들이 어디로부터 유입되어 현재 페이지를 방문중인지 인식할 수 있도록 하는 주소가 포함되어 있습니다. 따라서 해당 데이터들은 로그 분석, 캐싱 최적화 등에 활용될 수 있습니다.

- 추가로 현재 페이지와 링크된 페이지는 같은 프로세스를 통해 실행되는데, 링크된 페이지가 높은 부하를 유발하는 Script를 사용하고 있다면 링크를 건 페이지에도 영향을 미쳐 퍼포먼스 저하가 일어날 수 있습니다. `noopenner`는 이를 방지합니다.

- 정리하면 `noopenner`는 새창이 열릴 때 기존 페이지를 제어하는 피싱과 퍼포먼스 저하를 방지하지만 이전 페이지에 대한 주소는 여전히 제공하는 속성값입니다.

**참고사항**
- IE 에서 지원되지 않습니다.
- `noopener`를 사용하면 `_top`, `_self` 및 `_parent` 이외의 비어 있지 않은 `target`의 속성값은 `_blank`로 처리되므로 해당 속성값만으로 새 창/탭을 열 것인지 여부를 결정할 수 있습니다.

<hr>

## noreferrer
- `noreferrer` 역시 `<a>` 뿐만 아니라 `<area>` 및 `<form>` 요소의 `rel` 속성에 대한 값으로 부여할 수 있습니다.

- **Referer HTTP header** 또한 조작이 가능하기 때문에 해당 정보를 사용할 때는 보안 이슈를 고려해야 합니다.

- `noreferrer`는 **Referer HTTP header**와 그 외의 참조 정보의 누출을 방지합니다.

- 정리하면 `noopener` 속성값이 여전히 제공하는 **Referer header** 또한 제공하지 못하게 하는 속성값입니다.

**참고사항**
- 역시 IE에서 지원되지 않습니다.
- `noopener` 가 이미 지정되어 있는 것처럼 동작합니다.

<hr>

## 기타 참고할만한 속성값
### nofollow
- 검색엔진이 연결된 링크페이지를 크롤링하지 않을 수 있도록 합니다. 검색의 대상이 아니라고 생각되는 로그인 페이지 등을 연결시 사용을 고려해 볼 수 있습니다. 그러나 항상 보장되는 것은 아닙니다.
- https://www.affde.com/ko/when-to-use-nofollow-on-links.html
- https://www.affde.com/ko/what-is-a-nofollow-link.html

<hr>

## 더 알아보면 좋을 것들
- **Window 객체와 openner**
- **Reffer HTTP header**

<hr>

### 참조링크
- https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Referer
- https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types/noreferrer#specifications
- https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types/noopener