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

-> 노드를 설치하면 폴더의 경로를 잡아주는 path를 require할 수 있게 된다. 하나 선언해준다.

<img width="281" alt="스크린샷 2021-12-26 오후 9 13 01" src="https://user-images.githubusercontent.com/86910922/147407658-b6dad008-4bc2-4903-bcd0-525413ca6648.png">

-> 모듈을 필요한 곳에 던져줄 것이다.
모드는 개발단계이니 development로 설정해준다. -> 실제 배포시 production으로 변경해주면 된다.

<img width="329" alt="스크린샷 2021-12-26 오후 9 16 59" src="https://user-images.githubusercontent.com/86910922/147407771-78e78dca-5e40-4998-8d16-b90e49f973c3.png">

-> 리졸브로 확장자들을 붙잡아줄 수 있다. -> 여기서 설치하면 실제 임포트시 편리함.

<img width="278" alt="스크린샷 2021-12-26 오후 9 19 00" src="https://user-images.githubusercontent.com/86910922/147407802-3542ab87-0425-498c-9e1d-eb8b1cd5e24e.png"><img width="257" alt="스크린샷 2021-12-26 오후 9 19 18" src="https://user-images.githubusercontent.com/86910922/147407806-29608b24-8d04-4a1a-8f48-0d7e6ad21191.png">

-> 가장 중요한 요소중 하나인 entry를 설정해준다. -> 모듈이 하나로 모이는 지점이다. 인덱스(원하는 이름 아무거나 적어도 되고 난 index로 사용했다.) 파일을 하나 만들고 경로로 지정해준다.

<img width="549" alt="스크린샷 2021-12-26 오후 9 25 48" src="https://user-images.githubusercontent.com/86910922/147407962-d25193f2-545f-4819-b1a6-2bc81f082897.png">

-> entry의 결과물에 추가옵션을 붙이는 과정이라고 생각하면 된다. css를 읽고 적용시켜주는 css로더, 이미지나 gif등을 적용시켜주는 file로더, js혹은jsx 적용 로더와 로더에 맞는 옵션즈들을 적용시킨 결과물이다.

<img width="750" alt="스크린샷 2021-12-26 오후 9 35 57" src="https://user-images.githubusercontent.com/86910922/147408229-faf8344d-0da6-4b20-8f87-81f032d6ff28.png"><img width="515" alt="스크린샷 2021-12-26 오후 9 36 05" src="https://user-images.githubusercontent.com/86910922/147408232-99667f9a-d51a-4620-b2a7-2e4b2a2ce15f.png">

-> 이제 웹팩 플러그인들을 장착시키는 중이다. -> 조립된 html의 견본을 따서 페이지로 출력시켜주고 핫로더는 그걸 또 더 편리하게 자동화시켜준다. 그리고 클리너가 이전의 기록들을 제거해준다.

<img width="631" alt="스크린샷 2021-12-26 오후 9 42 14" src="https://user-images.githubusercontent.com/86910922/147408406-9d717dc4-9ca9-4f6d-ad80-6f0bb1d60843.png">

-> 노드로 잡아놓은 __dirname 현재 폴더에서 , 내가 임의로 지정한 폴더 위치를 지정해주고 파일네임은 entry key값이 들어갈 수 있도록 \[name] 사용해주도록 한다. 퍼블릭패스는 가상 경로가 되겠고 패스.조인이 실제경로가 될 것이다.

<img width="624" alt="스크린샷 2021-12-26 오후 9 51 23" src="https://user-images.githubusercontent.com/86910922/147408669-75b29c5d-46f5-40f9-9b08-bb5231e3dbac.png">

-> 핫로더를 위해 데브미들웨어로 가상경로 설정, 스태틱으로 실제 리로드할 경로 설정, 핫로더 트루로 설정해준다.

이렇게 하면 웹팩콘피그 설정은 끝이다.

### 에러

<img width="390" alt="스크린샷 2021-12-26 오후 10 14 05" src="https://user-images.githubusercontent.com/86910922/147409399-25f729dd-80b5-487a-abb1-c89f0dea8f73.png"><img width="387" alt="스크린샷 2021-12-26 오후 10 13 54" src="https://user-images.githubusercontent.com/86910922/147409401-ef78c720-8157-416b-9f21-e2a111763f68.png">

-> 위에서 로더 2개를 사용할 때 loader 사용 했더니 에러가 났다. use로 바꾸어서 여러 로더들을 사용할 수 있도록 변경해주었다.
-> html 폴더 경로 설정을 잘못해서 에러가 났었다. 주의하자.

### 브라우저 설정

<img width="316" alt="스크린샷 2021-12-24 오후 8 23 17" src="https://user-images.githubusercontent.com/86910922/147348774-24b55587-09cf-4661-b181-6bd0c2dfc99a.png">

브라우저 범위가 넓으면 바벨 일이 많아지기 때문에 위처럼 설정하였다. 소스는 깃허브/브라우저스리스트를 참고하였다.

### 실행
이후 인덱스html을 만들고 설정이 필요한 부분 설정하고 실행시키면 된다.
