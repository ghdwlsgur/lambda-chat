![image](https://user-images.githubusercontent.com/77400522/163090728-32af11bc-0a1b-4f49-a034-9a7b0d15dca3.png)

# API Gateway

- API 형식으로 AWS 서비스에 접근할 수 있도록 해주는 서비스

- REST API

  > - Lambda를 HTTP 프로토콜 기반의 REST API로 호출

- WebSocket
  > - Websocket 프로토콜로 Lambda를 호출
  > - Websocket으로 붙을때 `ConnectionID`를 부여
  > - `ConnectionID`로 구분된 클라이언트에 메시지 전송 가능

# Lambda

- Serverless 기반으로 코드를 실행할 수 있는 서비스
- 총 4개의 Lambda

### 웹소켓 연결

> - `ConnectionID`를 DynamoDB(유저목록)에 저장

### 웹소켓 연결 해제

> - `ConnectionID`를 DynamoDB(유저목록)에서 삭제

### 채팅 입력

> - `DynamoDB(채팅)`에 채팅 내용 기록
> - 해당 방에 `ConnectionID`를 DynamoDB에서 불러와 채팅 내용을 API Gateway Websocket을 통해 전달

### 채팅 가져오기

> - DynamoDB(채팅)에서 채팅 내용을 가져오기

# DynamoDB

- Key-Valud 기반의 완전관리 DocumentDB
- Serverless
- 총 2개의 테이블
  > - 채팅 메시지: 채팅 내용을 저장
  > - 유저 목록: 채팅방에 접속된 유저들의 ConnectionID를 저장

# S3(Simple Storage Service)

- 객체 스토리지 서비스
- Static Web Hosting (정적 웹 호스팅 가능)
