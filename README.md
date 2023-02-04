# NexhJS introduction

library 와 framework 의 차이

library = 개발자가 라이브러리를 사용해서 무언가를함

framework는 = 개발자가 작성한 코드를 불러옴

react 에서는 내가 어떻게 컴포넌트를 나눌건지 route를 할건지 자유도가 높은폄

next.js같은 framework에서는 특정한 규칙을따라서 특정한걸 해야함 ( 그것들을 따랐을경우 모든게 정상적으로 작동함 )
framework는 코드를 어떤곳에 넣으면 framework가 그 코드르 부르는 형태임 ( 추상화 )

react.js 는 원할때 부르고 원할때 사용하는 library
next.js franmework는 코드를 적절하게 넣는 집 ( 코드가 게스트같은것이라 생각하면편함 코드를 적절하게 넣어주면 알아서 보여줌)

page의 이름작성시 파일이름으로 url이 만들어지기떄문에 신경쓸것, components의 이름은 중요하지않음 ( 중요부위는 export default ) 즉, url이름은 파일명이될것임
유저에게 보여주고싶은게있다면 pages 폴더에서 파일에 export default function 을 해줘야함

- pages 폴더안에 넣을 수 있는 예외들

1. index.js 는 기본으로 home 을 잡아줌 => http://localhost:3000/
2. jsx를 사용하고있다면 React.js를 import 해줄 필요가없음
