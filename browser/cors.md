# CORS(cross-origin-resource-sharing)

추가적인 HTTP 헤더를 이용하여 서로 다른 출처 간의 자원 공유를 허용하는 방식이다.

<br />

---

<br />

## SOP(Same Origin Policy)

브라우저는 서로 다른 출처(Scheme, Domain, Port)간의 자원 공유(....ajax)가 발생하려 할 때 그것을 막는다.

### 이유?

메일을 열었을 때 해커가 보낸 메일이 있다. 그것을 클릭했을 때 해커는 해당 링크에 유저의 메일을 도청하는 스크립트를 작성해놓았다고 가정해보자.

해커가 스크립트로 메일 서버에 요청을 보낸다면 쿠키에 저장된 사용자 정보가 함께 전송되어 인증 상으로는 문제가 없다.

하지만 브라우저 SOP 정책으로 인해 자원 공유를 막기 때문에 해커는 해당 자원에 접근할 수 없다.

### 자원 공유가 필요하다면?

- CORS 사용

## CORS 시나리오

1. simple request

   client가 요청 헤더에 origin을 첨부한다 서버의 response header의 access-control-allow-oirgin 헤더와 비교하여 다른 출처일 때 요청은 막힌다.

2. preflight request

   preflight 요청은 CORS 요청에 대한 보안 메커니즘이 없는 서버를 위해 사용된다. 특정 조건을 가지는 요청은 실제 요청에 앞서 preflight 요청을 하게 되는데 서버가 어떤 CORS 스펙을 가지는지 먼저 파악하는 과정이다.

   해당 과정에서 클라이언트의 요청이 서버의 스펙에 부합하지 않으면 요청은 막힌다.

3. credential request

   인증 정보를 포함하는 요청이다. 해당 요청에서는 클라이언트와 서버 모두 인증 요청을 표시하는 정보가 true로 설정되어야 한다.

   이때 서버는 access-control-allow-oirgin 값을 와일드카드로 설정할 수 없다.
