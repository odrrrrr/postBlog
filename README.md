# postBlog
      postBlog
- 프론트 : html / css / js / sass / react / redux / redux-saga
- 백엔드 : node.js / koa / mongoDB
- 로그인 , 포스트 CRUD , 이미지업로드 구현
- 모바일 최적
- CORS proxy 사용
- XSS 쿠키 httpOnly , sanitizeHtml 사용
- axios 이용한 비동기 통신

- 로그인, 회원가입
   -    
      -  로그인 , 회원가입 성공시 jsonwebtoken 이용해서 토큰 생성 후 해당 토큰을 쿠키로 클라이언트에게 전달
      -  회원가입 시 패스워드는 bcrypt 이용해서 단방향 해쉬함수로 DB 저장
      -  회원 중복 가입 안되도록 구현
     ![login](https://user-images.githubusercontent.com/83571689/143227298-490296ce-4996-408c-a77d-48c13dc5fcbc.jpg)
     ![user](https://user-images.githubusercontent.com/83571689/143230803-ee0a9f9a-8780-4a01-9fbd-a55094fa8662.jpg)

- 로그아웃
   -    
      -  store에 저장된 유저정보와 localStorage , cookies 초기화
     ![logout](https://user-images.githubusercontent.com/83571689/143228899-a9e22825-2bec-426d-ac08-0179fe229572.jpg)

- 포스트 작성
   -    
      -  로그인했을때만 글 작성 가능하도록
      -  text editor 는 react-quill 라이브러리 사용
      -  이미지 업로드는 koa-multer 사용
      -  글 작성시 악성코드 넘겨줄 수 있으니 원치않는태그 ex)) <script/> 방지 하기위해 sanitizeHTML 사용해서 태그 필터
      -  태그 기능 추가
    ![writePost](https://user-images.githubusercontent.com/83571689/143230639-3838bbad-f7fd-4bc9-ab0d-c94521e5b3ff.jpg)

- 포스트 수정 , 삭제
   -    
      -  수정 및 삭제는 해당 포스터 작성자와 로그인 유저의 아이디가 일치하면 되도록
    ![updatedeletepost](https://user-images.githubusercontent.com/83571689/143231511-592da281-87f7-424d-bedb-78b8adcae5d5.jpg)

- 포스트 불러오기
   -    
      -  포스트 페이지네이션 구현 ( 현재 페이지 넘버를 쿼리로 보내주고 페이지에 맞게 포스트들을 skip 해서 가져오도록 )
      -  첫번째 사진은 list 페이지(포스트 전체 불러오는) 는 DB에서 포스트 정보 가져올때 200자 이상 넘으면 ... 표시해주기
      -  두번째 사진은 특정 포스트 불러올때 쿼리로 받은 정보로 서버쪽에서 find(query)
    ![mainPage](https://user-images.githubusercontent.com/83571689/143232261-61717282-a685-4b46-9485-1d2f35aef210.jpg) 
    ![xmrwjdPost](https://user-images.githubusercontent.com/83571689/143232705-85719660-8f33-40a8-b8a2-e1aeab279bff.jpg)

      
   

