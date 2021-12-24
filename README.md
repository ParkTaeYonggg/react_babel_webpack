# 리액트 바벨/웹팩 설정과 용도

우선 설치를 해야할 것들이 많다.

npm init -y<br>
--> 이것은 원하는 폴더에 모듈들을 만들어준다.

npm i --save react react-dom
--> 이것은 리액트 개발에 필수적인 라이브러리다.

npm i webpack webpack-cli html-webpack-plugin webpack-dev-server<br>
--> 순서대로 
1. 웹팩 라이브러리를 설치한다. 
2. 웹팩을 명령어로 접근하기 위한 라이브러리를 설치한다.
3. 웹팩이랑 에치티엠엘이 상호작용 할 수 있도록 만들어주는 플러그인을 설치한다. 
4. 웹팩이 로컬(서버)에 접근할 수 있도록 만들어주는 라이브러리를 설치한다.


이렇게 웹팩 설치는 끝났다. 이제 바벨 차례이다.<br>
npm i babel-loader @babel/core @babel/preset-env @babel/preset-react rimraf<br>
--> 순서대로
1. 웹팩이 바벨을 다룰 수 있게 만들어준다.
2. 최종적으로 컴파일을 해주는 역할을 한다.
3. 컴파일할 타겟을 잡아준다.
4. 웹팩과 리액트가 상호작용할 수 있도록 만들어준다.
5. rimraf는 윈도우와 맥에서 동일한 명령어를 가지고 폴더 삭제요청할 수 있는 기능 때문에 넣었다.

이제 기본 설치는 끝났고 pacakage.json 파일을 열어보자.
<img width="80%" height="300px" alt="스크린샷 2021-12-24 오후 5 00 36" src="https://user-images.githubusercontent.com/86910922/147332221-40d85a2d-d23e-47cf-a8b1-c4d658667b28.png">

사진에 보이는 스크립트s 영역은 실행명령어다. npm start로 사용하는 "start" : "webpack-dev-server --mode development"는 개발모드로 실행시키겠다는 뜻이다.

