# postBlog

- 사용 : react / redux / redux-saga / node.js / koa / mongoDB / styled-component
- 서버 : node.js / koa
- 
- 모바일 최적화
- react-moment 이용해 현재 시간 실시간으로 가져옴  

- 시계  
시침,초침,분침 / 이미지 가져와 rotate 돌리는 형식으로 구현  
rotate 각도를 현재 시간으로 구현하기위해 실시간 반영이 가능하도록 styled-component 사용    
ex)) transform : rotate (${seconds)deg);  


- 알람 구현 (setTimeout() , setAlarmWork() , localstorage)   
   알람설정창에서 입력받은 시간을 각도로 변환시켜 나타내줌   
   현재시간,알람시간을 초로 변환        

   1. setTimeout 값 ↓                                                                                                                                                     
   알람시간 - 현재시간 = 양수 >> 현재시간에서부터 알람시간 사이의 남은시간(초)   
   알람시간 - 현재시간 = 음수 >> 알람시간에서부터 현재시간 까지의 시간(초)
   현재시간 < 알람시간 // 알람시간 - 현재시간
   현재시간 > 알람시간 // 알람시간 - 현재시간 + 86400초(하루)   
   여기서 86400초를 더해주는 이유는 알고싶은 값이 알람시간에서부터 현재시간 까지의 시간(초)이 아닌 현재시간에서부터 알람시간 사이의 남은시간이므로 그 반댓값을 얻기위해 하루를 더해줌    

   2. setAlarmWork 값 ↓  
      지정된 시간에 알람이 울리면 setAlarmWork(true)  
      setAlarmWork useEffect 따로 구현해  Alarmwork(true) 일때 실행시킬 이벤트 정리  

   3. localstorage 값 ↓  
      Alarm알람시간(초) 상태로 키값 저장해 같은 시간 알람 중복안됌  
      localstorage value값은 º사용해 구분  
      ex)) 각도º오늘의 할 일º알람설정시간º알람시간(초)   
      저장한 value를 .split("º") 사용해 나눠주고 table 에 넣어 정리   


- 알람 설정 (알람음 , 음소거 , 알람 숨기기)  
   1. 알람음 설정 ↓    
      기본 알람음으로 bird.MP3 사용 
      유저가 알람음 따로 설정  
      javascript 로 사용자의 파일 절대경로 가져오는게 불가능 
      그래서 createObjectURL() 사용해 받은 오디오파일 정보를 url 로 변환시키고 해당 url 을 audio source 에 넣어서 구현   
      audio onEnded 이벤트로 오디오재생이 끝나는시점에 메모리 누수 방지를 위해 revokeObjectURL() 로 생성한 오디오 url 주소 지움   
      (페이지 새로고침하거나 나갈경우 createObjectURL()으로 생성된 url 주소는 사라짐)   
   2. 알람 음소거 ↓    
      volume 조절   
   3. 알람 숨기기 ↓    
      display:none;  





www.wakeabird.com

