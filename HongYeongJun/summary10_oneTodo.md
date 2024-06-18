# oneTodo 컴포넌트

## 위치

src/pages/todo/\_components/oneTodo.jsx

## 주변 컴포넌트

[todoList.jsx](./summary9_todoList.md)  
&emsp;|||  
oneTodo.jsx

## 의미

-   oneTodo는 todoList에서 todos 배열의 요소 하나를 변형하여 만든 컴포넌트([todoList](./summary9_todoList.md#1-return문에서-todos-배열에-map-적용))
-   todo 매개변수의 의미: oneTodo 자기 자신을 가리키는 참조

## 기능

1. 할 일 하나 표현
2. 할 일 삭제
3. 할 일 수정

## 동작 원리

### 1. props 매개변수

-   todo: todos 배열의 요소 하나
-   [deleteTodo 함수](./summary9_todoList.md#2-deletetodo)
-   [updateTodo 함수](./summary9_todoList.md#3-updatetodo)

### 2. onPressDeleteTodo

-   todo.id: 자기 자신의 id([todo의 의미](./summary10_oneTodo.md#의미))
-   삭제 버튼 누르면 [deleteTodo(todo.id)](./summary9_todoList.md#2-deletetodo) 실행

### 3. onPressEdit

1. 수정이 끝나고 수정 사항을 반영하는 과정이므로 isEditMode를 false로 바꾼다.
2. updateTodo()를 실행한다. 매개변수는 다음과 같다.

-   todoId: 지금 순회하고 있는 컴포넌트 자기 자신의 id
-   content
    -   contentRef에는 return의 [textarea](summary10_oneTodo.md#5-return-문) 태그가 들어가 있다.
    *   content 매개변수에는 이 textarea의 내용(즉, 수정할 할 일)이 들어간다.

### 4. onPressChangeEditMode

-   isEditMode 상태를 true로 바꾼다.

### 5. return 문

1. S.Wrapper의 state는 아래의 S.Wrapper CSS와 연계된다.
2. todo 요소의 state가 true(완료)이면 텍스트를 완료로, false(미완료)이면 텍스트를 미완료로 작성한다.
3. 완료/수정 버튼
    - isEditMode 상태가 true(수정 중)이면
        - 텍스트는 완료로 작성
        - onClick 함수는 [onPressEdit](./summary10_oneTodo.md#3-onpressedit)이 된다.
    - false(수정 안 하고 있음)이면
        - 텍스트를 수정으로 작성한다.
        - onClick 함수는 [onPressChangeEditMode](./summary10_oneTodo.md#4-onpresschangeeditmode)가 된다.
4. 삭제 버튼은 [onPressDeleteTodo](./summary10_oneTodo.md#2-onpressdeletetodo)를 발동한다.
5. isEditMode가 true(수정 중)이면 textarea 태그를, 아니면 S.Content(일반 div) 태그를 작성한다.
    - textarea의 속성
        - ref
            - ref는 jsx에서 제공하는 태그 속성이다.
            - ref에는 useRef로 만든 변수가 들어간다. 이 속성 안에 ref 변수를 등록하면 리액트에서 이 태그를 등록된 ref 변수 안에 집어넣는다.
            - textarea 태그는 이제 rerender 후에도 변하지 않는다.
        * default value에는 [todos 요소](summary7_Todo.md#2-todos)의 현재 content 값이 들어간다.
    * S.Content에는 완료/미완료 정보가 담긴 todo.state가 들어간다.
