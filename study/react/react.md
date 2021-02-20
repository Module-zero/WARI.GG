# React
- react 공식 문서 - www.react.org
- npm 관련 공부 - www.seomal.org
## 실습환경 구축
#### npm 설치
1. www.nodejs.org 사이트에 가서 운영체제에 맞는 파일을 다운받은 후 설치.
2. 설치 확인은 ```terminal``` 에서 ```npm -v``` 를 통해 할 수 있다.
### react 설치
1. 전역으로 영구 설치(npm)
```
sudo npm install -g create-react-app
```
1. 일시적으로 한번만 설치(npx)
```
npx create-react-app
```
2. 설치확인
```
create-react-app -V
```

### 개발환경 설정
1. 디렉터리를 하나 생성한다.

2. terminal 에서 현재 디렉터리로 이동을 한다.

3. 현재 디렉터리로 react 개발 환경을 설정 명령어를 입력한다.
```
create-react-app .
```

### 실행
```
npm run start
```
 ⇢ 웹 브라우저가 자동으로 열린다.  
 ⇢ ```public > index.html``` 파일이 실행되는 것.(따로 수정할 필요가 없다.)  

### 코드 작성
- 실행 시 진입 파일은 ```src > index.js``` 이다.
- 코드의 방식은 _함수방식_, _클래스방식_ 으로 총 2가지가 있다.

###### 함수 방식
```
function App(){
    return(
        <div className="App">

        </div>
    );
}
```
###### 클래스 방식
```
class App extends Component{
    render(){
        return (
            <div className="App>
                // 이곳에 코드를 입력해 주세요
            </App>
        )
    }
}
```

### 배포하는 방법
- build 파일 생성  
개발하던 코드를 그대로 배포하면 **용량이 크기 때문에** 성능상 이슈가 있다.  
따라서 **코드를 최적화** 한 후 배포해야 한다.  
```
npm run build
```
위 코드를 ```terminal``` 에서 실행하면 ```build``` 파일이 생성된다.  
이 때 생성된 파일을 사용하여 배포하면 된다.  

- npm을 통해 설치할 수 있는 간단한 웹서버 ```serve``` 
```
npm install -g serve / npx serve
```
- ```serve``` 를 통해 서버 실행
```
serve -s {root파일명} 
```
----
----

## 컴포넌트
#### 컴포넌트란 ? 
- 컴포넌트는 여러 코드를 부품(객체)화 시켜 하나의 파일로 따로 분리를 한 것.  
- 코드의 가독성이 좋아진다.  
- 유지보수가 쉬워진다.

#### 예시
```Subject``` 라는 컴포넌트를 만들어 본다고 가정한다.
```
//Subject.js

// 컴포넌트(클래스) 명은 대문자로 시작, Component 를 상속한다.
class Subject extends Component{

    // 해당컴포넌트를 랜더링 하게 해주는 함수
    render(){ 

        // 컴포넌트의 내용
        return (

            // 반드시 하나의 최상위 태그로 시작해야 한다.
            <header>
                <h1>WEB</h1>
                welcome! 
            </header>
        )
    }
}
export default Subject; // Subject class 를 내보낸다.
```
위에서 만든 ```Subject``` 를 App 에서 호출한다.  
```
//App.js

import Subject from 'subject의 파일경로'; // 해당 컴포넌트 파일을 불러온다.

class App extends Component{
    render(){
        return(
            <div className="App">
                <Subject></Subject> // 위에서 만든 컴포넌트 호출
                // 이 위치에 Subject 클래스의 return 내부의 코드가 들어간다.
            </div>
        )
    }
}
```
- 컴포넌트는 반드시 하나의 최상위 태그로 시작해야 한다.
- 이 때, ```App``` 안에 ```Subject``` 가 포함되어 있으므로, ```App``` 를 **상위 컴포넌트** , ```Subject``` 를 **하위 컴포넌트** 라고 한다.
---
---

## props
- 어떠한 값을 컴포넌트에게 전달해 주기 위해 사용.

#### 전달하는 방법
만약 ```App``` 에서 ```Subject``` 로 전달하고자 하는 값이 **"HELLO"** 와 **"i am fine thank you"** 라는 값이라면
```
// App.js

import Subject from 'subject의 파일경로';

class App extends Component{
    render(){
        return (
            <div className="App">
                <Subject title="HELLO" desc="i am fine thank you "></Subject>
            </div>
        )
    }
}
```
위 코드처럼 보내고자 하는 _컴포넌트_ 태그 사이에 ```key="value"``` 형식으로 작성한다.  

```Subject``` Component 에서 받기 위해서는 
```
class Subject extends Component{
    render(){
        return(
            <header>
                <h1>{this.props.title}</h1>
                {this.props.desc}
            </header>
        )
    }
}
export default Subject;
```
위 코드에서처럼 ```{}``` 중괄호 안에 ```this.props.key``` 를 작성한다.  
그러면 ```key``` 에 해당하는 ```value``` 가 입력된다.  

## state
- props 에 따라서 내부 구현에 필요한 값들  
- 정보은닉과 비슷한 개념 (내부 알고리즘을 신경쓰지 않아도 된다.)  

## 예제코드
```
// App.js

import Subject from 'subject의 파일경로';

class App extends Component{
    constroctor(props){
        super(props);
        this.state = {
            subject:{title:"WEB", desc:"world wide web"}
        }
    }
    render(){
        return (
            <div className="App">
                <Subject 
                    title={this.state.shbject.title}
                    desc={this.state.subject.desc} 
                ></Subject>
            </div>
        )
    }
}
```
```constroctor``` 는 ```render``` 함수가 실행되기 이전에 **먼저 실행되며** ,함수 실행에 있어 필요한 변수의 값을 초기화하는 용도로 사용된다.  
즉, ```state``` 값을 초기화 할 때 사용한다.

## key
