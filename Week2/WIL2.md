# GDSC 백엔드 스터디 2주차
### HTTP란?
HyperText Transfer Protocol   
HTML 문서와 같은 하이퍼미디어 문서를 전송하기 위한 애플리케이션 계층 프로토콜.   
<br>

### HTTP 특징
- **transfer layer**   
    TCP/IP 기반으로 서버와 클라이언트 간의 요청과 응답을 전송한다. 
    > TCP/UDP란?   
    데이터를 보내기 위해 사용하는 프로토콜.   
    TCP : 인터넷상에서 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜.   
    UDP : 데이터를 데이터그램 단위로 처리하는 프로토콜.
- **비연결성**   
    클라이언트와 서버가 한번 연결을 맺은 후에 클라이언트의 요청에 대해 서버가 응답을 마치면 TCP/IP 연결을 끊어버린다 => 최소한의 자원으로 서버 유지   
    ![img1](https://velog.velcdn.com/images/wlwl99/post/614190c0-9a42-4aee-8ca4-401dbd35fd1a/image.png)
- **무상태성**
    Connectionless로 인해 서버가 두 요청간의 어떠한 데이터도 유지하지 않는다. 즉 서버는 클라이언트와 연결에 대한 정보를 저장하지 않고, 클라이언트를 식별하지 못한다. (page1에서 만들어진 데이터는 page2를 요청할 때 유지되지 않음.)   
    <br>

    장점 : 서버 확장성이 높다.   
    단점 : 클라이언트가 추가 데이터를 전송해야 한다. (브라우저 쿠키, 서버 세션, 토큰 등을 이용해 상태 유지)   
<br>

### HTTP 연결
1. TCP 연결을 열어준다. 새연결 혹은 기존 연결을 재사용할 수 있다.
2. HTTP 메시지 전송한다.
3. 서버가 보낸 응답을 읽는다.
4. 연결을 닫거나 다른 요청을 위해 재사용한다.
![img2](https://t1.daumcdn.net/cfile/tistory/9970083359F297D62A)
<br>

### HTTP Message
HTTP Message는 서버와 클라이언트 간에 데이터가 교환되는 방식으로, 이 메세지에는 요청과 응답이 있으며, 각각 특정한 포맷을 가지고 있다.      
![img3](https://velog.velcdn.com/images/dlwoxhd/post/036c17f7-55d6-4af7-9989-b266cc5df384/image.png)   
http method, 경로, http 버전, 헤더로 이루어져 있다.
![img4](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F21282E3B554A0A1B2C)   
<br>

### HTTP Method
클라이언트가 서버에 특정 요청을 보낼때, 웹서버에게 요청하는 목적 및 그 종류를 알리는 수단으로 사용한다.
![img5](https://blog.kakaocdn.net/dn/bKPin9/btqEamE4tCi/AOHPjKmnmAEkoWrlsCMprK/img.png)
- GET : 리소스 조회
- POST : 요청 데이터 처리, 주로 등록(생성)에 사용
- PUT : 리소스를 대체, 해당 리소스가 없으면 생성
- PATCH : 리소스 부분 변경
- DELETE : 리소스 삭제   
<BR>
<br>

- HEAD : GET과 동일하지만 메세지 부분을 제외하고, 상태 줄과 헤더만 반환
- OPTIONS : 대상 리소스에 대한 통신 가능 옵션을 설명
- CONNECT : 대상 리소스로 식별되는 서버에 대한 터널을 설정
- TRACE : 대상 리소스에 대한 경로를 따라 메시지 루프백 테스트를 수행   
<BR>

### HTTP 상태 코드
서버측에서 클라이언트로 요청에 대한 응답을 보낼 때, 해당 요청에 관한 처리 상태를 알려주는 기능.
응답 코드를 통해 성공 / 실패 여부 확인.
- 1XX (informational) : 요청이 수신되어 처리중
- 2xx (successful) : 요청 정상 처리
- 3xx (redirection) : 요청을 완료하려면 추가 행동이 필요
- 4xx (client error) : 클라이언트 오류, 잘못된 문법 등으로 서버가 요청을 수행할 수 없음.
- 5xx (server error) : 서버 오류, 서버가 정상 요청을 처리하지 못함.   
<br>
<br>

- 200 : 클라이언트의 요청을 정상적으로 수행함
- 201 : 클라이언트가 어떠한 리소스 생성을 요청, 해당 리소스가 성공적으로 생성됨(POST를 통한 리소스 생성 작업 시)
- 204 : 클라이언트가 어떠한 리소스 삭제를 요청, 해당 리소스가 성공적으로 삭제됨
- 400 : 클라이언트의 요청이 부적절 할 경우 사용하는 응답 코드
- 401 : 클라이언트가 인증되지 않은 상태에서 보호된 리소스를 요청했을 때 사용하는 응답 코드
- 403 : 유저 인증상태와 관계 없이 응답하고 싶지 않은 리소스를 클라이언트가 요청했을 때 사용하는 응답 코드
- 404 : 클라이언트가 요청한 리소스에서는 사용 불가능한 Method를 이용했을 경우 사용하는 응답 코드
- 500 : 서버에 문제가 있을 경우 사용하는 응답 코드
- 502 : 게이트웨이 오류
<br>

## HTTP VS HTTPS
HyperText Transfer Protocol Secure
기본 프로토콜인 HTTP의 **보안 버전**이 HTTPS이다. HTTPS는 브라우저와 서버가 데이터를 전송하기 전에 안전하고 암호화된 연결을 설정한다. 사용자가 은행 계좌, 이메일 서비스 로그인 등 중요한 데이터를 전송할 때 특히 중요하다.   
HTTPS는 대칭키 암호화 방식과 비대칭키 암호화 방식을 모두 사용하여 빠른 연산 속도와 안정성을 모두 얻고 있다. 처음 연결을 성립하여 안전하게 세션키를 공유하는 과정에서 비대칭키를 사용하고, 이후 데이터를 교환하는 과정에서 빠른 연산 속도를 위해 대칭키가 사용된다.   
- 대칭키 암호화
    클라이언트와 서버가 동일한 키를 사용해 암호화 / 복호화를 진행함. 키가 노출되면 매우 위험하지만 연산 속도가 빠름.
- 비대칭키 암호화
    1개의 쌍으로 구성된 공개키와 개인키를 암호화 / 복호화 하는데 사용함. 키가 노출되어도 비교적 안전하지만 연산 속도가 느림.   
![img6](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcCodLU%2FbtrqRZnoOFq%2Fe6kFHjADoVby70466Jkq51%2Fimg.png)

## RESTful한 URI 설계
- 이벤트 목록 조회   
    GET /eventList
- 이벤트 조회   
    GET /event
- 이벤트 등록   
    POST /event
- 이벤트 수정   
    PATCH /event
- 이벤트 삭제   
    DELETE /event
- 이벤트 상태 변경   
    PUT /event/state
- 특정 이벤트의 주문 목록 조회   
    GET /events/{id}/orderList
- 멤버 목록 조회   
    GET /memberList
- 특정 멤버 권한 변경   
    PUT /members/{memberId}/authority
- 특정 멤버 정보 조회   
    GET /members/{memberId}/info
- 특정 멤버 정보 변경   
    PUT /members/{memberId}/info
- 멤버 등록   
    POST /members
