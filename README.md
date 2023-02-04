# NexhJS introduction

// 노마드코더 NextJs 사용하기 1 - 0 library와 framework의 차이 설명

library 와 framework 의 차이

library = 개발자가 라이브러리를 사용해서 무언가를함

framework는 = 개발자가 작성한 코드를 불러옴

react 에서는 내가 어떻게 컴포넌트를 나눌건지 route를 할건지 자유도가 높은폄

next.js같은 framework에서는 특정한 규칙을따라서 특정한걸 해야함 ( 그것들을 따랐을경우 모든게 정상적으로 작동함 )
framework는 코드를 어떤곳에 넣으면 framework가 그 코드르 부르는 형태임 ( 추상화 )

react.js 는 원할때 부르고 원할때 사용하는 library
next.js franmework는 코드를 적절하게 넣는 집 ( 코드가 게스트같은것이라 생각하면편함 코드를 적절하게 넣어주면 알아서 보여줌)

// 노마드코더 NextJs 사용하기 1 - 1 nomad Pages에 들어갈수있는 예외들

page의 이름작성시 파일이름으로 url이 만들어지기떄문에 신경쓸것, components의 이름은 중요하지않음 ( 중요부위는 export default ) 즉, url이름은 파일명이될것임
유저에게 보여주고싶은게있다면 pages 폴더에서 파일에 export default function 을 해줘야함

- pages 폴더안에 넣을 수 있는 예외들

1. index.js 는 기본으로 home 을 잡아줌 => http://localhost:3000/
2. jsx를 사용하고있다면 React.js를 import 해줄 필요가없음

// 노마드코더 NextJs 사용하기 1 - 2 react-CSR, next-SSR 설명

next.js의 가장 좋은 기능중 하나는 앱에 있는 페이지들이 미리 렌더링되는것임 ( 정적으로 생성됨 )

cra 와 next.js 의 차이점은
cra는 client-side-render를 하는 앱을 만든다는것임
client-side 는 내가 만든 브라우저가 사용자가 보는 UI를 만드는 모든것을 한다는것을 의미함

브라우저가 자바스크립트를 가져와서 client-side의 자바스크립트가 모든 UI를 만든다는것 ( 왜냐하면 사용자가 볼수있는것든 <div id="root"><div> 비어있는 루트 하나이기때문에 )
index.js에서 자바스크립트가 없을경우는 <noscript>가 보여지고 있다면 작동된 script를 따라서 javascript 가 보여짐

1. 브라우저가 HTML을 가져올때 비어있는 div로 가져옴
2. 그 후에 모든 JavaScript 를 요청해서
3. 브라우저가 JavaScript 와 react.js를 실행시키고
4. 그 후에 앱이 사용자에게 보여지게됨 ( UI를 만듬 )

react와 next 의 차이점은 client-side-render 와 server-side-render이다

react에서 느린 인터넷으로 api를 요청할경우 빈화면이 보여지고 fetch등을 만나 통신후에 그려지게되는데 이 과정중에 빈화면이 보여지는 처리를 안했다면 빈화면이 필수적으로 보여지게된다
next는 server-side-render라서 느린 인터넷으로 api를 요청할경우 data를 불러오는 구역을 제외하고 기본 HTML등은 받아와 미리 렌더링 시켜 HTML파일등을 볼수있게해줌

react = 빈화면 ( 빈 root ) => 자바스크립트( App.js 등 , fetch 데이터등 )
next = HTML( html를 미리 받아와서 렌더링 ) => 자바스크립트 ( fetch 데이터등 )

next.js는 새로고침을 하면 앱의 초기상태를 활용해서 미리 렌더링을 해옴 ( next.js는 초기상태로 pre - rendering 를 함 )

1. next.js는 react.js를 백엔드에서 동작시켜서 이 페이지를 만드는데 index.js에서 function Home 컴포넌트들을 렌더시킴
2. 렌더링이 끝났을경우 그건 HTML이 되고 next.js는 그 HTML을 페이지의 소스코드에 넣어줌
3. 그럼 사용자는 자바스크립트와 react.js가 로딩되지 않았더라도 콘텐츠를 볼수있게됨
4. 그리고 react.js가 로딩되었을때 기본적으로 이미 존재하는것들과 연결되어 일반적인 react.js 앱이 됨 ( 두방면에서 좋다고함 )

- 사용자가 웹사이트에 가면 초기 상태의 component로 미리 생성된 HTML페이지를 보게되고
- 상호작용이 일어날 경우 react.js는 그걸 받아서 동작하게해줌
- 자바스크립트 작동을 중지허다러다도 react.js의 기능이 동작이 하지않지만 HTML을 보여줄수있음
  위와같은 이유 때문에 SEO에 정말 좋다고함 ( 구글 검색엔진같은경우에도 사용자에게 너무 좋음)
- 사용자가 나의 웹사아트에 들어오게되면 이미 무언가가 있는다는것 ( 사용자가 코드를 다운받아 react를 실행시키기를 기다리지않아도됨 )
- 모든게 다 로딩된다면 react.js가 연결되어서 원하는 모든것을 가능하게해줌

// 노마드코더 NextJs 사용하기 1 - 3 next.js에서 새로고침없이 route 시켜주는방법

next.js 에서의 eslint에서 a태그를 사용하지말라고함
이유는 route로 이동시 새로고침이 일어나 느려지게하기떄문임

Link는 우리에게 Next 애플리케이션의 클라이언트 사이드 네이게이션을 제공해줌

// 이전
<a href="/">Home</a>

// 이후

<Link  href="/">
  <a>Home</a>
</Link>
위와 같은 코드 작성시 아래의 오류가 나옴  legacyBehavior 추가할경우 해결됨

Invalid <Link> with <a> child. Please remove <a> or use <Link legacyBehavior>.

// 노마드코더 NextJs 사용하기 1 - 4 Next.js 어플리케이션에 css를 추가하는 방법 1편

Next.jsdp style 를 추가하는방법

1. inline CSS
2. module.css = CSS모듈 패턴사용하기

- 일반적인 css방법을 사용하지만 일반적인것과 틀린점은 className로 NavBar.module.css 에 적인 .nav 가 아닌 className={styles.nav} css모듈을 불러와 변수처럼 사용함
- 요소를 살펴볼경우 className이 무작위 글자로 바껴서 에러가 나오지않음 ( className 의 충돌이 없음 )
- 두가지 이상의 className을 사용해야할경우 백틱으로 사용하는방법과 배열로 사용하는방법등이 있음 ( a태그의 밑줄없애기 , a태그의 색상변화 )

/\*

.link {
text-decoration: none;
}
.active {
color: tomato;
}

\*/
module.css CSS모듈에 위의 코드를 붙여놓고

1.  백틱의 경우
    className={`${styles.link} ${
  router.pathname === "/" ? styles.active : ""
}`}
2.  배열의 경우
    className={[
    styles.link,
    router.pathname === "/about" ? styles.active : "",
    ].join(" ")}

// 노마드코더 NextJs 사용하기 1 - 5 Next.js 어플리케이션에 css를 추가하는 방법 2편

Next.jsdp style 를 추가하는방법

3. styled jsx - NextJs 고유의 방법

<style jsx>{`
        nav {
          background-color: tomato;
        }
        a {
          text-decoration: none;
        }
      `}</style>

styled jsx는 오직 같은 컴포넌트 내부의 범위만 한정함
