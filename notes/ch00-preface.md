# Ch0. 들어가기 전에 - 0-04 이 책을 읽기 전에

출처: [점프 투 스프링부트 위키독스](https://wikidocs.net/160032)

---

## 📌 본문 일부
`**폼(form)에 대한 지식**
  브라우저가 서버에 요청을 보낼 때 사용하는 **GET, POST 방식의 차이**를 알고 있다면 OK.`

---

## ❓ 질문
> Q. 위의 본문에서 *폼(form)*이 정확히 뭔가요?
> 제가 아는 폼은 프론트 수업에서 배운 설문조사 폼 같은 프로젝트에서 사용한 `<input>` 태그들 밖에 없는데요!

---

## ✅ 답변 정리
### 폼(form)이란?
- HTML에서 `<form>` 태그로 감싼 입력 영역을 **폼(form)**이라고 한다.
- 즉, **사용자가 입력한 데이터를 서버로 보내기 위한 영역**이다.

### 예시
```html
<form action="/signup" method="POST">
  <input type="text" name="username" />
  <input type="password" name="password" />
  <button type="submit">회원가입</button>
</form>
```

- `action="/signup"` → 이 폼 데이터를 보낼 서버 주소
- `method="POST"` → 데이터를 보낼 방식 (`GET` 또는 `POST`)

### GET vs POST

- **GET**
    - 주소(URL)에 쿼리스트링(`?username=abc&password=123`)으로 붙여서 전송
    - 데이터가 **노출됨**
- **POST**
    - 요청 본문(body)에 담아 전송
    - 주소창에는 **노출되지 않음**

즉, 설문조사 같은 input 묶음도 결국 다 서버로 데이터를 제출(submit)하기 위한 폼임

---
