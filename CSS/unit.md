# relative unit  🆚  absolute unit

## 상대단위란

> 고정되지 않고 어떤 기준에 따라서 유동적으로 바뀔 수 있는 길이를 나타내는 단위.
> 브라우저의 계산 기준에 따라 px로 변환하여 나타낸다.
> 대표적인 상대단위 : em, rem, %, vw, vh 등

## 절대단위란

> 어떤 상황에서든 항상 고정된 길이를 나타내는 단위
> 대표적인 절대단위 : px, pt, cm, in 등


👉 즉, 1px는 무슨 짓을 해도 1px지만 1em은 16px이 될 수도 있고, 32px이 될 수도 있다! 
(저는 여러분들이 어떻게 하느냐에 따라 천사가 될 수도 악마가 될 수도,,,어쩌구,,,저쩌구)


</br>

# 📏 em 
> em 단위가 적용된 엘리먼트의 글자 크기에 비례한 사이즈.

![그룹 52](https://user-images.githubusercontent.com/48905932/129482613-f4ac0510-53a9-43d2-8ace-04fbf33ea893.png)

- div의 font-size가 20px로 설정되어 있기 때문에 width는 40px이 된다.

</br>

![그룹 533](https://user-images.githubusercontent.com/48905932/129482733-21b165ad-0218-4b71-8186-ad05f5c485fb.png)

- div에 font-size가 적용되어 있지 않아, 부모의 값을 상속 받는 경우에는, 상속받은 글자 크기가 먼저 적용되고, 그 후 em에 의해 너비가 계산된다.
- 따라서 15 * 2 = 30px이 된다.


```html
<body> 
    <div class="test">Test</div> 
</body>
```

```css
body { font-size: 14px; 
}

div { font-size: 1.2em; // div의 font-size = 14 * 1.2 = 16.8px 
}
```

- 이처럼 body에 font-size를 적용하고 자식 요소들의 font-size에 em값을 사용하면 body의 font-size를 상속 받아 모든 자식요소들의 font-size에 영향을 미치게 되는 것!

```html
<div>
    child1 (14 * 1.2 = 16.8px)
    <div>
        child2 (16.8 * 1.2 = 20.16px)
        <div>
            child3 (20.16 * 1.2 = 24.192px)
        </div>
    </div>
</div>
```
<img width="480" alt="스크린샷 2021-08-16 오전 12 26 14" src="https://user-images.githubusercontent.com/48905932/129483624-e6e69e70-c244-4665-8db6-031ad9f944a4.png">

- em을 사용할 경우 이렇게 ,,,상속에 상속에 상속을 더해서~ 마트료시카 인형처럼 글씨가 점점 커지는 결과가 발생할 수 있으니 주의해야한다.😮

---

# 📐rem (root em)
> rem은 오직 html 태그의 font-size만 참조한다.

![그룹 51](https://user-images.githubusercontent.com/48905932/129483017-aeba5f92-1f90-4df3-a2a2-eb6a6fad725d.png)

- 따라서 html의 font-size를 참조하여 10 * 2 = 20px이 된다.
- em의 경우 상속받은 값이 변경되거나 추가 요소가 생길 경우 복잡해 질 수 있기 때문에 rem 사용을 권장한다. 
- 특히 계산의 편의를 위해 html 태그의 font-size를 10px로 맞춰놓고 개발을 시작하는 경우가 많다고 한다.

```css
html{
    font-size: 62.5%;
}
```

- 🍯 브라우저 기본 설정 기준 html의 font-size는 16px이기 때문에 62.5%를 곱해주면 10px로 맞춰놓고 시작할 수 있다!

</br>

이제 반응형 웹 페이지에서 자주 사용되는 vh, vw, vmin, vmax에 대해 알아보자.

# vh 
> Viewport Width, 즉 뷰포트 너비의 1% 길이와 동일하다.

ex. 뷰포트의 너비값이 1000px라면, vh는 1000/100 = 10px

# vw
> Viewport Height, 즉 뷰표트 높이의 1% 길이와 동일하다.

ex. 뷰포트의 높이값이 500px라면, vw는 500/100 = 5px

# vmin & vmax
> 뷰포트의 너비값과 높이값에 따라 최대, 최소값을 지정할 수 있다.

ex. 뷰포트의 너비가 1500px, 높이가 3000px 이라면, vmin = 1500/100 = 15px, vmax = 3000/100 = 30px


