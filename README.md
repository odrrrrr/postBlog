# postBlog

- 프론트 : html / css / js / sass / react / redux / redux-saga
- 백엔드 : node.js / koa / mongoDB
- 로그인 , CRUD , 이미지업로드 구현
- 모바일 최적
- CORS proxy 사용
- XSS 쿠키 httpOnly , sanitizeHtml 사용
- axios 이용한 비동기 통신

   - 로그인 , 로그아웃 , 회원가입
     1.로그인
     로그인,회원가입 성공시 jsonwebtoken 이용해서 토큰 생성 후
     해당 토큰을 쿠키로 클라이언트에게 전달
     
![login](https://user-images.githubusercontent.com/83571689/143227298-490296ce-4996-408c-a77d-48c13dc5fcbc.jpg)

     2. 회원가입
     bcrypt 이용해서 단방향 해쉬함수로 패스워드 DB 저장
     회원 중복 가입 안되도록 구현
     4. 로그아웃
     store에 저장된 유저정보와 localStorage , cookies 초기화

   - 포스트
     1. 포스트 작성 , 수정 , 삭제 , 이미지 업로드
     로그인했을때만 가능하도록
     수정 및 삭제는 해당 포스터 작성자와 현재 로그인 유저의 아이디가 일치하면 되도록
     react-quill 라이브러리 사용하여 글 작성 수정 및 이미지 업로드
     이미지 업로드는 koa-multer 라이브러리 사용
     글 작성시 악성코드 넘겨줄 수 있으니 원치않는태그 ex)) <script/> 방지 하기위해 sanitizeHTML 사용해서 태그 필터
     2. 포스트 불러오기
     list 페이지(포스트 전체 불러오는)는 DB에서 포스트 정보 가져올때 200자 이상 넘으면 ... 표시해주기 (페이지당 포스트 9개만)
     특정 포스트 불러올때 쿼리로 받은 정보(태그 , 유저명)를 서버쪽에서 find(query)로 포스트들 가져옴
     3. 포스트 페이지네이션
     현재 페이지 넘버를 쿼리로 보내주고 그에 맞는 포스트들을 가져오도록
     
