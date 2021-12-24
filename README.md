# 리액트 바벨/웹팩 설정과 용도

우선 설치를 해야할 것들이 많다.

### package.json 생성
npm init -y<br>
--> 이것은 원하는 폴더에 모듈들을 만들어준다.
### react react-dom 라이브러리 설치
npm i --save react react-dom
--> 이것은 리액트 개발에 필수적인 라이브러리다.
### 웹팩 설치
npm i webpack webpack-cli html-webpack-plugin webpack-dev-server<br>
--> 순서대로 
1. 웹팩 라이브러리를 설치한다. 
2. 웹팩을 명령어로 접근하기 위한 라이브러리를 설치한다. ( 터미널에서 웹팩을 실행이 가능하도록 해주는 기능 )
3. 웹팩이랑 에치티엠엘이 상호작용 할 수 있도록 만들어주는 플러그인을 설치한다. 
4. 웹팩이 로컬(서버)에 접근할 수 있도록 만들어주는 라이브러리를 설치한다. -> 개발용서버
### 바벨설치
이렇게 웹팩 설치는 끝났다. 이제 바벨 차례이다.<br>
npm i babel-loader @babel/core @babel/preset-env @babel/preset-react rimraf<br>
--> 순서대로
1. 웹팩이 바벨을 다룰 수 있게 만들어준다.
2. 최종적으로 컴파일을 해주는 역할을 한다.
3. 컴파일할 타겟을 잡아준다.
4. 웹팩과 리액트가 상호작용할 수 있도록 만들어준다.
5. rimraf는 윈도우와 맥에서 동일한 명령어를 가지고 폴더 삭제요청할 수 있는 기능 때문에 넣었다.
### 패키지설정
이제 기본 설치는 끝났고 pacakage.json 파일을 열어서 변경하였다.

<img width="347" alt="스크린샷 2021-12-24 오후 7 32 09" src="https://user-images.githubusercontent.com/86910922/147345232-d3362249-7772-4ba4-8b34-5f9d36e2dee4.png"> 
<span>하나하나 뜯어보면
  
  스크립트 : 명령어가 들어간다. (webpack-cli를 설치한 이유) 
  
  author, license : 임의로 넣으면 된다.
  
  디펜던시와 dev디펜던시로 나뉜다. (설치시  npm i -D ~~)
  - 특별히 다른 건 dev디펜던시는 개발시에만 사용하겠다는 의미이다.
</span>
### 웹팩 설정

이후 webpack.config.js 파일을 만들었다.
<img width="876" alt="스크린샷 2021-12-24 오후 7 43 52" src="https://user-images.githubusercontent.com/86910922/147346041-29545e2f-c380-46b2-a430-49cf61c935aa.png">

세세한 설명은 주석에 입력하였다.
엔트리에 들어간 모듈에 옵션을 적용해주는게 모듈이라는 것 그리고 최종적으로 아웃풋으로 보내진다는 것이 순서이다.

### 브라우저 설정

<img width="316" alt="스크린샷 2021-12-24 오후 8 23 17" src="https://user-images.githubusercontent.com/86910922/147348774-24b55587-09cf-4661-b181-6bd0c2dfc99a.png">

브라우저 범위가 넓으면 바벨 일이 많아지기 때문에 위처럼 설정하였다. 소스는 깃허브/브라우저스리스트를 참고하였다.


### 핫리로드

npm i react-refresh @pmmmwh/react-refresh-webpack-plugin -D으로 설치해준다.
webpack.confing.js에
devServer: {
        devMiddleware: { publicPath: "./dist" },
        static: {directory: path.resolve(__dirname, "src")},
        hot: true,
    }
를 추가해준다.
여기서 스태틱은 실제경로, 데브미들웨어는 가상경로가 되겠다.
설치한 라이브러리는 임포트 후에 플러그인즈에 장착해주면 된다.
+ options 내부에 있는 plugins: 에도 react-refresh/babel을 추가해주어야 한다.


### 실행
이후 인덱스html을 만들고 설정이 필요한 부분 설정하고 실행시키면 된다.
