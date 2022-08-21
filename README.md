# react_study

---

## 기존 웹 동작 방식

i. 서버에 데이터를 요청하면 서버 단에서 데이터 처리와 함께 view를 통째로 변경
ii. Ajax를 통해 데이터를 요청하고 JSON으로 응답받아 화면을 부분적으로 변경

복잡한 웹의 경우 Ajax를 통해 부분적인 화면 변경에 한계가 있음

## 리엑트

- 위와 같은 한계 대안으로 리액트가 등장
- 데이터 변경 감지를 통해 UI가 자동 업데이트(옵저버 패턴)
- 계속된 변경 감지를 위해 nodejs라는 Java Script 런타임 환경 기반으로 동작

### npm

- 라이브러리를 다운하고 빌드해주는 도구
- 프로젝트마다 로컬에 다운받아 중복되는 라이브러리가 많음
- 글로벌로 다운받을 수 있지만 같은 라이브러리라도 버전이 다르면 충돌 발생 할 수 있음
- 초기 세팅 및 실행

```
npm install -g create-react-app
create-react-app my-app -> 초기 설치(최초 실행 1번만)

cd my-app
npm start
```

### npx

- npm과 같이 라이브러리를 다운받고 빌드해주는 도구
- 캐싱을 통해 중복되는 라이브러리를 재사용
- 다운받고 실행 후 다시 삭제한다
- 권장
- 초기 세팅 및 실행

```
npx create-react-app my-app -> 초기 설치(최초 실행 1번만)
cd my-app
npm start
```

- VSCode 오픈 파일 경로를 my-app으로 설정하면 경로변경 없이 npm start 가능
- 종료 시, ctrl+c

---

## 리액트 확장 도구

- ESLint : 문법 검사
- Prettier - Code formatter : 코드 정렬(개인 설정 가능)
  -- File -> preference -> setting ->prettier에서 환경 설정하거나
  -- .prettierrc(이름 주의) 파일 생성하여 환경설정 가능

```
{
    "singleQuote": true, // 저장 시 홀따옴표 자동변경
    "semi": true, // 세미콜론 자동생성
    "tabWidth": 2, // tab키 공백 크기
    "trailingComma": "all", // 콤마 자동생성
    "printWidth": 80
}
```

- Reactjs code snippets : 코드 자동완성

---

### 실행과정

i. index.js 실행
ii. react-dom 라이브러리를 에서 ReactDom 을 사용해 render 함수를 실행

```
ReactDOM.render(<App />, document.getElementById('root'));
```

iii. JSX문법 <App />을 통해 App.js의 요소가 index.html의 id가 root div에 그려짐

---

### 리액트의 컴포넌트화

- return 함수를 다르제 주어 따로 렌더링한다.
- 기준이 필요하다 ##리액트 엔진전략
  i. 부모가 다시 그려지면 자식도 다시 그려야할지 연산 -> 깊은 복사
  깊은 복사 - 자식을 다시 그릴지 안그릴지 레퍼런스만 비교하여 연산이 최적화
