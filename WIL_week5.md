# WIL week5

## 1. 미니프로젝트 협업

### 처음으로 프론트엔드 백엔드를 나누어 협업을 해봤다. 시작하자마자 6명의 팀원이 어색한 분위기에 모여서 미니프로젝트 주제를 결정하고 와이어프레임과 API설계를 했다. 주제는 의외로 투표시스템으로 금방 정해졌지만, 처음하는 와이어프레임과 API 설계에서 시간이 좀 오래걸렸다. 

### 와이어프레임이 먼저냐, API설계가 먼저냐가 첫 관문이였다. 일단 와이어프레임으로 틀을 잡아놓아야 API문서를 만들 수 있다 판단을 하여 와이어프레임을 먼저 그렸다. 그리고 API문서를 만들었다. 나를 포함한 프론트엔드 팀원들은 와이어프레임에 맞는 뷰를 만들고 그동안 백엔드 팀원들은 API문서를 만들면서 백엔드 구축을 했다. 아직도 잘 모르겠는건 API문서를 백엔드에서 설계를 하는건지 같이 해야하는건지 잘 모르겠다. 아무튼 아직도 나는 할줄 모르는거같아서 아쉽다. 다음 클론프로젝트때는 해봐야할것같다.

### 프론트엔드에선 와이어프레임을 보고 연관성 있는 페이지를 3등분하여 나누어갔다. 원하는 페이지를 말하고 겹치는 부분이 있어 사다리타기로 정했다. component는 element단위로 나누어 작업하기로 하였고, 각 페이지 별 필요한 element를 나열해보았다. 생각보다 겹치는 부분이 많아 또 3등분해서 나눠가서 일단 만들었다. 나중에 필요한 속성이 있으면 추가하면 되니까 일단 시작하기로 하고 element단위로 컴포넌트를 만들었다. 그 다음부터는 페이지 단위로 각자 개발을 시작했다.

### 나는 게시물들이 나오는 메인페이지와 게시물 상세페이지를 맡았다. 메인페이지에 뿌려지는 게시물 컴포넌트는 다른 팀원이 해주기로 했다. 나는 상세페이지 위주로 작업이 오래걸렸다. 그중에 댓글, 좋아요 기능이 오래걸렸던거같다. 전 프로젝트에서는 firebase를 사용한 서버리스 프로젝트였어서 ajax, axios 통신을 많이 다뤄보지 못해서 작은 에러로 밤을 새며 겨우 찾았다. POST방식에서 url파라미터로 post_id를 넘겨주고, data로 댓글 정보를 넘겨주는데 나는 이게 가능한지 모르고 자꾸 post_id를 안넘겨주고있어서 통신 에러가 떳었다.  아마 내가 api문서를 불신해서 밤을 새는 불상사가 일어난거같다. 앞으로는 더 신뢰해야겠다. <span style ="color : red">댓글추가기능을 만드는데</span> key값이 없어서 추가를 할때 id값을 임의로 redux store에 추가를 해주었다. 그렇게 만드니 추가를 하자마자 삭제가 불가능했다. 삭제를 하려면 새로고침을 하여 댓글을 다시 불러와야 가능했다.(db에있는 key값과 다르기때문) 그래서 POST요청을 보낸 후 비동기로 GET요청도 보내서 해결을 했지만 찝찝함이 가시지 않았다. 추가를 하는데 댓글창이 깜빡거렸기 때문이다. <span style="color:red">나중에 멘토링을 하면서 알게되었는데</span> POST 요청을 보내고 response로 댓글 정보를 받아오는 방법도 있다고 했다.(POST는 요청을 보내서 서버에서 처리하는 역할만 하는줄....) 댓글 추가부분 API설계가 조금 잘못된부분이였나보다.. 하나더 배워갑니다 굳.  (회고를 하며 생각해봤는데 좋아요도 댓글추가할때랑 똑같이 POST요청을 보낼때 response로 좋아요 상태를 받아오면 될거같다.)

### 아무튼 팀원들과의 불화도 없었고, 시간이 조금 부족해서 처음에 생각했던거만큼 제대로 구현하지는 못한거 같지만 좋은 성과가 나온거같아서 뿌듯한 1주간의 팀플이였다. 

- ### 아쉬웠던 점 : 백엔드 팀원들과의 소통을 많이 하지 못했다. 일단 처음부터 역할을 나눠서 하다보니 프론트는 프론트끼리 나와서 따로 대화를 하며 와이어프레임을 만들고, 돌아가봤자 다시 또 나와서 대화를 해야할거같아서 아예 나와서 따로행동을 했다. 그래서 일을하다가 막혔을때 진짜 마지막수단으로 백엔드 팀원들에게 쭈뼛쭈뼛 찾아가서 "죄송한데... ~~~ 이렇게 하는게 맞을까요 한번 확인부탁드려도 될까요...?" 이런 태도로 갔다. 물론 조심스러운 행동을 좋아하시는 분도 계셨지만 답답해하시는 분도 계셨을거같다. 아마 내가 더 명확하게 소통을 했으면 더 좋은 결과가 나왔을거같다.

- ### 뿌듯했던 점 : 잠이많던 내가 해결이 안되니까 잠이 안왔다. 나도 이제 개발자에 한걸음 다가갔다. 결국 해결하고잤다. 많은것을 질문하고 많은것을 대답해주고 엄청나게 좋은 경험이였고 많은것을 배웠다.


