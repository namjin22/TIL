# HTTP 조사

    1. HTTP란? (HyperText Transfer Protocol의 역할)
    2. HTTP의 특징 Stateless, 클라이언트-서버 구조 등
    3. 주요 HTTP 메서드 소개 (GET, POST, PUT, DELETE 등)
    4. HTTP 상태 코드 (200, 404, 500 등)
    5. HTTP 요청과 응답 구조 (Header, Body 설명)

---

## 1. HTTP란?(HyperText Transfer Protocol의 역할)

![HTTP img](https://velog.velcdn.com/post-images/filoscoder/1ba8e120-174b-11ea-8bfd-dbe06624c57d/unnamed.png)

- 웹(WWW)에서 클라이언트(주로 브라우저)와 서버가 데이터를 주고받기 위해 사용하는 규칙(약속)이다.

- 어떤 데이터를, 어떤 방식으로, 어떤 주소로, 어떤 상태로 주고받을지를 모두 정리한 웹의 대화법 역할을 한다.

<br>

---

## 2. HTTP의 특징(Stateless, 클라이언트-서버 구조 등)

![client server img](https://images.velog.io/images/dnflekf2748/post/3ae851c0-f5a1-4b24-a9f0-00dd4d1efe2d/%EC%84%9C%EB%B2%84%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8.png)


- 클라이언트와 서버가 직접접 요청 및 응답을 주고받는 `클라이언트 서버 구조`

- 이전 요청과 다음 요청 사이의 상태(연결 정보)를 저장하지 않는 `Stateless(무상태)`

- JSON, 이미지, HTML 등 다양한 데이터가 전송 가능하다.

- 보안이 없는 텍스트 기반 통신으로 암호화가 없다.

- 헤더 등으로 기능 쉽게 확장할 수 있다.

`이외에도 HTTP는 다양한 특징이 있다.`

<br>

---

## 3. 주요 HTTP 메서드 (GET, POST, PUT, DELETE 등)

![Methods img](https://images.velog.io/images/yh20studio/post/c3db3a6e-6c66-4a1c-b469-d2be898f3ece/53%EB%B2%88%EC%9E%90%EC%82%B0%201911.jpg)

#### 메서드?
메서드란 컴퓨터에게 어떤 동작을 요청하는 코드(명령어)이다.

<br>

- ### GET?
  - 서버에서 데이터를 검색(요청)할 때 사용한다.

  - 주로 URL 쿼리 문자열에 붙여 보낸다. `(?key=value)`

  - 데이터를 불러오기만 하기 때문에 서버 데이터를 바꾸거나 삭제하진 않는다.

  - URL에 길이 제한이 있고 URL에 그대로 정보가 남기 때문에 보안에 민감한 정보는 보내면 안된다.

##### 예시

`GET /search?q=hello&hl=ko HTTP/1.1 Host: www.google.com`에서

`/search?q=hello&hl=ko`는 Google에서 hello를 검색하고 결과는 한국어로 보여주는 것이다.

프로토콜 버전은 `HTTP/1.1`이다.

`Host: www.google.com`는 이 요청은 구글(www.google.com)에 보낼 거야. 라는 뜻을 가진다.

그리고 `https://www.google.com/search?q=hello&hl=ko`의 URL과 같은 뜻을 가진다.

---

<br>

- ### POST?
  - GET 메서드가 서버에 데이터를 요청하는 것이였다면 POST는 서버에 데이터를 보낼 때, 새로운 데이터를 등록하거나 요청 데이터를 처리할 때 사용한다.

  - 요청 본문(body)에 데이터를 담아서 보낸다.

  - URL에 데이터가 함께 보이는 GET과 달리 URL에 데이터가 보이지 않고 body에 담기기 때문에 GET보다 보안성은 높다.

  - 보통 회원가입, 로그인, 글쓰기, 댓글 등록 등에 사용된다.

#### 예시

    POST /users HTTP/1.1
    Host: example.com
    Content-Type: application/json
    {
    "name": "Alice",
    "email": "alice@example.com"
    }
에서

`/users`는 사용자 정보를 보내서 새로운 사용자를 만들어줘! 라는 뜻이다.

`HTTP/1.1`은 사용된 HTTP의 프로토콜 버전이다.

`Host: example.com`은 이 요청을 보낼 서버의 도메인 이름이 example.com이라는 뜻이다.

`Content-Type: application/json`은 서버에게 보낼 데이터가 JSON 형식이라는 걸 알려준다.

`{
  "name": "Alice",
  "email": "alice@example.com"
}`은  서버에 보내는 데이터인 사용자의 이름과 이메일 정보를 서버에게게 알려준다.

정리하자면 `example.com` 서버의 `/users` 경로로 `POST 요청`을 보내서, 이름이 `Alice`이고 이메일이 `alice@example.com`인 `새로운 사용자를 등록`해. 라는 뜻이다.

---

<br>

- ### PUT?
  - 서버에 데이터를 보낼 때 사용되며, 기존 데이터를 완전히 덮어서 수정하거나 업데이트할 때때 사용된다.

  - POST와 똑같이 요청 본문(body)에 데이터를 담아 보낸다.

  - 클라이언트가 보낸 데이터로 해당한 리소스를 전체 업데이트한다.

  - ㅇ

  - ㅇ




URL로 어떤 리소스를 수정할지 명확히 지정해야 한다.

예: /users/123 → 123번 사용자의 정보를 이걸로 덮어써줘!

- ### DELETE?
  - 서버에 있는 데이터를 삭제할 때 사용된다.

URL을 통해 어떤 리소스를 삭제할지 지정한다.

요청 본문(body)은 없어도 되지만, 필요하다면 넣을 수 있다.

서버의 데이터를 실제로 없애기 때문에 주의해서 사용해야 한다.

여러 번 요청해도 결과는 같기 때문에 멱등성(idempotent) 을 가진다.

예: /users/123 → 123번 사용자를 삭제해줘!

- ### 그 외...
  - ㅇㅇ

---

## 4. HTTP 상태 코드 (200, 404, 500 등)

- ### 상태 코드 200
  - ㅇ

- ### 상태 코드 404
  - ㅇ

- ### 상태 코드 500
  - ㅇ

- ### 그 외
  - ㅇ


---

## 5. HTTP 요청과 응답 구조 (Header, Body)