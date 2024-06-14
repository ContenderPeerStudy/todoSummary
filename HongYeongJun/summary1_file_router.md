# todolist 파일 생성, router 생성

## 1. 준비

1. react-app 생성
2. 폴더 구조 생성
3. main.jsx 생성

    - 위치: pages-main
    - 내용물: 지금은 main만 넣기

4. todo.jsx 생성

    - 위치: pages-todo
    - 내용물: 지금은 todo만 넣기

## 2. router 생성

1. react-router-dom 설치
2. router.jsx 생성
    - 위치: libs-routes
    - 내용물: 주소에 따라 보여줄 페이지 결정
3. createBrowseRouter 함수 안에 다음과 같은 객체 배열 생성
    - ```javascript
        {
        path: "/", //주소명
        element: <Main></Main>,//컴포넌트 태그
        }
      ```
4. App.js 반환값: <RouterProvider router={3번 router 이름}/>
