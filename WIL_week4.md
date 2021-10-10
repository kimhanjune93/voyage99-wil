# WIL week4

## 1. 리액트와 전역 상태 관리

### 전역상태관리란?

- 상태의 중앙 관리를 뜻한다. 

- 상태관리 도구에는 Redux, Context API가 존재한다.

- 상태관리 도구를 사용하지 않는다면 컴포넌트 간 데이터를 전달하기 위해 Prop Drilling 과정이 필요하다.

  * <b>Prop Drilling이란?</b>

    props를 하위 컴포넌트로 전달하는 용도로만 쓰이는 컴포넌트들을 거치면 Component간 데이터를 전달하는 과정이다.

    - <b>문제점</b>

      Prop 전달이 3~5개 정도의 컴포넌트라면 Prop Drilling 과정이 문제가 되지 않겠지만

      10개 정도의 더 많은 과정을 거쳐야 한다면 복잡해지고 유지보수도 어려워 질 것이다.

#### 	1) Context API

- Context API는 상태의 중앙 관리를 위한 <b>상태관리도구</b>다. React에서만 사용할 수 있고, 리덕스와 다르게 여러 저장소가 존재할 수 있다.

- Context API는 크게 전역 상태가 저장되는 context, 전역 상태를 제공하는 Provider, 전역상태를 받아 사용하는 Consumer로 나누어져 있다.

  

  ##### 1. context

   - context는 컴포넌트가 Provide한 상태가 저장된다. Consumer는 이 context를 통해 전역 상태에 접근할 수 있다.

   - 여러 context가 존재할 수 있다. 단, 하나의 context만 존재한다면 성능상 이슈가 있을 수 있다.

   - Context 안에는 Provider와 Consumer가 정의되어 있으며 다른 컴포넌트에서는 이것들을 이용해 상태에 접근한다.
   
   
   ![good](./img/스크린샷 2021-10-10 오후 7.12.33.png)
   
     

  <img src="./img/스크린샷 2021-10-10 오후 7.12.33.png" alt="스크린샷 2021-10-10 오후 7.12.33" style="zoom:50%;" align = "left" />

  

  ##### 2. Provider

  - Context에 상태를 제공한다. 즉, 다른 컴포넌트가 해당 상태에 접근하여 사용할 수 있다.

  - 제공된 상태에 접근하기 위해서는 Provider의 하위 컴포넌트에 포함되어야 한다.

  - 모든 컴포넌트에서 접근해야하는 상태를 제공하기 위해서는 <b>app.js</b> 와 같은 루트컴포넌트에서 Provider를 정의해야한다.

    

  <img src="./img/스크린샷 2021-10-10 오후 7.23.31.png" alt="스크린샷 2021-10-10 오후 7.23.31" style="zoom:50%;" align = "left"/>

  

  ##### 3. Consumer

  - Consumer는 제공된 상태에 접근하는 방법 중 하나다. context는 Consumer 사이에 있는 처음의 객체를 context에 인자로

    전달하기 때문에 바로 JSX를 작성하는 것이 아닌 빈 객체를 작성하고 나서 JSX를 작성해야 한다.

  

  <img src="./img/스크린샷 2021-10-10 오후 7.32.44.png" alt="스크린샷 2021-10-10 오후 7.32.44" style="zoom:50%;" align = "left"/>



#### 2) Redux

- Redux는 상태의 중앙 관리를 위한 <b>상태관리도구</b>다. React뿐만 아니라 Angular, Vue에서도 사용할 수 있다.

- Redux는 전역상태를 생성하고 관리하기 위한 <b>라이브러리</b>다.

