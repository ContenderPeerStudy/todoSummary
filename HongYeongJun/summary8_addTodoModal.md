# 모달창

## 위치

-   src/pages/todo/\_components/addTodoModal.jsx

## 주변 컴포넌트

[Todo.jsx](./summary7_Todo.md)  
&emsp;|||  
addTodoModal.jsx  
&emsp;|||  
[TDButton](./summary6_TDButton.md)

## 기능

-   추가 버튼을 누르면 Modal 창이 뜸
-   x 버튼을 누르면 Modal 창이 그냥 닫힘
-   추가 버튼을 누르면 todolist에 항목이 추가되며 Modal 창이 닫힘

## 받는 props

-   setIsOpenAddTodoModal
-   todos
-   setTodos

## 동작 원리

### 1. onPressAddTodo

1. 발동 조건: Form 제출
    - 추가 버튼이 Form 태그 안에 있고 따로 type을 지정하지 않았으므로 자동으로 제출 버튼이 된다.
2. newTodo 객체
    - id: 랜덤한 값, 겹침 방지
    - title과 content: 제출 받은 form의 value
3. setTodos([...todos, newTodo])
    - ...todos: 위에서 받아온 todos 배열을 전개 연산자로 setTodos 안의 배열에 펼쳐 넣는다. (기존 할 일)
    - newTodo: 위에서 만든 새 할 일.
    - todo.jsx에 상태로 등록되어 있는 todos를 할 일이 추가된 배열로 바꾸는 함수
4. 가져온 setIsOpenAddModal 함수로 모달창을 닫는다.

### 2. return 문

1. x 버튼: onClick에 가져온 setState 함수를 걸어서 누르면 창이 닫히도록 한다.
