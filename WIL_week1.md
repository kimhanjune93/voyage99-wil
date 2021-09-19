# WIL week1

## 1. jwt 란?
### 정의)
Json Web Token 약자로 모바일이나 웹의 사용자 인증을 위해 사용하는 암호화된 토큰을 의미합니다.<br>
JWT 정보를 request에 담아 사용자응 정보 열람, 수정 등 개인적인 작업 등을 수행할 수 있게합니다.
### 구조)
Header(헤더), Payload(내용), Signature(서명)

Header: 3가지 요소를 암호화할 알고리즘 등과 같은 옵션이 들어간다.<br>
Payload: 유저의 고유 ID 등 인증에 필요한 정보가 들어간다.<br>
Signature: Header, Payload와 Secret Key가 더해져 암호화된다.
