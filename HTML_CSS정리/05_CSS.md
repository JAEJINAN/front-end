# CSS 파고들기

## CSS 상속

부모 태그의 속성이 자식 태그들에게도 적용되는 것을 CSS 상속이라고 한다.

모든 것이 상속되는 것은 아니다.



종류는 더 많지만 대표적으로 상속이 되는 속성들이다.

```bash
├── color
├── font-family
├── font-size
├── font-weight
├── line-height
├── list-style
├── text-align
└── visibility
```



> a태그는 상속을 받지 않는다.



## CSS 우선순위

### 중복 요소

상속은 순서대로 받는다. 단, 같은 셀렉터가 나오면 후 순위가 전 순위의 셀렉터를 덮어쓴다.

```css
h1 {
  color: blue;
  text-align: center;
}

h1 {
  color: green;
}
```

이 경우 첫 번째 속성인 color와 text-align이 적용된다. 처음엔 색이 blue였지만, 두 번째 속성인 green을 만나 색이 green으로 덮어 쓰여진다.



### 명시도(Specificity)

같은 요소이나 셀렉터가 다르면, 명시도에 따라 우선 순위가 정해진다.

**명시도 계산**

1. 인라인 스타일이 가장 우선 순위가 높다.
2. 셀렉터에 id가 많을 수록 우선 순위가 높다.
3. 셀렉터에 class, attribute, pseudo-class가 많을 수록 우선 순위가 높다.
4. 요소가 많은 순서

| Inline styles | IDs  | Classes, attributes, pseudo-classes | Elements, pseudo-elements |
| ------------- | ---- | ----------------------------------- | ------------------------- |
| 0             | 0    | 0                                   | 0                         |



예시)

```html
<ul>
  <li><a id="link" href="#">Link 1</a></li> <!-- ** -->
  <li><a id="link" href="#">Link 1</a></li>
  <li><a id="link" href="#">Link 1</a></li>
  <li><a id="link" href="#">Link 1</a></li>
</ul>
```

다음 CSS는 둘 다 위의 HTML에서 첫 번째 `**`을 가리킨다. 다음 중 어느 것을 따를까?

```css
ul li:first-child #link {
  color: green;
}

ul li:first-child a {
  color: orange;
}
```



위의 명시도 계산법에 따라서 

첫 번째는 id가 1개(#link), pseudo-class가 1개 (:first-child), 요소가 2개 (ul, li)라서 점수가 0112

두 번째는 pseudo-class가 1개 (:first-child), 요소가 3개 (ul, li, a)라서 점수가 0013이다.

그래서 첫 번째인 112가 13보다 높아서 더 우선순위이다. 즉, 글자는 green으로 출력된다.



## Display

layout을 제대로 하기 위해선 inline, block, inline-block, list-item, table, flex, none 등에 대해 알아야 한다.

모든 요소는 딱 한 개의 display값을 갖는다.



### inline display

- 다른 요소들과 같은 줄에 머무르려고 하는 성향을 가진 것들
- 가로 길이는 필요한 만큼만 차지하려 함 (width, height를 줘도 적용이 안된다.)

- 예: span, b, i, a, img, button 등



### block display

- 새로운 줄에 가려고 하는 성향
- 가로 길이를 최대한 많이 차지하려고 하는 성향 (물론 width, height를 줘서 길이 설정도 가능)
- 예: div, h1, p, nav, ul, li



### display 설정

위의 태그별 inline과 block display는 기본적으로 설정이 되어있다. 이를 따로 설정해서 display를 바꿀 수도 있다.

```css
/* 예로 div는 block display인데 이를 inline으로 바꾸면 */
div {
    display: inline;
}

/* 마찬가지로 inline도 block으로 바꿀 수 있다. */
b {
    display: block;
}
```





### inline-block

inline은 width, height를 줘도 값 적용이 안된다.
그러면 inline에도 크기를 주고싶을 땐?

inline을 block화 하자.

```css
b {
    display: inline-block;
    width: 300px;
    height: 300px;
}
```



### img

img는 가로, 세로가 있어서 inline-block같아 보이지만 inline이다.

`<img>`태그는 대체 요소(replaced element)

이미지이지만 글자처럼 생각하면 된다. 그래서 text-align: center도 적용 가능하다.

그래도 정렬은 다음과 같이 쓰는게 좋다.

```css
img {
    display: block;
    margin-left: auto;
    margin-right: auto;
}
```



### links

기본적으로 a태그에 링크를 쓸 땐 텍스트로 썼다. 이미지를 링크로 쓰고 싶을 땐 a태그 안에 img태그를 써주면 된다.

```html
<a href="https://naver.com" target="_blank">
	<img src="naver_logo.png">
</a>
```

<a href="https://naver.com" target="_blank">
	<img src="naver_logo.png" width=300px>
</a>

위 이미지를 클릭하면 naver로 연결된다.



이렇게도 사용가능

```html
<html>
<style>

   a {
        display: block;
        background-color: #f9f9f9;
        color: black;
        text-align: center;
        text-decoration: none;
        width: 300px;
        height: 250px;
        margin-left: auto;
        margin-right: auto;
        border: 2px solid #f9f9f9;
        padding-top: 30px;
    }
</style>
<a class="naver" href="https://naver.com" target="_blank">
	<img src="../HTML_CSS정리/naver_logo.png">
    <h1>
        네이버로 떠납니다.
    </h1>
    <p>
        갑시다.
    </p>
</a>
</html>
```

<img src="C:\Users\Jay\Desktop\New_git\front\HTML_CSS정리\To_naver.PNG" alt="To_naver" style="zoom:105%;" align="Left"/>

위의 코드대로 하면 위의 이미지처럼 블록자체를 누르면 링크를 타고 넘어간다.