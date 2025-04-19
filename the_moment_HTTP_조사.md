# HTTP 조사

    1. HTTP란? (HyperText Transfer Protocol의 역할)
    2. HTTP의 특징 Stateless, 클라이언트-서버 구조 등
    3. 주요 HTTP 메서드 소개 (GET, POST, PUT, DELETE 등)
    4. HTTP 상태 코드 (200, 404, 500 등)
    5. HTTP 요청과 응답 구조 (Header, Body 설명)

---

### HTTP란?(HyperText Transfer Protocol의 역할)

- 웹(WWW)에서 클라이언트(주로 브라우저)와 서버가 데이터를 주고받기 위해 사용하는 규칙(약속)이다.

- 어떤 데이터를, 어떤 방식으로, 어떤 주소로, 어떤 상태로 주고받을지를 모두 정리한 웹의 대화법 역할을 한다.

![HTTP img](https://velog.velcdn.com/images/hysperion/post/207120cb-c455-4996-a92e-64a96ad007af/image.jpg)

---

### HTTP의 특징(Stateless, 클라이언트-서버 구조 등)

- 클라이언트와 서버가 요청 및 응답을 주고받는 `클라이언트 서버 구조`
- 이전 요청과 다음 요청 사이의 상태(연결 정보)를 저장하지 않음 `Stateless(무상태)`
- 보안이 없는 텍스트 기반 통신 `암호화 없음`
- 헤더 등으로 기능 쉽게 확장 `확장성 높음`

`이 4가지 이외에도 HTTP는 다양한 특징이 있다.`

![client server img](https://images.velog.io/images/dnflekf2748/post/3ae851c0-f5a1-4b24-a9f0-00dd4d1efe2d/%EC%84%9C%EB%B2%84%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8.png)

---

### 주요 HTTP 메서드 소개 (GET, POST, PUT, DELETE 등)

- jkj