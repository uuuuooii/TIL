### JWT 장단점 정리 (Cookie & Session & Token)

- JWT 인증 방식
JWT(JSON Web Token)란 인증에 필요한 정보들을 암호화시킨 JSON 토큰을 의미한다.
- JWT 기반 인증은 JWT 토근 (Access Token)을 HTTP 헤더에 실어 서버가 클라이언트를 식별하는 방식이다.
​

- JWT는 JSON 데이터를 Base64 URL- safe Encode 를 통해 인코딩하여 직렬화한 것이며, 토큰 내부에는 위변조 방지를 위해 개인키를 통한 전자서명도 들어있다.
따라서 사용자가 JWT를 서버로 전송하면 서버는 서명을 검증하는 과정을 거치게 되며 검증이 완료되면 요청한 응답을 돌려준다.


### 쿠키 / 세션 대비 장 단점
[ JWT ]

- 장점 

인증을 위한 별도의 저장소가 필요 없음.

별도의 I/O 작업 없는 빠른 인증 처리로 확장성이 우수함.


- 단점

토근의 길이가 늘어날 수록 네트워크 부하특정 토큰을 강제로 만료시키기 어려윰

​

[ Cookie & Session ]

- 장점

Cookie만 사용하는 방식보다 보안 향상 서버 쪽에서 Session 통제 가능 네트워크 부하 낮음


- 단점 

세션 저장소 사용으로 인한 서버 부하


### JWT 장점 정리

1. Header 와 Payload를 가지고 Signatur를 생성하므로 데이터 위변조를 막을 수 있다.

2. 인증 정보에 대한 별도의 저장소가 필요하다.

3. JWR는 토큰에 대한 기본 정보와 전달할 정보 및 토큰이 검증 됬음을 증명하는 서명 등 필요한 모든 정보를 자체적으로 지니고 있다.

4. 클라이언트 인증 정보를 저장하는 세션과 다르게, 서버는 무상태(StateLess)가 된다.

5. 확장성이 우수하다.

6. 토큰 기반으로 다른 로그인 시스템에 접근 및 권한 공유가 가능하다. (쿠키와 차이)

7. OAuth의 경우 Facebook, Googe 등 소셜 계정을 이용하여 다른 웹서비스에서도 로그인을 할 수 있다.

8. 모바일 어플리케이션 환경에서도 잘 동작한다, (모바일은 세션 사용 불가능)


​

[ tip ]

서버에서 가장 피해야 할 것은 데이터베이스 조회이다.

서버 자체가 죽는 경우도 있지만, 대부분 DB가 터져서 서버도 같이 죽는 경우가 허다하기 때문이다.

이런 점에서, JWT 토큰은 DB조회를 안해도 되는 장점을 가지고 있다는 점이다.

만일 payload에 유저이름과 유저등급을 같이 두고 보내면, 서버에서는 유저이름을 가지고 DB를 조회해서 유저 등급을 얻지않아도 바로 원하는 정보를 취할 수 있다.


### JWT 단점 정리

1. 쿠키 / 세션과 다르게 JWT는 토큰의 길이가 길어, 인증 요청이 많아질 수록 네트워크 부하가 심해진다.

2. Payload 자체는 암호화되지 않기 때문에 유저의 중요한 정보는 담을 수 없다.

3. 토큰을 탈취당하면 대처하기 어렵다.

​