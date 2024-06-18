# todo 페이지

## 위치

src/pages/todo/todo.jsx

## 주변 컴포넌트

[router.js](./summary1_file_router.md)  
&emsp;|||  
Todo.jsx <---(nav)---sign-in-form.jsx
&emsp;|||  
[TDButton.jsx](./summary6_TDButton.md), [AddTodoModal](./summary8_addTodoModal.md), [TodoList](./summary9_todoList.md)

## 기능

-   모달창이 열려있는지 확인하는 state 존재(isOpenAddTodoModal)
-   todos: 할 일을 담고 있는 객체 배열. state로 만들어 뒀으므로 변경 시 이벤트 발생
-   할 일을 생성, 조회, 수정, 삭제하는 컴포넌트가 모인 장소

## 동작 원리

### 1. isOpenAddModal

1.  기능: 모달 창이 열려있는지 알려주는 state 변수(기본값: false)
2.  작동
    -   (1) return 문의 AddTodoModal 태그는 isOpenAddTodoModal이 true여야만 작성된다. 이 state의 초기값은 false이므로 모달 창이 열리지 않는다.
    -   (2) TDButton 태그(추가)에서 onClick에 이 state를 true로 바꾸는 함수가 등록되어 있다. 따라서 이걸 누르면 (1)의 태그가 작성되어 모달 창이 열린다.

### 2. todos

1. 기능
    - 할 일을 담고 있는 객체 배열
    - 객체의 state 값이 true이면 완료, false이면 미완료
    - AddTodoModal과 TodoList 컴포넌트에 props로 todos와 setTodos가 전달된다.
2. 코드
 <details>
 <summary>todos 배열</summary>
     
     [
         {
             id: 1,
             title: "example-1",
             content: "example-1",
             state: true,
         },
         {
             id: 2,
             title: "example-2",
             content: "example-2",
             state: false,
         },
     ]
     
 </details>

### 3. CSS

1. ThemeProvider

-   (1) 의미
    -   styled-components의 기능 중 하나
    -   자주 쓰이는 CSS를 import 없이 쓰게 해준다.
-   (2) 사용법

    -   I. theme.js 파일 생성(src/libs/styles/theme.js)
    -   II. theme.js 파일에 객체를 만들고 자주 쓰는 CSS 등록

          <details>
          <summary>상세 코드</summary>
          
          ```javascript
              const COLORS = {
              primary: "#00C7AE",
              text: {
                  black : '#111111',
                  white : '#ffffff'
              },
              Gray: {
                  1: "#e9e9e9",
                  2: "#d9d9d9",
                  3: "#656565"
              }
          }

        const FONT_SIZE = {
        small: "14px",
        medium: "18px",
        large: "20px"
        }

        ```
        </details>
        ```

    -   III. 위 객체를 담은 theme 객체를 export
    -   IV. App.js에서 ThemeProvider의 theme 속성에 위의 theme 객체 집어넣기
    -   V. todo.jsx의 CSS에서 props의 theme 객체를 받아 theme 객체의 CSS 문구를 반환하게 하기

2. common.js

-   위치: src/libs/styles/common.js
-   자주 쓰는 CSS를 모아놓는 곳
-   해당 CSS를 사용할 파일에서 import 하고, 변수 형태로 common.js의 CSS 문구를 집어넣기
