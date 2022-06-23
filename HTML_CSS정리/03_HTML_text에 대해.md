# Text에 대해

## Color

- 색상 이름으로 표현

  ```css
  h1 {
      color: blue;
  }
  ```

- RGB 또는 HEX로 표현

  ```css
  h1 {
  	color: rgb(97, 249, 107);
  }
  
  h2 {
      color: #61F96B;
  }
  ```

  hex는 RGB값을 16진법으로 바꾼것



## 텍스트 스타일링

### font-weight

100부터 900까지 값을 갖을 수 있으며 숫자가 커질수록 폰트가 굵어짐
100단위씩으로만 지원함 100, 200, 300, ... 800, 900, 그 외의 값 예를 들어 110같은것 없음

폰트나 브라우저에 따라 사용할 수 있는 값이 지정되어있을 수 있음. 그래서 테스트해보면서 사용해야한다.

400이 보통적인 굵기고 700정도가 b태그 굵기정도라 함

- 100일 때
	
	- <p style="font-weight: 100;">스타일링을 해보자</p>
	
- 900일 때
	- <p style="font-weight: 900;">스타일링을 해보자</p>

> 참고
>
> font-weight: normal = font-weight: 400
>
> font-weight: bold = font-weight: 700



### text-align

텍스트를 정렬해주는 요소

left, right, center가 있음



### text-decoration

텍스트를 꾸며주는 기능

- underline : 텍스트 밑에 줄을 그어줌
- overline : 텍스트 위에 줄을 그어줌
- line-through : 텍스트에 줄을 그어줌 ~~ㅁㅇㅁㄴㅇ~~
- none : 하이퍼링크같은 경우 자동으로 밑줄이 그어지는 경우가 있는게 그런게 보기싫을 때 none을 지정해주면 사라짐
  - a태그와 같이 사용
    a태그는 기본적으로 밑줄이 그어져서 나온다. 이때 밑줄이 보기싫어서 text-decoration을 주로 쓴다.




### 텍스트 정렬이 안될 때

어떤 태그는 정렬하고자 할 때 정렬이 안되는 경우가 있다. 왜그럴까? 그 태그의 영역이 딱 그 태그를 표현하는 영역에만 있기 때문이다. 그렇기에 정렬을 하나 안하나 그 위치에 있기때문에 변화가 없다.

이럴 때는 그 태그를 div로 감싸고 div에 정렬을 주자.



### 텍스트 크기

- Absolute (절대값)
  - px, pt
- Relative (상대값)
  - em, %

#### px

HTML에서 크기를 나타내는 기본 단위로 픽셀(px) 단위를 사용한다.
절대값을 가지므로 항상 픽셀값에 해당하는 크기를 갖는다.

#### pt

px의 1.33배 정도 되는 크기라고 한다. 웹페이지 만들 땐 잘 안쓰인다고 한다.

#### em

%와 기능적으로는 같다.
1em = 100%, 2 em= 200%...

#### %

픽셀 대신에 퍼센트를 사용할 수도 있다. 부모요소에 대한 %비율을 크기로 갖는다. 부모요소가 24px이면 50%면 14px 크기를 갖는 것이다.

이미지로 예를 들면 실제 이미지 크기를 그대로 출력하고자 하면 100%, 반으로 줄이려면 50%, 이런식으로 사용된다.



### line-height

![line-height](C:\Users\Jay\Desktop\New_git\front\HTML_CSS정리\line-height.PNG)

우선 위 사진의 파란 줄 사이 글자 영역을 `content area`라고 한다. 
content area는 font-family와 font-size에 따라 결정된다. (line-height영향은 없다.)

위 사진의 분홍 박스 영역을 봐보자.
line-height: normal인경우 content area에 해당하는 영역을 갖게된다. 

line-height: 99px로 지정해주면 content area의 px를 뺀 나머지 40px가 남는데 이를 반반씩해서 위아래로 나눠 영역을 차지한다.

content area보다 작은 line-height를 가지면 차의 반반씩만큼 영역이 줄어든다.



### font

기본 폰트 -> 사용자 컴퓨터에 설치되어있어야 적용된다.

- Serif
  - Times New Roman
  - 궁서체
- Sans-Serif
  - Arial
  - 굴림체
- Monospace
  - Courier
  - Courier New
- Cursive
  - Comic Sans MS
  - Monotype Corsiva
- Fantasy
  - Impact
  - Haettenschweiler

등등

```css
h1 {
    font-family: "Times New Roman", Times, serif;
}
```

띄어쓰기가 있는 경우 ""로 감싸줘야하며 여러 폰트패밀리를 써주는건 순차적으로 우선순위를 가지며 쓰여지는데 없을 경우 다음 폰트를 쓰기위함이다. 보통 맨 마지막은 위의 serif, Sans-Serif같은 기본 폰트를 써줌. (최후의 수단임. 다 없을 경우 기본폰트를 쓰겠다는 의미)



### 외부 font를 쓰려면?

link태그를 통해 다운받아와야한다.

예로 구글폰트를 적용하려면?

```html
<head>
	...
    <link href="https://fonts.googleapis.com/css?family=Barrio|Roboto" ref="stylesheet">
    ...
</head>
```

html이 실행될 때 해당 링크의 주소에서 폰트를 받아와서 적용시켜준다.



### 다운받은 font를 쓰려면?

폰트를 다운을 받고 css에 이렇게 추가해주자.

@font-face로 css파일에 폰트를 추가해주고 밑에 태그들에 font-family로 적용 시켜주면 된다.

```css
@font-face {
    src: url("../fonts/BMJUA_otf.otf");
    font-family: "Jua";
}

p {
    font-family: "Jua";
}
```

