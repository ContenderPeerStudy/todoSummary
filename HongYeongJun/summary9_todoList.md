# todoList 컴포넌트

## 위치

src/pages/todo/\_components/todoList.jsx

## 주변 컴포넌트

[todo.jsx](./summary7_Todo.md)  
&emsp;|||  
todoList.jsx  
&emsp;|||  
[oneTodo.jsx](./summary10_oneTodo.md)

## 기능

1. 할 일 삭제
2. 할 일 수정

## 동작 원리

### 1. return문

#### 1. return문에서 todos 배열에 map 적용

-   각 요소의 정보를 활용하여 OneTodo 태그를 작성한다.
-   (1) props 전달([props 매개변수](./summary10_oneTodo.md#1-props-매개변수))
    -   key 값: todo 요소 하나의 id
    -   todos의 요소 하나의 참조 todo
    -   [deleteTodo 함수](./summary9_todoList.md#2-deletetodo)
    -   [updateTodo 함수](./summary9_todoList.md#3-updatetodo)

### 2. deleteTodo

1. 매개변수 todoId: 이 함수가 호출된 [oneTodo](./summary10_oneTodo.md#2-onpressdeletetodo) 자기자신의 id
2. filterTodo
    - (1) todos 배열 전체 순회
    - (2) todo.id: 현재 순회하고 있는 요소의 id
    - (3) todo.id(현재 순회하고 있는 요소의 id) != todoId(함수가 호출된 컴포넌트의 아이디)를 만족하는 요소만 가져온다.
    - (4) 즉, 현재 순회하고 있는 요소가 함수가 호출된 컴포넌트의 아이디면 거른다.
3. setTodos(filterTodo)로 state인 todos 배열을 filterTodo로 변형한다.

### 3. updateTodo

1. oneTodo의 완료/수정 버튼에 걸려있는 [onPressEdit](summary10_oneTodo.md#3-onpressedit) 함수가 실행되면 updateTodo가 실행된다.
2. temp_todos에는 todo.jsx에서 받아온 todos 배열을 통째로 가져온 다음 요소별로 분해해서 빈 배열에 집어넣은 배열을 할당한다.(쉽게 말해, todos 배열을 복사한다.)
3. selectTodoIndex 변수는 지금 수정하고 있는 요소를 temp_todos 배열에서 찾아 그 인덱스를 할당받는다.
    - updateTodo를 호출한 todos 요소의 아이디와 같은 아이디를 가지고 있는 temp_todos 배열의 요소의 인덱스를 가져온다.
    -
4. 3에서 찾아온 요소를 다시 작성한다.
    - 해당 요소의 원래 값을 작성한다.
    - content는 updateTodo의 매개변수로 받아온 값으로 수정한다. (근데 이게 어떻게 가능?)
5. temp_todos에는 변경이 완료된 todos 배열이 들어있다. 이 배열로 원래 todos 배열을 수정한다.
