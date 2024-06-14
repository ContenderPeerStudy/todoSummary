# FormInput 컴포넌트

## 위치

src/components/FormInput.js

-   공용 컴포넌트

## 주변 컴포넌트

[sign-in-form.jsx](./summary3_SignIn.md) <-[SignUpForm.jsx](./summary4_SignUp.md)  
&emsp;|||  
FormInput.jsx

## 기능

-   size props로 받은 번호에 따라 css가 달라진다.

## 동작 원리

### 1. return 문

-   (1) props 객체의 속성을 구조 분해 할당으로 받는다.
    -   input 태그에 전달될 수 있는 속성이 매우 많으므로 이러한 속성은 따로 지정하는 게 아니라 나머지 매개변수 연산자(...props)로 받을 수 있는 공간만 마련한다.
        -   나중에 input 태그에 들어갈 속성을 넣으면 나머지 매개변수로 들어간다.
    -   containerStyle은 용도가 뭐지?
-   (2) InputBox 태그와 Input 태그에 size 번호를 넣는다.
-   (3) Input 태그에 ...props 매개변수를 넣는다.

### 2. CSS

-   (1) props에 있는 size 번호를 가져온다.
-   (2) sizeCSS 객체에서 위 번호에 해당되는 CSS를 가져온다.

*   (3) placeholder
    -   & 선택자 자기 자신을 뜻하는 기호이다.
    -   ::placeholder placeholder 텍스트의 모양을 바꿀 수 있는 가상 선택자이다.
