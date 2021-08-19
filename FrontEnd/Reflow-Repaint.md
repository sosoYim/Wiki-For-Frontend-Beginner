# Repaint - Reflow 란?

우선 Reflow와 Repaint를 알아보기 전에 브라우저의 기본 구조부터 알아볼 필요가 있습니다.

[참고 - 렌더링 엔진](https://github.com/sosoYim/Wiki-For-Frontend-Beginner/blob/main/FrontEnd/Rendering_Engine.md)

### Layout

Layout 단계에서는 Render Tree 노드들이 가지고 있는 스타일과 속성에 따라서 브라우저 화면의 어느 위치에 어느 크기로 출력될지 계산합니다.

### Paint

Layout 단계를 통해 위치, 크기 속성이 pixel 단위로 변환되면, 브라우저에서 Paint Setup 및 Paint 이벤트를 발생시켜 화면의 픽셀로 변환후 브라우저 화면에 UI가 나타납니다.

---

### Reflow

Reflow는 레이아웃의 수치(height, width, 위치 등) 변경시 영향 받은 모든 요소(자신, 자식, 부모, 조상)의 수치를 다시 계산하여, Layout 단계를 다시 수행합니다. 이때 변경하려는 특정 요소 뿐만 아니라 연관된 요소들의 위치와 크기도 다시 계산 하기 떄문에 브라우저의 퍼포먼스를 저하시키게 됩니다.

### Repaint

Repaint는 paint 과정이 다시 수행되는 것입니다.

보통의 경우 Reflow 와 Repaint가 같이 발생하지만 화면의 구조가 변경되지 않고 화면의 변화가 존재하는 경우 Repaint만 발생됩니다.
Ex) color, background-color, opactiy 등이 있습니다.

## 내용 출처 및 이미지 출처

https://d2.naver.com/helloworld/59361 ...1
https://oyg0420.tistory.com/entry/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%9D%98-Reflow-%EC%99%80-Repaint
https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/
