# TDButton 컴포넌트

## 위치

src/components

-   공용 컴포넌트

## 주변 컴포넌트

[sign-in-form.jsx](./summary3_SignIn.md) <-[SignUpForm.jsx](./summary4_SignUp.md)  
&emsp;|||  
TDButton.jsx

## 기능

받아온 props에 따라 다양하게 CSS가 바뀌는 버튼

## 동작 원리

### 1. return 문

1. size, shape, variant, children, 나머지 props를 TDButton 함수의 매개변수로 받아온다. [sign-in-form.jsx](summary3_SignIn.md#)
2. children(해당 태그의 자식, 태그 사이에 오는 것을 모두 총칭)을 태그 사이에 넣는다.

### 2. CSS

1. props 객체 안의 요소를 CSS로 가져온다
    ```javascript
        ${(obj)=> variantCSS[obj.variant]}//obj는 props 객체
        ${({size})=> sizeCSS[size]}//size는 props 객체의 size 요소를 구조 분해 할당한 결과물
        ${(props)=> shapeCSS[props.shape]}//props는 props 객체
    ```
2. 1번 요소에 해당되는 CSS 문장을 가져온다.
