## ✏️ 개발 서버 실행과 빌드

#### npm 사용을 위해 
  ~~~bash
  npm init -y

  npm install parcel-bundler -D
  npm install lodash
  ~~~

- package lock.json, pakage.json은 지우면 안 되는데, node_modules는 지워도 됨 
  - npm i 로 살리면 돼서


#### 개발용 의존성 패키지 설치
  - 개발할 때만 필요하고 웹 브라우저에서는 동작할 필요없음
  ~~~bash
  $ npm install -D xxx
  ~~~

#### 일반 의존성 패키지 설치
  - 웹 브라우저에서도 동작할 수 있는 것
  ~~~bash
  $ npm install xxx
  ~~~

#### parcel index.html (서버 켜기)
  - 로컬 환경에서 개발용으로 서버를 열겠다. 서버를 접근을 해서 내가 만든 프로젝트를 브라우저에서 확인을 하겠다.
    ```
    - pakage.json
    "scripts": {
      "dev": "parcel index.html",         // 개발용
      "build": "parcel build index.html"  // 사용자용
    }

    - bash 
      // 개발용 실행
      $ npm run dev

      // 종료
      control C 

      // 사용자용 실행
      $ npm run build   -> dist 폴더 생성됨
    ```

- 오류 났던 부분
  - 새로운 노드 버전을 적용하면 다시 빌드해야된다.
    ~~~bash
    // 오류 
    ➜  test npm run dev    

    > test@1.0.0 dev
    > parcel index.html
    /Users/sa/Desktop/test/node_modules/bindings/bindings.js:126
      err = new Error(
            ^
    Error: Could not locate the bindings file.


    // 해결
    ➜  test nvm use 12.14.1              
    ➜  test npm rebuild node_modules 
    ➜  test npm run dev    
    ~~~


#### 버전관리가 불필요한 파일 처리
- 파일이 많고 용량이 크지만 버전관리가 불필요한 것들이 있다.
  - ex) .cache, dist, node_modules

- .gitignore 파일에 버전관리가 필요 없는 폴더나 파일을 명시해준다.
  ~~~
  .cache/
  dist/
  node_modules/
  ~~~