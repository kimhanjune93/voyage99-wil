# WIL week2

## 1. React 프로젝트 시작

### 1) node 설치

- 구글에 nodejs 검색해서 공식사이트 들어가기
- LTS버전 확인
- 터미널에서 프로젝트 생성할 폴더까지 cd 명령어로 들어가기
- "nvm install 버전" 입력해서 node 설치
- nvm ls 로 노드가 깔렸는지 확인(방금 설치한 노드 버전이 나오면 설치확인 끝)

### 2) yarn 설치

- 터미널에 "npm install -g yarn" 입력 ( '-g' 는 global의 약자로 전역에 설치)
- yarn -v 로 설치/버전 확인

### 3) yarn으로 CRA(create react app) 설치

- CRA란? react로 웹을 만들기위한 모든걸 갖고있는 패키지.
- 터미널에 "yarn add global create-react-app" 입력

### 4) CRA 사용하여 프로젝트 만들기

- 터미널에 "yarn create react-app 프로젝트명" (프로젝트 만들고싶은 경로에서 입력해야함.)

  ** 나는 여기서 프로젝트 생성이 되지 않아서 npx를 사용해 프로젝트를 생성했다.

  - npm uninstall -g create-react-app

    yarn global remove create-react-app

    yarn cache clean

    npm uninstall -g yarn

    명령어로 CRA와 yarn을 지웠다.

  - 터미널에 "npx create-react-app 프로젝트명" 을 입력하니까 생성이되었다.

- 터미널에 cd 명령어로 생성한 프로젝트 경로로 들어가준다.

- 프로젝트 경로 안에서 "npx start"를 입력하면 localhost:3000 주소로 웹사이트가 열린다.

## 2. 서버리스

- 서버리스는 백엔드리스가 아니다.(내가 인프라 작업을 직접 할 필요가 없다는 뜻.)
- 서버사양, 네트워크 설정 등 미리 만들어져있는 서버를 빌려쓰는것.
- db작업 즉, 데이터를 사용하기 쉽게 이쁘게 만드는 작업도 서버의 역할인데 이 작업도 해준다.
- Firebase를 사용하는것도 위에 이유라고 한다.

## 3. DOM(문서객체모델)

- DOM은 트리구조다.(예: document, document.head, document.body)
  - document와 head, body는 부모 자식관계다.
  - head와 body는 형제관계이다(sibling)
- tag는 <> </>이고 <div><button> 등은 요소라고한다.

## 4. 라이프사이클

### 정의)

컴포넌트가 우리 눈에 보이는 순간부터 사라지는 순간까지를 라이프사이클이라 한다.

![스크린샷 2021-09-26 오후 8.45.23](/Users/kim/Desktop/스크린샷 2021-09-26 오후 8.45.23.png)

- 컴포넌트는 생성되고, 수정되고, 사라진다.

- '생성'은 컴포넌트를 불러오는 단계다.

- '수정'되는 경우

  - props가 바뀔 때
  - state가 바뀔 때
  - 부모 컴포넌트가 리렌더링 될때
  - 강제로 업데이트 했을때(forceUpdate()를 통해 컴포넌트를 강제로 업데이트 가능)

- '제거'는 페이지를 이동하거나, 사용자의 행동(삭제버튼 등)으로 인해

  컴포넌트가 화면에서 사라지는 단계

#### 가상돔이란?

- DOM은 html 단위 하나하나를 객체로 생각하는 모델이다. DOM트리중 하나가 수정될 때마다

  모든 DOM을 뒤지고 수정을 한다면 필요없는 연산이 너무 많이일어난다

  그래서 가상돔이 필요하다.

- 가상돔은 메모리상에서 돌아가는 가짜 DOM이다.

- 기존 DOM과 어떤 행동 후 새로 그린 DOM(가상돔)을 비교해서 바뀐 부분만 갈아끼운다.

  (돔 업데이트 처리가 간결하다.)

- 사이트 구조에따라 DOM 이 빠를수도 있고 가상돔을 사용하는것이 빠를수도 있다.

## 5.리덕스

## 								  상태관리 흐름

<img src="/Users/kim/Desktop/스크린샷 2021-09-23 오후 8.59.13.png" alt="스크린샷 2021-09-23 오후 8.59.13" style="zoom:50%;" />

### 1) State

- store에 있는 data

### 2) Action

- dispatch를 할때 무엇* 을 수정해줘 할때 그 무엇*이 Action이다.

### 3) ActionCreator

- Action을 만드는데 쓰는것.

### 4) Reducer

- 실제로 state를 수정하는 곳.

### 5) Store

- 구독을 한 노드에 data가 바뀌었다고 알려주는 곳.

### 6) dispatch

- 수정을 해달라고 요청을 하는 것
- state는 바로 수정이 불가능하다 (ex: state=1 X)



