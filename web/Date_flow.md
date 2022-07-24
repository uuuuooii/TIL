## Date flow
프론트엔드 개발자가 실수하는 것 중에 가장 큰게 데이터다.
![이미지](/image/KakaoTalk_Photo_2022-07-21-23-32-24.jpeg)

---
## 유저 시나리오

[ 공통 ]

- 메인 페이지에 접속할 수 있어야 한다.

- 로그인을 할 수 있어야 한다.

- 회원가입을 할 수 있어야 한다.

- 메뉴가 노출되어야 한다.

비회원

회원 

구매 회원

어드민 (어드민(admin)은 관리자를 의미하는 어드미니스트레이터(administrator)의 줄임말)

​

[ 메뉴 ]

- 카테고리 버튼이 보여야 한다.

- 카테고리 버튼에 마우스를 올리면 메뉴가 확장된다.

- 최신 혹은 어드민이 지정한 메뉴가 상단에 노출되어야 한다.

    - 어드민이 지정한 메뉴 : XXX API를 호출하면 된다.

    - 메뉴는 어드민이 n일에 한번씩 변경한다.

- 메뉴는 메인메뉴와 서브메뉴가 존재한다.

    - 메인 메뉴는 언제나 노출된다.

    - 서브메뉴는 메인 메뉴에 묶여있는 그룹에 한해서 노출된다.

- 강의 전체보기를 클릭하면 강의 목록으로 넘어간다.

​

[ 배너 ]

- 어드민에서 지정한 배너가 상단에 노출되어야 한다.

    - 배너는 5초마다 자동으로 롤링된다. (상수)

​

[ 강의 목록 ] 

- 특정 옵션의 강의 목록이 노출되어야 한다.

    - 특정 옵션 : 태그, 카테고리, 신규 런칭

- 타입

    - 목록형

    - 슬라이드형 

- 강의 데이터

    - 썸네일 

    - 태그

    - URL

​