# oneTodo 컴포넌트

## 위치

src/pages/todo/\_components/oneTodo.jsx

## 주변 컴포넌트

[todoList.jsx](./summary9_todoList.md)  
&emsp;|||  
oneTodo.jsx

## 의미

-   todoList에서 todos 배열의 요소 하나를 변형하여 만든 컴포넌트([todoList](./summary9_todoList.md#1-return문에서-todos-배열에-map-적용))
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

-   todo.id: 자기 자신의 id([todo의 의미](./summary10_oneTodo.md#의미)
-   삭제 버튼 누르면 [deleteTodo(todo.id)](./summary9_todoList.md#2-deletetodo) 실행
