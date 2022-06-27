# Box Model

HTML문서의 요소들은 기본적으로 Box 모형의 형태갖는다.

## Box 예시

다음의 예를 보자.

<img src="C:\Users\Jay\Desktop\New_git\front\HTML_CSS정리\naver.PNG" alt="naver"  />

네이버 홈페이지의 로그인 창을 봐보자.
개발자 도구에서 로그인 창의 정보를 봐보면

 <img src="C:\Users\Jay\Desktop\New_git\front\HTML_CSS정리\box.PNG" alt="box" style="zoom:110%;" align="Left"/>











이러한 박스 형태를 갖는다.

- 파란 박스 (315 x 105)는 위 로그인창의 빨간 박스 안쪽 내용
- padding 영역은 로그인창의 파란 부분
- border는 노란 박스 부분
- margin은 현 요소와 다른 요소들간의 간격을 뜻 함



## Box 조절하기

### padding

padding 부분의 크기를 조절해보자.

1. 직접 방향을 지정해줘서 조절
   - 방향을 top, bottom, left, right 로 입력

```css
p {
    border: 1px solid blue;
    padding-top: 20px;
    padding-bottom: 30px;
    padding-left: 40px;
    padding-right: 50px
}
```

2. 순서대로 쓰면 위치대로 적용

```css
p {
    border: 1px solid blue;
    padding: top right bottom left;
    padding: 20px 50px 30px 40px;
}
```

3. 모두 같은 값 적용

```css
p {
    border: 1px solid blue;
    padding: 20px;
}
```

4. 위아래, 왼쪽오른쪽 각각 같은 값

```css
p {
    /* 위아래는 50px, 왼쪽오른쪽은 50px */
    border: 1px solid blue;
    padding: 20px 50px;
}
```



### margin

margin도 padding과 기본적으로 같다.

margin-top, margin-bottom, margin-left, margin-right로 쓰면 된다.



### 가운데정렬

앞에서 사진 정렬을 할 때 처럼 가운데 정렬하려면 값을 auto로 해주면 된다.

```css
p {
    border: 1px solid blue;
    width: 100px;
    margin-left: auto;
    margin-right: auto;
}
```



### width, height

요소의 가로길이와 세로길이를 직접적으로 지정해서 만들 수 있다.

```css
p {
    width: 100px;
    height: 200px;
}
```



최대최소 영역을 지정해 줄 수도 있다.

```css
p {
    min-width: 100px;
    max-height: 200px;
}
```

- 브라우저 크기에 따라 달라지는데, 창 크기를 가로로 줄일 때 같이 줄어들면서 최소 100px까지 줄면 더이상 따라서 줄지 않는다.
- max도 동일하게 높이가 창 크기에 따라 증가하나, 200px를 넘어가면 같이 증가하지 않는다.



#### overflow

그렇다면, width, height를 넘어서는 내용이 오면 어떻게 될까? 이런걸 overflow라고 한다.

선택지는 4가지가 있다.

1. 넘어가는 부분을 가려버린다. (넘어간 부분을 잘라내버림)
2. 넘어가도록 남겨둔다. (다른 영역을 침범할 수 있음)
3. 넘어가는 부분을 scroll처리해버린다. (단, 넘지 않아도 스크롤이 생긴다.)
4. auto (넘어가면 스크롤이 생기도록 처리) - :sparkles:추천:sparkles:

```css
/* css에 overflow 요소를 주자 */

/* 1. 넘어가는 부분을 가려버린다. */
overflow: hidden;

/* 2. 넘어가도록 남겨둔다. (default값임) */
overflow: visible;

/* 3. scroll 만들기 */
overflow: scroll;

/* 4. auto로 돌리기 */
overflow: auto;
```



### border

테두리 설정에 대해 살펴보자. (top, bottom, left, height 도 같이 쓸 수 있음)

```css
p {
    border: 2px solid red;
}
```

- 테두리 두께는 2px
- 테두리 형태는 solid
  - style 설정 : https://developer.mozilla.org/ko/docs/Web/CSS/border-style
- 테두리 색상은 red
  - hex 색상으로 써도된다.



#### border 삭제

border를 안쓰고 싶다면?

둘 중에 하나를 쓰면된다.

```css
border: none;

border: 0;
```



#### border 꾸미기

- trim같은 기능 (테두리 끝 부분을 10px만큼 둥글게 깎는다.)

```css
/* 전체 */
border-radius: 10px;

/* 부분 */
border-top-left-radius: 50px; /* 왼쪽 위 */
border-top-right-radius: 5px; /* 오른쪽 위 */
border-bottom-right-radius: 0px; /* 오른쪽 아래 */
border-bottom-left-radius: 20px; /* 왼쪽 아래 */
```



- background-color (배경색 설정)
  - transparent : 배경색을 투명하게 설정 (default값)

```css
background-color: red;

background-color: transparent;
```



- 그림자 설정
  - default = none
  - 박스에 그림자 효과를 넣을 수 있음
  - `-`부호로 방향 설정

```css
box-shadow: 50px 50px; /* right, bottom */
box-shadow: -50px -50px; /* left, top */

/* right, bottom, blur, 그림자가 퍼지는 정도(spread), 색상 */
box-shadow: 50px 50px 50px -10px red;
```



### box-sizing

박스는 가로, 세로 길이 구성이 border size + padding size + content size 인데

딱 어느 값으로 고정되게 만들려면 위의 3가지를 잘 조절하면서 만들어야한다.

그러나 이는 번거롭고 귀찮다.

이럴 땐, box-sizing을 넣어주면된다.

```css
p {
    width: 300px; /*width와 height는 border와 padding을 뺀 content의 크기만을 뜻함 */
    height: 200px;
    padding: 35px;
    border: 5px solid red;
    box-sizing: border-box;
}
```

box크기가 border-box의 크기로 고정됨 (알아서 위의 width, height로 만들어줌) 

즉, width, height가 border, padding, content 전체를 포함한 값이 된다.



모든 요소에 box-sizing을 넣고싶다면 `*`을 쓰고 box-sizing을 주면된다.

```css
* {
    box-sizing: border-box;
}
```



