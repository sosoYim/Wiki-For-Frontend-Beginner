# Web Vitals

## 웹 바이탈 이란?

![image](https://user-images.githubusercontent.com/53992007/131055003-59d50be8-e5d2-4a29-b865-c19d9b6036b8.png)


Web Vitals는 구글이 주요 웹 사이트 품질 지표 중 하나인 사용자 경험을 위해 사이트를 어떻게 측정했는 지 확인할 수 있는 획기적인 측정 도구입니다. 웹 바이탈 항목에는 약 7가지 항목이 있는 데, 구글은 2021년 5월 코어 웹 바이탈 항목을 검색 결과 요소에 반영하겠다고 발표하였습니다. 코어 웹 바이탈에 대해서 알아보기 전, 다른 웹 바이탈에 대해서 간략하게 설명드리겠습니다.


- 모바일 친화성: 얼마나 모바일에 친화적이고 최적화 되었는 가?

- 안전 브라우징: 컨텐츠에 악성 소프트웨어 같은 것들이 포함되어 있지 않은 가?

- HTTPS: HTTPS보안 프로토콜 버전을 사용하고 있는가?

- 방해요소: 페이지 컨텐츠를 방해하는 요소가 있는 가?

구글은 이 4가지 요소를 제외한 LCP, FID, CLS를 구글 코어 웹바이탈 항목으로 분류하였습니다. 


<br>

## Core Web Vitals

### LCP

![image](https://user-images.githubusercontent.com/53992007/131057090-cfa9a0bb-4d02-4ff0-b80f-92e5b57a8667.png)

LCP는 페이지의 **로딩 성능**을 측정하는 항목입니다. 사용자에게 좋은 경험을 제공하기 위해선, 페이지가 처음으로 로딩되었을 시 스크롤 없이 볼 수 있는 부분을 2.5초 안에 표시해야 한다고 합니다.



### FID

![image](https://user-images.githubusercontent.com/53992007/131057061-5be2bad1-66d5-4b7f-bb52-524cc8dc5fda.png)

FID는 페이지의 **응답성**을 측정하는 항목입니다. 이 항목은 버튼 클릭과 같은 상호작용이 이루어질 때, 100밀리세컨드 이내에 이루어져야 좋은 사용자 경험이라고 합니다.

### CLS

![image](https://user-images.githubusercontent.com/53992007/131057028-25f74307-e275-4568-9180-5941d3ac1617.png)

CLS는 **시각적 안정성**을 측정하는 항목입니다. 이는 눈에 보이는 페이지 콘텐츠의 예기치 않은 레이아웃의 변화량을 정량화 하는 것으로 0에 가까울수록 좋은 환경을 제공하는 것이라고 판단합니다.


<br>

## 코어 웹 바이탈을 측정하고 보고하는 도구

### 측정과 보고하는 도구

| 항목| LCP | FID | CLS |
|:---|:----|:----|:----| 
|[Chrome User Experience Report](https://web.dev/vitals/#:~:text=CLS-,Chrome%20User%20Experience%20Report,-%E2%9C%94) | O | O | O |
|[PageSpeed Insights](https://web.dev/vitals/#:~:text=%E2%9C%94-,PageSpeed%20Insights,-%E2%9C%94) |O | O | O |
| [Search Console (Core Web Vitals report)](https://web.dev/vitals/#:~:text=Search%20Console%20(Core%20Web%20Vitals%20report))|O | O | O |


### 간단하게 측정만 하는 도구


| 항목| LCP | FID | CLS |
|:---|:----|:----|:----| 
|[Chrome DevTools](https://web.dev/vitals/#:~:text=CLS-,Chrome%20DevTools,-%E2%9C%94) | O | X(대신 [TBT](https://web.dev/tbt/)로 측정) | O |
|[Lighthouse](https://web.dev/vitals/#:~:text=%E2%9C%94-,Lighthouse,-%E2%9C%94) |O | X (대신 [TBT](https://web.dev/tbt/)로 측정)| O |


<br>


## CSS for web Vitals

### 웹 바이탈 최적화를 위한 CSS 관련 기술

> 이 글은 [CSS for Web Vitals](https://web.dev/css-web-vitals/) 를 번역한 글입니다.

스타일을 작성하고 레이아웃을 작성하는 방법에 따라 Core Web Vitals에 큰 영향을 미칠 수 있습니다. 이는 특히 CLS와 LCP에 영향을 미치는데, 이와 관련하여 웹 바이탈 최적화를 위한 CSS 관련 기술에 대해 설명합니다. 이러한 최적화는 레이아웃, 이미지, 글꼴, 애니메이션, 로드 등 페이지의 여러 가지 측면에 따라 구분됩니다. 이 과정에서는 [예제 페이지](https://codepen.io/una/pen/vYyLKvY)를 개선하는 방법에 대해 알아봅니다.



![image](https://user-images.githubusercontent.com/53992007/131062518-a99b138a-69af-4285-a1fb-fc7a135aba53.png)


#### 레이아웃

**DOM에 내용 삽입**

주변 내용이 이미 로드된 후 페이지에 내용을 삽입하면 페이지의 다른 모든 내용이 아래로 내려갑니다. 이로 인해 레이아웃 이동이 발생합니다.

쿠키 통지(특히 페이지 맨 위에 배치된 통지)는 이 문제의 일반적인 예입니다. 로드 시 종종 이러한 유형의 레이아웃 이동을 일으키는 페이지 요소에는 광고와 embed가 포함됩니다.


**쿠키를 상단에 배치 하여 생기는 문제** 

Lighthouse "대규모 레이아웃 이동 방지" 감사는 이동된 페이지 요소를 식별합니다. 이 데모의 결과는 다음과 같습니다.

![image](https://user-images.githubusercontent.com/53992007/131063157-2ac7d16e-ebd2-41a3-820e-97e9a1598920.png)

쿠키 알림이 로드될 때 쿠키 알림 자체가 이동하지 않기 때문에 이 결과에는 쿠키 알림이 나열되지 않습니다. 오히려 페이지의 아래 항목(즉, div.hero와 기사)이 이동하게 합니다.

**위 사례를 수정하는 방법**

`position: absolute` 또는 `fix`와 같은 고정 포지셔닝을 사용하여 쿠키 공지를 페이지 하단에 배치합니다.

![image](https://user-images.githubusercontent.com/53992007/131063510-948a698d-4b5b-4ec2-b243-df98c61db944.png)


Before:

```css
.banner {
  position: sticky;
  top: 0;
}
```

After:

```css
.banner {
  position: fixed;
  bottom: 0;
}
```


이 레이아웃 이동을 수정하는 또 다른 방법은 화면 상단에 있는 쿠키를 공지하는 부분의 공간을 미리 설정해 두는 것입니다. 이 접근법은 똑같이 효과적이며, 자세한 내용은 [쿠키 알림 모범 사례](https://web.dev/cookie-notice-best-practices/)를 참조하십시오.


#### 이미지

**이미지와 LCP**

이미지는 일반적으로 페이지에서 LCP(Largest Contentful Paint) 요소입니다. LCP 요소가 될 수 있는 다른 페이지 요소에는 텍스트 블록 및 비디오 포스터 이미지가 포함됩니다. LCP 요소가 로드되는 시간에 따라 LCP가 결정됩니다.

페이지의 LCP 요소는 페이지가 처음 표시될 때 사용자에게 표시되는 내용에 따라 페이지 로드마다 다를 수 있습니다. 예를 들어, 이 데모에서 쿠키 알림의 배경, 히어로 이미지 및 문서 텍스트는 잠재적인 LCP 요소 중 하나입니다.


![image](https://user-images.githubusercontent.com/53992007/131063845-c111b75b-6dbb-4397-84d4-f4623c559477.png)


예제 사이트에서 쿠키 알림의 배경 이미지는 실제로 큰 이미지입니다. LCP를 개선하기 위해 이미지를 로드하여 효과를 만드는 대신 CSS에서 그라데이션 페인트를 칠할 수 있습니다.



**위 사례를 수정하는 방법**

이미지가 아닌 CSS 그라데이션으로 .banner CSS를 변경합니다.

Before:

```css
background: url("https://cdn.pixabay.com/photo/2015/07/15/06/14/gradient-845701\_960\_720.jpg")
```

After:

```css
background: linear-gradient(135deg, #fbc6ff 20%, #bdfff9 90%);
```


**이미지 및 레이아웃 이동**

브라우저는 이미지가 로드된 후에 이미지의 크기를 결정할 수 있습니다. 페이지가 렌더링된 후 이미지 로드가 발생하지만 이미지에 예약된 공간이 없는 경우 이미지가 나타날 때 레이아웃 이동이 발생합니다. 데모페이지에서 히어로 이미지는 로드 시 레이아웃 이동을 유발합니다.

> 이미지가 느리게 연결되거나 파일 크기가 특히 큰 이미지를 로드하는 등 이미지 로드 속도가 느린 상황에서 레이아웃 이동을 일으키는 현상은 더욱 뚜렷합니다.



**이미지 레이아웃 이동 문제**

명시적 너비와 높이가 없는 이미지를 확인하려면 Lighthouse의 "이미지 요소에는 명시적 너비와 높이가 있습니다" 감사를 사용하십시오.

![image](https://user-images.githubusercontent.com/53992007/131064544-b603c164-284c-4d01-8571-83e3d14cdb38.png)


이 예제에서는 히어로 이미지와 아티클 이미지 모두에 너비 및 높이 속성이 누락되었습니다.

**위 사례를 수정하는 방법**

레이아웃 이동을 방지하기 위해 이 이미지에 너비 및 높이 속성을 설정합니다.



Before:

```css
<img src="https://source.unsplash.com/random/2000x600" alt="image to load in">
<img src="https://source.unsplash.com/random/800x600" alt="image to load in">
```

After:

```css
<img src="https://source.unsplash.com/random/2000x600" width="2000" height="600" alt="image to load in">
<img src="https://source.unsplash.com/random/800x600" width="800" height="600" alt="image to load in">
```



> 이미지를 로드 하는 또 다른 방법은 너비 및 속성을 지정하는 것과 함께, srcset 및 크기 속성을 사용하는 것입니다. 이렇게 하면 크기가 다른 이미지를 다른 장치에 제공할 수 있다는 추가적인 성능 이점이 있습니다.



#### 글꼴

글꼴은 텍스트 렌더링을 지연시키고 레이아웃 이동을 유발할 수 있습니다. 따라서 글꼴을 빨리 전달하는 것이 중요합니다.

**지연된 텍스트 렌더링**

기본적으로 연결된 웹 글꼴이 아직 로드되지 않은 경우 브라우저는 텍스트 요소를 즉시 렌더링하지 않습니다. 이는 "스타일 없는 텍스트의 플래시"(FOUT)를 방지하기 위해 수행됩니다. 대부분의 경우 이 경우 FCP(First Contentful Paint)가 지연됩니다. 경우에 따라 최대 내용물 페인트(LCP)가 지연됩니다.

기본적으로 크롬 기반 및 Firefox 브라우저는 연결된 웹 글꼴이 로드되지 않은 경우 최대 3초 동안 텍스트 렌더링을 차단하고 Safari는 텍스트 렌더링을 무기한 차단합니다. 차단 기간은 브라우저가 웹 글꼴을 요청할 때 시작됩니다. 차단 기간이 끝날 때까지 글꼴이 로드되지 않은 경우 브라우저는 fallback 글꼴을 사용하여 텍스트를 렌더링하고 웹 글꼴에서 스왑합니다.


**레이아웃 이동**


글꼴 스와핑은 사용자에게 콘텐츠를 빠르게 표시하는 데 탁월하지만 레이아웃 이동을 유발할 수 있습니다. 이러한 레이아웃 이동은 웹 글꼴과 fallback 글꼴이 페이지에서 다른 공간을 차지할 때 발생합니다. 유사한 비율의 글꼴을 사용하면 이러한 레이아웃 이동의 크기가 최소화됩니다.


![image](https://user-images.githubusercontent.com/53992007/131064984-7e057597-6a5a-45bd-a156-6baef3e49e0f.png)


**글꼴 관련 문제**


특정 페이지에서 로드 중인 글꼴을 보려면 개발자 도구에서 네트워크 탭을 열고 글꼴별로 필터링합니다. 글꼴은 큰 파일이 될 수 있으므로 일반적으로 적은 수의 글꼴만 사용하는 것이 성능에 더 좋습니다.


![image](https://user-images.githubusercontent.com/53992007/131069982-c92e0292-31fb-443e-9a6e-39918f602735.png)

글꼴을 요청하는 데 걸리는 시간을 보려면 [타이밍] 탭을 클릭합니다. 글꼴을 빨리 요청할수록 더 빨리 로드하여 사용할 수 있습니다.

![image](https://user-images.githubusercontent.com/53992007/131070122-e3a72005-5034-468e-9363-5e21b58edd6a.png)




**위 사례를 수정하는 방법**

이 예제에서는 Google 글꼴 API를 사용합니다. Google 글꼴은 `<link>` 태그 또는 @import 문을 통해 글꼴을 로드하는 옵션을 제공합니다. `<link>` 코드에는 `사전 연결` 리소스 힌트가 포함되어 있습니다. 따라서 @import 버전을 사용하는 것보다 스타일시트가 더 빨리 전달됩니다.

매우 높은 수준에서 리소스 힌트를 브라우저에 `특정 연결`을 설정하거나 `특정 리소스`를 다운로드해야 함을 암시하는 방법으로 생각할 수 있습니다. 따라서 브라우저는 이러한 작업의 우선 순위를 지정합니다. 리소스 힌트를 사용할 때 특정 작업의 우선 순위를 지정하게되면 브라우저 리소스가 다른 작업(우선하지 않은 작업)에서 제거됩니다. 따라서 리소스 힌트는 주의하여 사용해야 합니다. 

스타일시트에서 다음 `@import` 문을 제거합니다.

```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400&family=Roboto:wght@300&display=swap');
```

다음 `<링크>` 태그를 문서의 `<헤드>`에 추가하십시오.

```css
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap" rel="stylesheet">
```


이러한 링크 태그는 브라우저가 Google 글꼴에서 사용하는 원본에 대한 초기 연결을 설정하고 Montserrat와 Roboto 글꼴 선언이 포함된 스타일시트를 로드하도록 지시합니다. 이러한 `<link>` 태그는 `<head>`태그안의 가능한 한 위쪽에 배치해야 합니다.


> Google Fonts에서 글꼴의 하위 집합만 로드하려면 `?text=` API 매개변수를 추가하십시오. 예를 들어 `?text=ABC`는 "ABC"를 렌더링하는 데 필요한 문자만 로드합니다. 이것은 글꼴의 파일 크기를 줄이는 좋은 방법입니다.



#### 애니메이션


애니메이션이 웹 바이탈에 영향을 미치는 주된 요인은 애니메이션이 레이아웃 이동 발생시킬 때 입니다. 레이아웃을 트리거하는 애니메이션과 페이지 요소를 이동하는 "애니메이션 유사" 효과의 두 가지 유형을 사용하면 안 됩니다. 일반적으로 이러한 애니메이션은 변환, 불투명도 및 필터와 같은 CSS 속성을 사용하여 보다 우수한 성능의 애니메이션으로 대체될 수 있습니다. 


**애니메이션 문제 식별**

Lighthouse의 "합성되지 않은 애니메이션 방지" 감사는 성능 저하된 애니메이션을 식별하는 데 도움이 될 수 있습니다.

![image](https://user-images.githubusercontent.com/53992007/131218640-1fa578f1-5fc2-41fe-9fc7-da208e8c0001.png)

> Lighthouse의 "합성되지 않은 애니메이션 방지" 감사 기능은 비성능 CSS애니메이션만 식별합니다. JS기반 애니메이션(예: 요소를 "애니메이션"하기 위해 setInterval()을 사용)은 성능에 좋지 않지만 이 감사에서 제외됩니다.

**애니메이션 문제 수정방법**

slideIn 애니메이션 시퀀스를 변경하여 `margin-left`를 변경하는 대신 `translateX`를 사용합니다.

Before:

```Css
.header {
  animation: slideIn 1s 1 ease;
}

@keyframes slideIn {
  from {
    margin-left: -100%;
  }
  to {
    margin-left: 0;
  }
}
```

After:

```css
.header {
  animation: slideIn 1s 1 ease;
}

@keyframes slideIn {
  from {
    transform: translateX(-100%);
  }

  to {
    transform: translateX(0);
  }
}
```

#### 중요한 CSS만 태그에 담자

스타일시트는 reder-blocking됩니다. 이 말의 의미는 브라우저에서 스타일시트를 다운로드하고 구문 분석할 때까지 다른 리소스 다운로드가 중지됩니다. 이로 인해 LCP가 지연될 수 있습니다. 성능을 향상시키려면 사용되지 않는 CSS를 제거하고, 중요 CSS를 인라인화하며, 중요하지 않은 CSS를 연기하는 것이 좋습니다.

#### 결론
아직 더 개선해야 할 여지가 있지만(예: 이미지 압축을 사용하여 이미지를 더 빠르게 전송), 이러한 변경으로 인해 이 사이트의 웹 바이탈이 크게 향상되었습니다. 실제 사이트인 경우 다음 단계는 실제 사용자로부터 성능 데이터를 수집하여 대부분의 사용자에 대한 Web Vitals 임계값을 충족하는지 여부를 평가하는 것입니다. 

<br>


## 추가적으로 읽으면 좋은 자료들

- [Optimize Largest Contentful Paint](https://web.dev/optimize-lcp/)
- [Optimize First Input Delay](https://web.dev/optimize-fid/)
- [Optimize Cumulative Layout Shift](https://web.dev/optimize-cls/)

<br>

## 참고 사이트
- [Web Vitals](https://web.dev/vitals/)
- [Web Vitals 소개: 건강한 사이트를 위한 필수적인 측정항목](https://developers-kr.googleblog.com/2020/05/Introducing-Web-Vitals.html)
- [Core Web Vital Tooling](https://css-tricks.com/core-web-vital-tooling/)
- [CSS for Web Vitals](https://web.dev/css-web-vitals/)
- [구글 코어 웹 바이탈이란?](https://noelle-world.tistory.com/14)