# Main 페이지

## 기능

-   SIGN-IN을 누르면 로그인 탭이, SIGN-UP을 누르면 회원가입 탭이 표시된다.
-   선택된 탭은 회색으로 색이 변한다.

## 동작 원리

### 1. state 등록

-   useState로 선택된 탭을 관리할 state 등록(formState, setFormState)

### 2. 탭 배열 생성

-   TAB_ARRAY에는 추가될 탭의 정보가 저장됨(이름 등)

### 3. 탭 태그 생성

-   TAB_ARRAY.map으로 2번 배열을 변형하여 탭 태그의 형태로 바꾼다.

    -   props
        -   key: ??
        -   $isSelected: formState와 TAB_ARRAY의 tab.name 비교. 같으면 true 반환
        -   onClick: 클릭 시 handlePressSignTab(tab.name) 함수 작동. map 함수 작동 시점에서 이미 매개변수는 탭 이름으로 지정
    -   내부 텍스트: tab.name으로 지정

### 4. handlePressSignTab(tab.name) 함수

-   매개변수: 선택된 탭 이름
-   역할: setFormState 함수 작동
-   주의:console.log(formState) 찍어보면 formState가 제대로 찍히지 않는다. 이유는?

### 5. 컴포넌트 가져오기

-   formState가 "SIGN-IN"이면 SignInForm을, 아니면 SignUpForm을 가져온다.

### 6. S.Tab CSS

-   props: 이걸 이름 바꿔도 작동하는 이유는?
    -   추정: styled-components 변수 안에 함수를 적으면 매개변수는 자동으로 props가 되나?
-   props 객체 안의 $isSelected가 true이면 `background-color: #회색` 반환
