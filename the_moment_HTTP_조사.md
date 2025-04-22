# HTTP 조사

    1. HTTP란? (HyperText Transfer Protocol의 역할)
    2. HTTP의 특징 Stateless, 클라이언트-서버 구조 등
    3. 주요 HTTP 메서드 소개 (GET, POST, PUT, DELETE 등)
    4. HTTP 상태 코드 (200, 404, 500 등)
    5. HTTP 요청과 응답 구조 (Header, Body 설명)

---

### 이번 조사를 통해 알게 된 다양한 개념들에 대한 정리

`클라이언트` : 서버에 요청을 보내고 서버에게 응답을 받는 쪽을 뜻한다.

`메서드` : 컴퓨터에게 어떤 동작을 요청하는 코드(명령어)이다.

<br>

## 1. HTTP란?(HyperText Transfer Protocol의 역할)

![HTTP img](https://velog.velcdn.com/post-images/filoscoder/1ba8e120-174b-11ea-8bfd-dbe06624c57d/unnamed.png)

- 웹(WWW)에서 클라이언트(주로 브라우저)와 서버가 데이터를 주고받기 위해 사용하는 규칙(약속)이다.

- 어떤 데이터를, 어떤 방식으로, 어떤 주소로, 어떤 상태로 주고받을지를 모두 정리한 웹의 대화법 역할을 한다.

<br>

---

<br>

## 2. HTTP의 특징(Stateless, 클라이언트-서버 구조 등)

![client server img](https://images.velog.io/images/dnflekf2748/post/3ae851c0-f5a1-4b24-a9f0-00dd4d1efe2d/%EC%84%9C%EB%B2%84%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8.png)


- 클라이언트와 서버가 직접 요청 및 응답을 주고받는 `클라이언트 서버 구조`

- 이전 요청과 다음 요청 사이의 상태(연결 정보)를 저장하지 않는 `Stateless(무상태)`

- JSON, 이미지, HTML 등 다양한 데이터가 전송 가능하다.

- 보안이 없는 텍스트 기반 통신으로 암호화가 없다.

- 헤더 등으로 기능 쉽게 확장할 수 있다.

`이외에도 HTTP는 다양한 특징이 있다.`

<br>

---

<br>

## 3. 주요 HTTP 메서드 (GET, POST, PUT, DELETE 등)

![Methods img](https://images.velog.io/images/yh20studio/post/c3db3a6e-6c66-4a1c-b469-d2be898f3ece/53%EB%B2%88%EC%9E%90%EC%82%B0%201911.jpg)

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

`Host: www.google.com`는 이 요청은 구글에 보낼 거야. 라는 뜻을 가진다.

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

`/users`는 사용자 정보를 보내서 새로운 사용자를 만들어줘! 라는 뜻이다.

`HTTP/1.1`은 사용된 HTTP의 프로토콜 버전이다.

`Host: example.com`은 이 요청을 보낼 서버의 도메인 이름이 example.com이라는 뜻이다.

`Content-Type: application/json`은 서버에게 보낼 데이터가 JSON 형식이라는 걸 알려준다.

`{"name": "Alice", "email": "alice@example.com"}`은 서버에 보내는 데이터인 사용자의 이름과 이메일 정보를 서버에게 알려준다.

정리하자면 `example.com` 서버의 `/users` 경로로 `POST 요청`을 보내서, 이름이 `Alice`이고 이메일이 `alice@example.com`인 `새로운 사용자를 등록`해. 라는 뜻이다.

---

<br>

- ### PUT?
  - 서버에 데이터를 보낼 때 사용되며, 기존 데이터를 완전히 덮어서 수정하거나 업데이트할 때때 사용된다.

  - POST와 똑같이 요청 본문(body)에 데이터를 담아 보낸다.

  - 클라이언트가 보낸 데이터로 해당한 리소스를 전체 업데이트한다.

  - 같은 PUT 요청을 여러 번 보내도 결과는 한 번 보낸 것과 동일하다.

#### 예시

    PUT /users/123 HTTP/1.1
    Host: example.com
    Content-Type: application/json

    {
    "name": "Alice",
    "email": "alice@example.com"
    }

`/users/123`은 `PUT`의 대상인 아이디가 123인 사용자를 뜻한다.

`HTTP/1.1`은 사용된 HTTP의 프로토콜 버전이다.

`Host: example.com`은 example.com이라는 서버로 보낸다는 뜻이다.

`Content-Type: application/json`는 요청 본문(body)의 데이터 형식이 JSON 형식이라는 걸 알려준다.

`{"name": "Alice", "email": "alice@example.com"}`은 서버에 보내는 데이터인 사용자의 이름(Alice)과 이메일 정보(alice@example.com)를 서버에게 알려준다.

정리하자면 `ID가 123`인 사용자의 정보를, 이름은 `Alice`, 이메일은 `alice@example.com`으로 `완전히` 수정해달라는 뜻이다.

---

<br>

- ### DELETE?

  - 서버에 있는 데이터를 삭제할 때 사용된다.

  - 삭제할 리소스는 URL로 명확히 지정해야 한다.

  - PUT, POST과 달리 일반적으로 본문(body) 없이 보낸다.

  - 서버의 데이터를 실제로 없애기 때문에 주의해서 사용해야 한다.

#### 예시

    DELETE /users/123 HTTP/1.1
    Host: example.com

`/users/123` DELETE 메서드의 삭제 대상을 뜻한다.

`HTTP/1.1`은 사용된 HTTP의 프로토콜 버전이다.

`Host: example.com` example.com이라는 서버로 요청을 보내겠다고 알려주는 것이다.

정리하자면 `example.com 서버`에게 `ID가 123`인 사용자를 `삭제`해주라고 요청하는 `DELETE 메서드`이다.

---

<br>

- ### 그 외...
  - 특정 부분만 수정할 때 사용하는 `"PATCH"`

  - 프록시 서버를 통해 터널을 만들 때 사용하는 `"CONNECT"`

  - 해당 리소스가 어떤 메서드를 지원하는지 물어볼 때 사용하는 `"OPTIONS"`

* `이외에도 HEAD, TRACE, PURGE, LOCK, COPY, MOVE 등 많은 메서드들이 있다.`


---

<br>

## 4. HTTP 상태 코드 (200, 404, 500 등)

![404 img](https://edgio.clien.net/F01/12204564/221a6c7811486c.png?scale=width:480)

<br>

- ### 상태 코드 200

      상태 코드 200은 클라이언트나 브라우저 등의 요청을 서버가 정상적으로 처리했다는 뜻으로 나타나는 상태 코드이다.

  - 쉽게 생각해서 그냥 요청한 작업이 성공했을 때 받는 기본적인 응답 상태 코드다.

<br>

- ### 상태 코드 404

      상태 코드 404는 클라이언트가 요청한 리소스(페이지, 파일 등)를 서버에서 찾을 수 없을 때 나타나는 상태 코드이다.

  - 사용자가 존재하지 않는 URL로 접근했을 때, 삭제된 페이지나 파일을 요청할 때, URL 오타가 있을 때 등과 같은 상황에서 주로 나타나는 상태 코드라고 생각하면 된다.

<br>

- ### 상태 코드 500
      상태 코드 500은 서버가 요청을 처리하려다가 서버에 오류(에러)가 발생해서 처리를 못했을 때 나타나는 상태 코드이다.

  - 서버에 문제가 생겨서 나오는 상태 코드지 클라이언트 요청에는 문제가 없다.

  - 데이터베이스 연결 실패 오류, 쿼리 에러, API 연동 실패, 타 시스템 연결 오류 등 상태 코드 500이 나오는 다양한 원인이이 있다.

- ### 그 외

  - 요청은 이해했지만 접근 권한이 없을 때 나타나는 `403`

  - 서버가 일시적으로 과부하 또는 점검 중일 때 나타나는 `503`

  - 요청한 리소스가 영구적으로 다른 URL로 이동했을 때 나타나는 `301`
  
  - 클라이언트의 요청으로 새 리소스가 성공적으로 생성되었을 때 나타나는 `201`

<br>

  `이외에도 다양한 상태 코드들이 있다.`

---

<br>

## 5. HTTP 요청과 응답 구조 (Header, Body)

<br>

`HTTP 요청과 응답 구조`는 클라이언트와 서버가 서로 정보를 주고받을 때 사용하는 구조를 말한다.

<br>

- ### HTTP 요청 구조 (Request)

  - HTTP 요청 구조는 클라이언트가 서버에게 무엇을 요청할 때 보내는 메시지 구조이다.

<br>


  - `요청 line(라인)`, `요청 header(헤더)`, `요청 body(본문)`으로 이루어져 있다.

.

  - `요청 line(라인)`은 요청의 핵심 정보(형식 등)를 나타낸다.

  - `요청 header(헤더)`는 요청에 대한 부가 정보인 "서버에게 누가, 어떤 형식으로, 어떤 정보를 보내는지 등"과 같은 정보를 담는다.

  - `요청 body(본문)`은 서버에 실제로 보내는 데이터(이름, 이메일 등)를 담는 부분이다.

<br>


- ### HTTP 응답 구조 (Response)

  - HTTP 응답 구조는 서버가 클라이언트 요청에 대한 답변으로로 보내는 메시지 구조이다.

<br>

  - 요청 구조와 비슷하게 `상태 line(라인)`, `응답 header(헤더)`, `응답 body(본문)`으로 이루어져 있다.

.

  - `상태 line(라인)`은 응답의 요약 결과인 사용된 HTTP 버전, 응답 상태 코드, 상태 메시지 등을 알려주는 부분이다.

  - `응답 header(헤더)`는 서버가 응답에 대한 부가 정보인 쿠키 설정, 캐시 정보, 인코딩 정보 등을 알려주는 부분이다.

  - `응답 body(본문)`는 실제로 클라이언트가 요청 했던 데이터가 들어가는 부분이다.

---

<br>

마지막으로,

쉽게 요약하자면 이런 순서로 진행된다.

    1. 사용자가 행동함

    2. 클라이언트가 요청을 보냄

    3. 서버가 요청을 처리함

    4. 서버가 응답을 클라이언트에 보냄

    5. 클라이언트가 응답 결과 보여줌

---

<br>

    이번 HTTP 조사 과제를 진행하며 HTTP에 관련된 정보를 더욱 많이 알게 된 것 같습니다.
    
    웹 서핑을 하고 ai에게 물어보고 몰랐던 것들을 정리하다보니 생각보다 분량이 많이진 것 같습니다.
    
    앞으로도 열심히 하겠습니다. 감사합니다!