- Redux는 크게 전역 상태를 보관하는 <b>저장소</b>, 상태 저장소에 접근을 위한 <b>리듀서</b>, 리듀서에 행동을 지시하는 <b>액션</b>,

  저장소에 보관된 상태를 가져오는 <b>서브스크립션</b>으로 나뉘어져 있다.

  

  ##### 1. Store

  - 전역 상태를 저장한다.

  - 자바스크립트 객체 형태로 저장되어 있어며 리듀서를 통하지 않고 접근할 수 없다.

  - 하나의 어플리케이션에 하나의 저장소만 존재해야 한다.

  - 리액트에서는 주로 <b>index.js</b>에 정의한다.

  - 저장소가 하나이기 때문에 리듀서 또한 하나로 존재해야 한다.

  - immutable하다는 특성을 가진다.

    

  <img src="./img/스크린샷 2021-10-10 오후 10.46.45.png" alt="스크린샷 2021-10-10 오후 10.46.45" style="zoom:50%;" align = "left"/>

  

  ##### 2. Reducer

  - 저장소에 유일하게 접근할 수 있는 유일한 객체다.

  - 들어오는 action에 따라 행동한다.

  - 리듀서 함수 내에서 반환되는 값이 상태 저장소에 저장된다.

  - 상태가 추가되는 것이 아닌 덮어씌워지게 되므로 전체 상태를 복사하여 상태를 갱신한 후 반환해야 한다.

    ex) 저장소에 {count : 1, price : 100} 이 저장되어 있는 상태에서 리듀서가 {count : 2}를 반환하면 저장소에는 {count : 2}가 저장된다.

    

    <img src="./img/스크린샷 2021-10-10 오후 10.51.52.png" alt="스크린샷 2021-10-10 오후 10.51.52" style="zoom:50%;" align = "left"/>

  <img src="./img/스크린샷 2021-10-10 오후 10.48.50.png" alt="스크린샷 2021-10-10 오후 10.48.50" style="zoom:50%;" align = "left"/>

  

  ##### 3. Action

  - 액션은 리듀서에게 보내지는 저장소에 대한 행동이다.
  - 리듀서는 Action에 따라 저장소에 접근하여 정해진 동작을하게된다.
  - 트리거(trigger) 역할이라고 볼 수 있다.

  <img src="./img/스크린샷 2021-10-10 오후 10.50.01.png" alt="스크린샷 2021-10-10 오후 10.50.01" style="zoom:50%;" align = "left"/>

  

  ##### 4. configurationStore

  - rootReducer : combineReducers로 reducer들을 한개로 모은다.
  - thunk로 비동기 작업 처리하는 미들웨어를 만든다.(필요시에)
  - const enhancer = composeEnhancers(applyMiddleware(...middlewares));  : 만든 미들웨어들을 enhancer로 모은다.
  - reducer들과 미들웨어들을 createStore로 store을 구성한다.

  <img src="./img/스크린샷 2021-10-10 오후 10.55.31.png" alt="스크린샷 2021-10-10 오후 10.55.31" style="zoom:50%;" align = "left"/>

## 2. css라이브러리와 리액트

	### 	css in js 라이브러리를 사용한다

- ### css in js 란?

  - CSS를 구성 요소를 추상화하고 JavaScript를 사용하여 선언적이고 유지 관리 가능한 방식으로 스타일 한다.

  - Styled-components, Emotion, JSS, Apthrodite 등이 존재한다.

- ### styled-components 사용법

  - 패키지 설치

    <img src="./img/스크린샷 2021-10-10 오후 11.16.28.png" alt="스크린샷 2021-10-10 오후 11.16.28" style="zoom:50%;" align = "left"/>

  - Styled-components로 element component구성

    <img src="./img/스크린샷 2021-10-10 오후 11.20.28.png" alt="스크린샷 2021-10-10 오후 11.20.28" style="zoom:50%;" align = "left"/>

    - styled를 import
    - 함수 선언 (다른 컴포넌트에서 "<Text/>" 이런식으로 사용할 이름으로 )
    - 원하는 요소의 스타일을 styled.요소 "백팁" 안에 스타일을 추가
    - defaultProps로 props로 받아오는 값의 초기값을 준다.



