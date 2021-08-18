# CSS Sprite

## 1. CSS Sprite (이미지 스프라이트) 기법이란?
- 아이콘, 버튼 같은 자주 쓰는 이미지들을 한 이미지 파일로 통합해 배경이미지로 만들어 놓고 position 값으로 각각의 이미지를 불러오는 것
- 장점
  1. 이미지의 로딩 시간이 짧음 -> 페이지의 로딩 속도를 줄일 수 있음
  1. 이미지를 한 번에 모두 불러오기 때문에 깜박임 현상을 없앨 수 있음
  1. 이미지를 요청하는 http 통신 횟수를 줄여 서버의 부하를 줄일 수 있음
- 단점
  1. 개별 이미지의 위치를 정확히 확인해야 함
  
  
## 2. CSS Sprites Generator를 통한 이미지 스프라이트 구현
  - [CSS Sprites Generator](https://www.toptal.com/developers/css/sprite-generator/)
  1. CSS Sprites Generator
  ![홈페이지 개요](./css_sprite_img/01.png)
  ![이미지 포지션](./css_sprite_img/02.png)
  - 이미지를 끌어다 놓으면 CSS에 적용하여야 할 좌표(position)값을 자동으로 생성해줌
  2. 생성된 SPRITE 이미지
  <img src="./css_sprite_img/css_sprites_td.png" width="30%" alt="Sprite Images" style="display:block;">
  <div>아이콘 제작자(출처) <a href="https://www.freepik.com" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/kr/"
      title="Flaticon">www.flaticon.com</a></div>

## 3. 코드
```html
  <div class="container">
    <div class="item item1"></div>
    <div class="item item2"></div>
    <div class="item item3"></div>
    <div class="item item4"></div>
  </div>
  <div>아이콘 제작자 <a href="https://www.freepik.com" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/kr/"
      title="Flaticon">www.flaticon.com</a></div>
```
```css
.container {
  display: flex;
}

.item {
  width: 512px;
  height: 512px;
  background-color: #fff;
}

.item1 {
  background: url(./images/css_sprites_td.png) -10px -10px;
}

.item2 {
  background: url(./images/css_sprites_td.png) -10px -542px;
}

.item3 {
  background: url(./images/css_sprites_td.png) -10px -1074px;
}

.item4 {
  background: url(./images/css_sprites_td.png) -10px -1606px;
}
```
- CSS Sprites Generator가 생성하는 좌표값 그대로 투입하면 됨

## 4. 출력화면
  ![출력화면](./css_sprite_img/03.png)