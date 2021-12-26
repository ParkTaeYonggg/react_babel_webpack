# 리액트 바벨/웹팩 설정과 용도

우선 설치를 해야할 것들이 많다.

### package.json 생성
명령어 : npm init -y 
패키지.js파일을 만들어준다.

<img width="309" alt="스크린샷 2021-12-26 오후 8 50 24" src="https://user-images.githubusercontent.com/86910922/147407086-cd426f55-1c87-4284-b5f3-ec8aaf88fc8a.png">

### react react-dom 라이브러리 설치
명령어 : npm i --save react react-dom
리액트를 실행하는데 필수적인 라이브러리를 설치한다.

<img width="225" alt="스크린샷 2021-12-26 오후 8 51 42" src="https://user-images.githubusercontent.com/86910922/147407138-0856c218-6b7e-482e-94ea-8db58737df4c.png"><img width="246" alt="스크린샷 2021-12-26 오후 8 51 34" src="https://user-images.githubusercontent.com/86910922/147407140-c8ce2e57-5585-403e-8232-10c0c7505037.png">

### 웹팩 설치
명령어 : npm i webpack webpack-cli html-webpack-plugin webpack-dev-server clean-webpack-plugin @pmmmwh/react-refresh-webpack-plugin react-refresh<br>

<img width="470" alt="스크린샷 2021-12-26 오후 8 55 36" src="https://user-images.githubusercontent.com/86910922/147407287-8e136b6b-a5ad-49a2-a5d4-473b4bad705f.png">


--> 웹팩 라이브러리, 웹팩을 명령어로 접근할 수 있도록 만들어주는 cli, 로컬서버에서 활동할 수 있도록 만들어주는 devSever, html에 적용시켜서 새로운 파일을 만들어주는 html플러그인, 최신꺼 제외하고 이전 기록들은 삭제해주는 clean플러그인, 리액트 설정에 변경사항이 있을 시 자동수정 및 리로드를 해주는 핫로더를 설치해준다.


### 바벨설치
이렇게 웹팩 설치는 끝났다. 이제 바벨 차례이다.<br>

명령어 : npm i babel-loader @babel/core @babel/preset-env @babel/preset-react css-loader style-loader file-loader <br>

<img width="365" alt="스크린샷 2021-12-26 오후 9 03 00" src="https://user-images.githubusercontent.com/86910922/147407433-708ba844-a289-4024-8692-72e025810d6a.png">

--> 웹팩이 바벨을 설정할 수 있도록 만들어주는 바벨로더와 코어, 바벨이 브라우저 등의 타겟을 잡을 수 있도록 도와주는 env, 리액트와 호환을 담당해주는 preset-react, css를 모듈에 적용시켜주는 것을 도와주는 css로더 + 실제 스타일에 입히는 걸 도와주는 style로더, 이미지 등을 불러올 수 있게 해주는 file-loader를 설치해준다.

### webpack.config.js 설정

<img width="326" alt="스크린샷 2021-12-26 오후 9 09 46" src="https://user-images.githubusercontent.com/86910922/147407621-49dd46a1-6a82-47af-85f5-95feeb87667d.png">

노드를 설치하면 폴더의 경로를 잡아주는 path를 require할 수 있게 된다. 하나 선언해준다.


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

### 실행
이후 인덱스html을 만들고 설정이 필요한 부분 설정하고 실행시키면 된다.
