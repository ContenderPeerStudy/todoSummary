# SignUp 탭

## 위치

src/pages/main/\_components/SignUpForm.jsx

## 주변 컴포넌트

[Main.jsx](./summary2_Main.md)  
&emsp;|||  
[sign-in-form.jsx](./summary3_SignIn.md) <-SignUpForm.jsx  
&emsp;|||  
[FormInput.jsx](./summary5_FormInput.md), [TDButton.jsx](./summary6_TDButton.md), style.js

## 기능

-   회원가입 후 (이메일)님 환영합니다 alert 창 띄우고 SignIn 탭으로 전환

*   실제 회원가입 할 때는 비밀번호도 받아야 하므로 입력 란은 이메일, 비밀번호, 비밀번호 확인 이렇게 3개

## 동작 원리

### 1. onSubmitSignUp

-   (1) 동작 조건: return 문의 Form을 제출할 때 발동
-   (2) [Main 컴포넌트](./summary2_Main.md#5-컴포넌트-가져오기)의 setFormState 속성으로 setFormState 함수를 받아온다.
    -   props 객체의 setFormState 속성을 구조 분해 할당으로 받으므로 중괄호 반필수
    -   중괄호 안 쓰면 이렇게 써야 함(왜 p로 해도 작동하지? 매개변수는 자동으로 props 객체로 지정되나?)
    -   ```javascript
          const SignUpForm(p) =>{
              //다른 코드
              p.setFormState("SIGN-IN");
          }
        ```
-   (3) input 박스의 이메일 값을 받아와 alert 창을 띄우고 setFormState 함수를 작동시켜 state를 SIGN-IN으로 바꾼다. -> 탭이 SignIn으로 바뀐다.

## 2. return 문

-   (1) SIGNFORM_ARRAY
    <details>
        <summary>상세 코드</summary>

        const SIGNFORM_ARRAY = [
        {
            label: "이메일",
            size: 3,
            name: "email",
            option: {
                placeholder: "이메일을 입력해주세요",
            },
        },
        {
            label: "비밀번호",
            size: 3,
            name: "password",
        },
        {
            label: "비밀번호 확인",
            size: 3,
            name: "password-confirm",
        },

    ];
    </details>

    -   label: 박스 경계선 위 텍스트
    -   size: [FormInput](./summary5_FormInput.md)에 전달될 size 속성
    -   name: FormInput의 input 태그에 전달할 속성. 여기서는 실제로 쓰지는 않았음
    -   option: 태그에 따라 없을 수도 있는 부가 정보를 담은 객체

*   (2) map으로 SIGNFORM_ARRAY를 태그로 변형한다.
*   (3) [FormInput](./summary5_FormInput.md)의 props에 값을 전달한다.
*   (4) 지금 변형하는 요소에 option이 있으면 option 객체의 placeholder를 placeholder props에 전달한다.
*   (5) [TDButton](./summary6_TDButton.md) 컴포넌트를 가져온다.
*   (6) Form 태그의 스타일은 style.js를 사용한다.
