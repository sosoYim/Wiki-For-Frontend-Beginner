# Repaint - Reflow 란?

우선 Reflow와 Repaint를 알아보기 전에 브라우저의 기본 구조부터 알아볼 필요가 있습니다.

## 브라우저 기본 구조
![helloworld-59361-1](https://user-images.githubusercontent.com/69140464/129714248-e0744a0c-e1bd-49a0-a7e2-533483299c1c.png)

브라우저 엔진 - 사용자 인터페이스와 렌더링 엔진 사이의 동작제어

렌더링 엔진 - 요청 받은 내용을 브라우저 화면에 표시 즉 html을 요청하면 css를 파싱하여 화면에 표시 

각각의 추가적인 내용은 아래 출처 1을 봐주시면 됩니다.

----

## 렌더링 엔진

![render](https://user-images.githubusercontent.com/69140464/129716343-9d926069-f866-41c0-81cb-59f8fb72ad26.png)

HTML 파싱 => DOM Tree , CSS 파싱 => CSSOM Tree 

### Layout
Layout 단계에서는 Render Tree 노드들이 가지고 있는 스타일과 속성에 따라서 브라우저 화면의 어느 위치에 어느 크기로 출력될지 계산합니다.

### Paint
Layout 단계를 통해 위치, 크기 속성이 pixel 단위로 변환되면, 브라우저에서 Paint Setup 및 Paint 이벤트를 발생시켜 화면의 픽셀로 변환후 브라우저 화면에 UI가 나타납니다.

----

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