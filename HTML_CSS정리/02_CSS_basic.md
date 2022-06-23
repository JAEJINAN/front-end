# CSS

## 시작하기 앞서

### 주석

css주석은 다음과 같이 쓴다.

```css
/* 주석입니다 */
```





## 기본 포맷

css는 기본적으론 다음과 같이 쓰인다.

```css
h1 {
    font-size: 64px;
    text-align: center;
}
```

- 맨앞 : 꾸며주고 싶은 html 요소 (여기선 h1태그)
- 속성 : h1에 css 속성을 부여 (font-size, text-align)
- 속성 값 : 속성의 세부 설정값 부여 (64px, center)



HTML문서 내에 css를 동시에 쓰려면 style태그와 함께 쓴다.

```html
<style>
h1 {
    font-size: 64px;
    text-align: center;
}
    
h2 {
    margin-top: 100px;
}
    
p i {
	font-size: 48px;
}
</style>
```

p i는 뭘까? i라고만 쓰면 문서 내 전체 i태그에 다 반영된다. 

특정 위치의 i만 적용하고자하면?
예: p태그 안에 있는 i에만 적용하고 싶다할 때 저렇게 쓴다.



## 기본 속성 정리

기본은 h1태그로 하겠다.

### 폰트 크기 (font-size)

```css
h1 {
    font-size: ##px;
}
```

px외에도 크기를 나타내는 단위가 많지만 일단 패스



### 텍스트 정렬 (text-align)

```css
h1 {
text-align: left;
text-align: right;
text-align: center;
}
```



### 텍스트 색상 (color)

```css
h1 {
	color: blue;
}
```



### 여백 (margin)

요소 사이의 여백을 설정해 줄 수 있음

```css
h1 {
    margin-bottom: 80px;
    margin-left: 50px;
}
```









## Display attribute

- Block
- Inline
- Inline-block
- None



### block

너비가 최대, 한줄 다차지



### Inline

글씨만큼만 높이를 가져감



### Inline-block

글씨 너비만큼가져가지만 블록이 있음





## SIZE

- px
- em
- rem
- %



## px

고정값

### em

em은 부보의 크기를 따라서 변경이 됨

부모가 여러개면 문제가 생김

부모1, 부모2가 각 2배씩 커지면 child가 4배가 되버림...

### rem

