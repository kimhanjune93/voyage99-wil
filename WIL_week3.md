# WIL week3

## 1. LifeCycle (Class형 vs 함수형)

### 컴포넌트가 우리 눈에 보이는 순간부터 사라지는 순간까지를 라이프사이클이라 한다.

#### 	1) Class형 컴포넌트

- constructor() : 컴포넌트가 마운트 되기 전에 호출된다.

  - 목적 : this.state에 객체를 할당하여 현재 component의 state를 초기화한다.

    ​		,이벤트를 발생시키는 곳에 이벤트 처리 메서드를 연결하기 위함이다.

- render()

  - 유일해야 하며, 생성시 꼭 필요하다
  - 순수 함수이다. 그렇기 때문에 컴포넌트의 state를 변경하지 않고, 호출될때마다 동일한 결과를 반환해야 한다.
  - 브라우저와 직접적으로 상호작용을 하지 않는다 (DOM조작)
  - 이 때 필요한 것이 componentDidMount 같은 생명주기 메서드이다.

- componentDidMount()

  - DOM 트리에 삽입ㄱ된 직후 즉, 초기 브라우저 화면을 갱신하기 전에 호출되는 메서드이다.
  - 초기에 설정이 필요한 경우 이곳에서 작업을 한다.
  - 만약 스크롤이벤트, setInterval을 호출했다면 componentWillUnmount() 메서드를 통해 해제 작업을 해야한다.

- setState(nextState, callback) : 컴포넌트의 변경사항을 React에게 알리는 메서드로서 비동기적으로 작업을 수행하는 함수다.

  - 현재 state를 setState에서 update하려는 nextState를 이용해서 merge하는 동작을 한다.
  - merge인 이유는 현재 state를 유지하며 바뀐 부분만 update를 할 수 있기때문이다.
  - callback은 setState()의 실행이 완료되고 컴포넌트가 다시 랜더링 되고 난 이후 실행된다.
  - callback에서 다음 작업을 진행하기보다는 componentDidUpdate를 사용하길 권장한다.

- componentDidUpdate(prevProps, prevState, snapshot) : 업데이트가 일어난 직후에 호출된다.

  - 최초 렌더링시에 호출되지 않는다.
  - DOM을 조작할 때 유용하다.

- componentWillUnmount() : 컴포넌트가 웹 브라우저상에서 사라지기 전에 호출하는 메서드

  - 컴포넌트를 DOM에서 제거할 때 실핸된다.

  - 클래스 내에 초기값을 설정해서 사용한다. state값은 부모 컴포넌트에서 받은 값으로 초기화되었기때문에 클래스형 컴포넌트에서

    (예: {this,state.number(=state의 속성명)}) 로 state값을 사용할 수 있다. 또한, setState를 통해 state값을 변경할 수 있다.

    

    #### 2) 함수형 컴포넌트

- 함수형 컴포넌트에서는 배열을 return하는 내장 hook인 useState를 사용해서 state 값을 초기화한다. 또한 useState의 인자로

  부모컴포넌트로부터 전달받은 props 값을 사용한다. useState는 2개의 값을 가진 배열로 이루어져 있는데 첫번째 값은 상태값을 가지고, 두번째 값은 상태값을 변경하는 함수이다.  ( Hook 예 : let [number, setNumber] = useState("초기화"); )

  

  #### 3) hook

- React 버전 16.8 부터 React 요소로 새로 추가되었다. Hook을 이용하여 기존 Class 바탕의 코드를 작성할 필요 없이 상태값과 여러 React의 기능을 사용 할 수 있다.

- useState() 

  - [value, setValue] = useState("초기화")
  - setValue는 함수이다. 그리고 setValue(변경할값) 를 하면 value에 setValue 값이 들어간다.

- useEffect()

  - 리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 수행하도록 설정 할 수 있는 Hook 이다.

    class형 컴포넌트의 componentDidMount와 componentDidUpdate를 합친 형태로 보아도 된다.

  - useEffect(() => {

    console.log("렌더링이 완료 되었습니다.");

    });

  - 화면에 가장 처음 렌더링 될 때만 실행되고 업데이트 할 경우에는 실행 할 필요가 없는 경우에는 두번째 파라미터에

    빈배열을 넣어주면 된다.

    useEffect(() => {

    console.log("렌더링이 완료 되었습니다.");

    },[ ]);

  - 특정 값이 업데이트 될 때만 실행하고 싶을때

    useEffect(() => {

    console.log(name);

    },[ name ]);

# 2. redux-actions

#### 1) import 하기

- import { createAction, handleActions } from "redux-actions";

  import { produce } from "immer"; 

  import { setCookie, getCookie, deleteCookie } from "../../shared/Cookie";

#### 2) 액션 타입 만들기

- const GET_USER = "GET_USER";

#### 3) 액션 생성 함수 만들기

- const getUser = createAction(GET_USER, (user) => ({user}));

#### 4) initalState 만들기

- Const initialState = {

  User : null,

  is_login : false,

  }

#### 5) 리듀서 만들기(feat. immer)

- export default handleActions(  

  ​	{
  ​		[GET_USER] : (state, action) => produce(state, (dragt) => {}),

  ​	},

  ​	initialState

  );

#### 6) actionCreators 내보내기

- const actionCreators = {

  ​	getUser,

  }

  Export {actionCreators};















