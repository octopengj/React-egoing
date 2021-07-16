# 생활코딩 리액트



## 1. React

npm install create-react-app

create-react-app my-app

cd my-app

npm run start



---

index.html

```react
<div id="root"></div>
```

App.js

```react
function App() {
  return (
    <div>
          here
    </div>
  );
}

export default App;
```

```react
import React, { Component } from 'react';

class App extends Component {
  render() {
    return (
      <div className="App">

      </div>
    )
  }
}

export default App;
```

index.js (진입파일)

```react
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
```



---

## 2. CSS 

index.css에서 작성하고

index.js에서 import해서 사용한다.

```react
import './index.css' 
```



---

## 3. deploy

create-react-app 파일이 무겁다. 개발할 때 사용하고

빌드를 할 때는 npm run build을 하면 build 디렉토리가 생성 될 것임

index.html파일이 있을 텐데 공백 없는 빽빽한 코딩이 되어 있을 것이다.

create-react-app이 불필요한 공간을 싹 줄여준 것임

실제로 서비스 할 때는 build안에 있는 것을 사용한다.

npx serve -s build로 설치 여기서 -s는 build를 documnet root로 하겠다는 설정

serving! 주소로 들어가면 된다.



---

## 4. Component

순수html을 react로 바꾸는 예제

```html
<html>
    <body>
        <header>
        <h1>WEB</h1>
        world wide web!
        </header>

        <nav>
            <ul>
                <li><a href="1.html">HTML</a></li>
                <li><a href="2.CSS">CSS</a></li>
                <li><a href="3.JavaScript">JavaScript</a></li>
            </ul>
        </nav>

        <article>
            <h2>HTML</h2>
            HTML is HyperText Markup Language.
        </article>
    </body>
</html>
```

App.js에서  Component로 만들기

```react
import React, {Component} from 'react';

class Subject extends Component {
  render() {
    return (
      <header>
        <h1>WEB</h1>
        world wide web!
      </header>
    );
  }
}

class TOC extends Component {
  render() {
    return (
      <nav>
        <ul>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.CSS">CSS</a></li>
            <li><a href="3.JavaScript">JavaScript</a></li>
        </ul>
  	  </nav>
    );
  }
}

class Content extends Component {
  render() {
    return(
      <article>
        <h2>HTML</h2>
        HTML is HyperText Markup Language.
      </article>
    );
  }
}

class App extends Component {
  render() {
    return (
      <div className="App">
        <Subject/>
        <TOC />
        <Content />
      </div>
    )
  }
}

export default App
```



---

## 5. Props

Component의 속성으로 정의 된 값을 불러오는 방법

App.js

```react
import React, {Component} from 'react';

class Subject extends Component {
  render() {
    return (
      <header>
        <h1>WEB</h1>
        world wide web!
      </header>
    );
  }
}

class TOC extends Component {
  render() {
    return (
      <nav>
        <ul>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.CSS">CSS</a></li>
            <li><a href="3.JavaScript">JavaScript</a></li>
        </ul>
  	  </nav>
    );
  }
}

class Content extends Component {
  render() {
    return(
      <article>
        <h2>HTML</h2>
        HTML is HyperText Markup Language.
      </article>
    );
  }
}

class App extends Component {
  render() {
    return (
      <div className="App">
        <Subject/>
        <TOC />
        <Content />
      </div>
    )
  }
}

export default App
```

props 사용

```react
import React, {Component} from 'react';

class Subject extends Component {
  render() {
    return (
      <header>
        <h1>{this.props.title}</h1>
        {this.props.sub}
      </header>
    );
  }
}

class TOC extends Component {
  render() {
    return (
      <nav>
        <ul>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.CSS">CSS</a></li>
            <li><a href="3.JavaScript">JavaScript</a></li>
        </ul>
      </nav>
    );
  }
}

class Content extends Component {
  render() {
    return(
      <article>
        <h2>{this.props.title}</h2>
        {this.props.desc}
      </article>
    );
  }
}

class App extends Component {
  render() {
    return (
      <div className="App">
        <Subject title="WEB" sub="world wide web!"/>
        <TOC />
        <Content title="HTML" desc="HTML is HyperText Markup Language."/>
      </div>
    )
  }
}

export default App
```



---

## 6. DEVTOOL

React developer tool을 크롬에서 설치

개발자도구를 열고 Elements를 보는 것이 아니라

리액트의 Component를 보고 싶으면 React를 클릭해서 보면 만든 앱의 Component를 보여준다.

실시간으로 값을 바꿔서 상태를 확인할 수도 있다.



---

## 7. Component 분리

하나의 파일안에 많은 Component가 있으면 복잡하다. 그래서 컴포넌트 별로 분리하여 사용한다.

src에 components라는 폴더를 만들고 정리

App.js

```react
import React, {Component} from 'react';

class Subject extends Component {
  render() {
    return (
      <header>
        <h1>{this.props.title}</h1>
        {this.props.sub}
      </header>
    );
  }
}

class TOC extends Component {
  render() {
    return (
      <nav>
        <ul>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.CSS">CSS</a></li>
            <li><a href="3.JavaScript">JavaScript</a></li>
        </ul>
      </nav>
    );
  }
}

class Content extends Component {
  render() {
    return(
      <article>
        <h2>{this.props.title}</h2>
        {this.props.desc}
      </article>
    );
  }
}

class App extends Component {
  render() {
    return (
      <div className="App">
        <Subject title="WEB" sub="world wide web!"/>
        <TOC />
        <Content title="HTML" desc="HTML is HyperText Markup Language."/>
      </div>
    )
  }
}

export default App
```



Component.js 생성

```react
import React, {Component} from 'react';

class Content extends Component {
    render() {
      return(
        <article>
          <h2>{this.props.title}</h2>
          {this.props.desc}
        </article>
      );
    }
  }

  export default Content
```

TOC.js 생성

```react
import React, {Component} from 'react';

class TOC extends Component {
    render() {
      return (
        <nav>
          <ul>
              <li><a href="1.html">HTML</a></li>
              <li><a href="2.CSS">CSS</a></li>
              <li><a href="3.JavaScript">JavaScript</a></li>
          </ul>
        </nav>
      );
    }
  }

  export default TOC
```

Subject.js 생성

```react
import React, {Component} from 'react';

class Subject extends Component {
    render() {
      return (
        <header>
          <h1>{this.props.title}</h1>
          {this.props.sub}
        </header>
      );
    }
  }

  export default Subject
```

App.js에서 import

```react
import React, {Component} from 'react';
import TOC from './components/TOC';
import Content from './components/Content';
import Subject from './components/Subject';

class App extends Component {
  render() {
    return (
      <div className="App">
        <Subject title="WEB" sub="world wide web!"/>
        <TOC />
        <Content title="HTML" desc="HTML is HyperText Markup Language."/>
      </div>
    );
  }
}

export default App
```



---

## 8. State

컴포넌트의 기본적인 동작을 바꾸고 싶을 때 사용자에게 제공하는 것이 props이고 component를 조작할 수 있게 된다.

컴포넌트의 내부적으로 사용되고 구현되는 것들이 state이다.



App.js에서 App이라는 컴포넌트에 Subject라는 하위 컴포넌트가 있고 그 안에 props들이 있는데

그 값들을 state로 만들고 Subject의 props로 전달하는 것으로 개선하는 예제





props를 사용하기 위해서 필요한 코드

```react
class App extends Component {
    constructor(props){
        super(props);
    }
    render() {
      return(
          
      );
    }
  }
```

어떤 컴포넌트가 실행 될 때 render라는 함수보다 먼저 실행이 되면서 그 컴포넌트를 초기화 시켜주는 코드이다.



그리고 state값을 초기화시키기

```react
class App extends Component {
    constructor(props){
        super(props);
        this.state = {
        
        }
    }
    render() {
      return(
          
      );
    }
  }
```



state화 시킬 컴포넌트 작성

```react
class App extends Component {
    constructor(props){
        super(props);
        this.state = {
            subject: {title: 'WEB', sub: 'World Wide Web'}
        }
    }
```



state의 값을 title의 값으로

```react
render() {
    return (
      <div className="App">
        <Subject title="WEB" sub="world wide web!"/>
        <TOC />
        <Content title="HTML" desc="HTML is HyperText Markup Language."/>
      </div>
    )
  }
```

```react
  render() {
    return (
      <div className="App">
        <Subject title={this.state.subject.title} sub={this.state.subject.sub} />
        <TOC />
        <Content title="HTML" desc="HTML is HyperText Markup Language."/>
      </div>
    )
  }
```

state값을 입력할 때 " "로 감싸면 오류발생



상위 컴포넌트의 state값을 하위 컴포넌트의 props의 값으로 전달하는 것이 가능하다.

App.js

```react
import React, {Component} from 'react';
import TOC from './components/TOC';
import Content from './components/Content';
import Subject from './components/Subject';

class App extends Component {
  constructor(props){
    super(props);
    this.state = {
      subject: {title: "WEB", sub: "World Wide Web."}
    }
  }
  render() {
    return (
      <div className="App">
        <Subject title={this.state.subject.title} sub={this.state.subject.sub} />
        <TOC />
        <Content title="HTML" desc="HTML is HyperText Markup Language."/>
      </div>
    )
  }
}

export default App
```



---

## 9. key

state를 여러개 사용할 때는 코드가 더 필요하다.



부모컴포넌트가 가지고 있는 state값을 이용해서 자식컴포넌트의 내부 값을 변경하도록 만들기 예제

```react
class App extends Component {
  constructor(props){
    super(props);
    this.state = {
      subject: {title: "WEB", sub: "World Wide Web."}
    }
  }
```

위에서 state에  props 추가하는 데 여러개를 사용하니 배열로 

```react
class App extends Component {
  constructor(props){
    super(props);
    this.state = {
      subject: {title: "WEB", sub: "World Wide Web."},
      contents: [
        {id:1, title:"HTML", desc: "HTML is HyperText Markup Language."},
        {id:2, title:"CSS", desc: "CSS is for design."},
        {id:3, title:"JavaScript", desc: "JavaScript is for interactive."}
      ]
    }
  }
```

TOC에 data라는 props를 만들어주고

```react
TOC data={this.state.contents}/>
```

그러면 TOC컴포넌트에서 내부적으로 this.props.data라는 값을 갖게 된다.

```react
class TOC extends Component {
    render() {
      return (
        <nav>
          <ul>
              <li><a href="1.html">HTML</a></li>
              <li><a href="2.CSS">CSS</a></li>
              <li><a href="3.JavaScript">JavaScript</a></li>
          </ul>
        </nav>
      );
    }
  }
```

```react
class TOC extends Component {
    render() {
        this.props.data  // 이곳 확인
      return (
        <nav>
          <ul>
              <li><a href="1.html">HTML</a></li>
              <li><a href="2.CSS">CSS</a></li>
              <li><a href="3.JavaScript">JavaScript</a></li>
          </ul>
        </nav>
      );
    }
  }
```

배열을 통해서 값을 변경하도록 만들어야 하기 때문에 반복문 사용

```react
class TOC extends Component {
    render() {
        var data = this.props.data  // length코드가 길어지니 변수에 담음
        var i = 0;
        while(i < data.length){
            i = i+1;
        }
```

반복할 때마다 `<li><a href="1.html">HTML</a></li>` 이 코드들을 배열에 담아서  push

```react
import React, {Component} from 'react';

class TOC extends Component {
    render() {
        var lists = [];
        var data = this.props.data
        var i = 0;
        while(i < data.length){
            lists.push(<li><a href={"/content/" + data[i].id}>{data[i].title}</a></li>);
            i = i+1;
        }

      return (
        <nav>
          <ul>
              <li><a href="1.html">HTML</a></li>
              <li><a href="2.CSS">CSS</a></li>
              <li><a href="3.JavaScript">JavaScript</a></li>
          </ul>
        </nav>
      );
    }
  }

  export default TOC
```

그리고 return 값 수정

```react
import React, {Component} from 'react';

class TOC extends Component {
    render() {
        var lists = [];
        var data = this.props.data
        var i = 0;
        while(i < data.length){
            lists.push(<li><a href={"/content/" + data[i].id}>{data[i].title}</a></li>);
            i = i+1;
        }

      return (
        <nav>
          <ul>
              {lists}
          </ul>
        </nav>
      );
    }
  }

  export default TOC
```

이때 브라우저는 정상적으로 작동을 하지만 개발자도구를 열어보면 오류를 발생시킴

```html
Warning: Each child in a list should have a unique "key" prop.
```

여러개의 엘리먼트를 자동으로 생성하는 경우에 발생하는 에러이다.

각각의 리스트의 항목들은 key 프롭스를 가져야한다.

```react
lists.push(<li key={data[i].id}><a href={"/content/" + data[i].id}>{data[i].title}</a></li>);
```

다시 리로드하면 에러가 사라진다.

```react
import React, {Component} from 'react';

class TOC extends Component {
    render() {
        var lists = [];
        var data = this.props.data
        var i = 0;
        while(i < data.length){
            lists.push(<li key={data[i].id}><a href={"/content/" + data[i].id}>{data[i].title}</a></li>);
            i = i+1;
        }

      return (
        <nav>
          <ul>
              {lists}
          </ul>
        </nav>
      );
    }
  }

  export default TOC
```



---

## 10.1 이벤트

역동적으로 만들어주는 기술인 이벤트는 props, state와 함께 사용된다.



링크를 클릭하면 그에 따라서 App컴포넌트에 state가 바뀌고 그 바뀐 state가  content의 component의 props값으로 전달되면서 동적으로 application이 바뀌는 것을 구현하기

state셋팅

현재 보고있는 페이지를 welcome페이지와 read페이지로 구분을하고 코딩 시작

mode라는 값을 주고 기본값을 welcome, 그리고 welcome일때의 값을 설정

App.js

```react
class App extends Component {
  constructor(props){
    super(props);
    this.state = {
      mode: "read",
      subject: {title: "WEB", sub: "World Wide Web."},
      welcome: {title: "React", desc: "Hello, React."},
      contents: [
        {id:1, title:"HTML", desc: "HTML is HyperText Markup Language."},
        {id:2, title:"CSS", desc: "CSS is for design."},
        {id:3, title:"JavaScript", desc: "JavaScript is for interactive."}
      ]
    }
  }
```

리액트에서는 state가 바뀌면 그 state을 갖고 있는 component의 render함수가 다시 호출된다.

그리고 그 render함수 하위에 있는 컴포넌트들도 각자 render함수가 있는데 그것들도 싹다 호출된다.

props가 바뀌어도 똑같이 다시 호출 된다.



subject.js에 링크걸기

```react
import React, {Component} from 'react';

class Subject extends Component {
    render() {
      return (
        <header>
          <h1>{this.props.title}</h1>
          {this.props.sub}
        </header>
      );
    }
  }

  export default Subject
```

```react
import React, {Component} from 'react';

class Subject extends Component {
    render() {
      return (
        <header>
          <h1><a href="/">{this.props.title}</a></h1>
          {this.props.sub}
        </header>
      );
    }
  }

  export default Subject
```



mode에 따라서 만들어지는 렌더링 결과가 달라지게 조건문 사용

```react
  render() {
    var _title, _desc = null;
    if(this.state.mode === "welcome"){
      _title = this.state.welcome.title;
      _desc = this.state.welcome.desc;
    } else if(this.state.mode === "read") {
      _title = this.state.contents[0].title;
      _desc = this.state.contents[0].desc;
    }
    return (
      <div className="App">
        <Subject title={this.state.subject.title} sub={this.state.subject.sub} />
        <TOC data={this.state.contents}/>
        <Content title={_title} desc={_desc}/>
      </div>
    )
  }
```



- Subject 안에 있는 <A>태그를 클릭했을 때 App이 바뀌도록 하는 것이 최종 목표

  Subject를 풀어서 그 안에 내용을 App에 도입해서 이벤트 구현

  Subject.js

  ```react
          <header>
            <h1><a href="/">{this.props.title}</a></h1>
            {this.props.sub}
          </header>
  ```

  App.js

  ```react
     return (
        <div className="App">
          <Subject title={this.state.subject.title} sub={this.state.subject.sub} />
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
  ```

  ```react
      return (
        <div className="App">
          {/* <Subject 
          	title={this.state.subject.title} 
          	sub={this.state.subject.sub} 
          /> */}
          <header>
            <h1><a href="/">{this.props.title}</a></h1>
            {this.props.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  props를 state로 변경

  ```react
      return (
        <div className="App">
          {/* <Subject title={this.state.subject.title} sub={this.state.subject.sub} /> */}
          <header>
            <h1><a href="/">{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
  ```

  function으로 onClick 이벤트 설정하고 alert로 잘 작동하는지 확인

  ```react
      return (
        <div className="App">
          {/* <Subject title={this.state.subject.title} sub={this.state.subject.sub} /> */}
          <header>
            <h1><a href="/" onClick={function(){
              alert("hi");
            }}>{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  클릭을하면 전체가 다시 리로드된다. 이것을 방지(기본적인 동작방법을 막는방법)

  e.preventDefault();

  ```react
      return (
        <div className="App">
          {/* <Subject title={this.state.subject.title} sub={this.state.subject.sub} /> */}
          <header>
            <h1><a href="/" onClick={function(e){
              e.preventDefault();
            }}>{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  

  ## 10.2 이벤트에서 state변경하기

  this.state.mode값을 "welcome"으로 변경해서 클릭을 했을 때 화면이 바뀌도록 설정

  ```react
      return (
        <div className="App">
          {/* <Subject title={this.state.subject.title} sub={this.state.subject.sub} /> */}
          <header>
            <h1><a href="/" onClick={function(e){
              e.preventDefault();
              this.state.mode="welcome";
            }}>{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  this.state.mode = "welcome"; 으로 저장하고 클릭을하면 오류가 발생한다.

  ```html
  TypeError: Cannot read property 'state' of undefined
  ```

  function안에 this를 알지 못한다. 이때 해결하는 방법이 bind(this) 

  ```react
      return (
        <div className="App">
          {/* <Subject title={this.state.subject.title} sub={this.state.subject.sub} /> */}
          <header>
            <h1><a href="/" onClick={function(e){
              e.preventDefault();
              this.state.mode="welcome";
            }.bind(this)}>{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  다시 저장하고 클릭하면 오류는 사라지지만 아무런 반응이 없다.

  리액트에서 state값을 변경할 때 공식문서에 나와있는 방법대로 안해서 그렇다. 

  setState를 사용해야 한다.

  ```react
      return (
        <div className="App">
          {/* <Subject title={this.state.subject.title} sub={this.state.subject.sub} /> */}
          <header>
            <h1><a href="/" onClick={function(e){
              console.log(e);
              e.preventDefault();
              // this.state.mode = "welcome";
              this.setState({
                mode: "welcome"
              });
            }.bind(this)}>{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  

  ## 10.2.1 bind함수 이해하기

  render함수 안에서의 this는 속해있는 해당컴포넌트 자신을 가리킨다.

  그러나 함수안에서의 this는 아무값도 없다. this 값이 없을 때 강제로 주입하는 방법이 bind(this)

  

  ```javascript
  var obj = {name: 'peng'};
  undefined
  function bindTest(){
      console.log(this.name);
  }
  undefined
  bindTest();    // bindTest를 호출하면 undefind
  undefined
  
  
  var bindTest2 = bindTest.bind(obj);   // bind로 묶고 bindTest2라는 변수에 담아주고
  undefined
  bindTest2();				// bindTest2를 호출하면 name이 출력된다.
  peng
  undefined
  ```

  

  ## 10.2.2 setState 이해하기

  state의 값을 직접 변경하면 안되고 함수형태로 변경해야하는 이유

  

  어떤 컴포넌트가 생성될 때 최초로 실행되는 constructor함수 안에서는 아래처럼 수정하면 된다.

  ```react
  class App extends Component {
    constructor(props){
      super(props);
      this.state = {
        mode: "read",
        subject: {title: "WEB", sub: "World Wide Web."},
        welcome: {title: "React", desc: "Hello, React."},
        contents: [
          {id:1, title:"HTML", desc: "HTML is HyperText Markup Language."},
          {id:2, title:"CSS", desc: "CSS is for design."},
          {id:3, title:"JavaScript", desc: "JavaScript is for interactive."}
        ]
      }
    }
  ```

  하지만 이미 컴포넌트가 생성이 끝나고 난 다음에 동적으로 state의 값을 변경할 때

  ```react
   // this.state.mode = "welcome";
  ```

  이런식으로 하면 안된다.

  setState라는 함수에 변경하고 싶은 값을 객체형태로 주어 변경해야 한다.

  ```react
  this.setState({
     mode: "welcome"
  });
  ```

  

  ## 11 이벤트 만들기

  주석처리 해둔 코드를 다시 살려서 작업

  ```react
  	return (
        <div className="App">
          {/* <Subject title={this.state.subject.title} sub={this.state.subject.sub} /> */}
          <header>
            <h1><a href="/" onClick={function(e){
              console.log(e);
              e.preventDefault();
              // this.state.mode = "welcome";
              this.setState({
                mode: "welcome"
              });
            }.bind(this)}>{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header>
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  ```react
      return (
        <div className="App">
          <Subject title={this.state.subject.title} sub={this.state.subject.sub} />
          {/* <header>
            <h1><a href="/" onClick={function(e){
              console.log(e);
              e.preventDefault();
              // this.state.mode = "welcome";
              this.setState({
                mode: "welcome"
              });
            }.bind(this)}>{this.state.subject.title}</a></h1>
            {this.state.subject.sub}
          </header> */}
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  사용자가 링크를 클릭했을 때 이벤트를 설치하고 싶다면 onChangePage라는 이벤트를 쓴다.

  ```react
      return (
        <div className="App">
          <Subject 
          title={this.state.subject.title} 
          sub={this.state.subject.sub} 
          onChangePage={function(){
            this.setState({mode:'welcome'});
          }.bind(this)}
          />
          <TOC data={this.state.contents}/>
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  Subject.js

  ```react
  import React, {Component} from 'react';
  
  class Subject extends Component {
      render() {
        return (
          <header>
            <h1><a href="/" onClick={function(e){
                e.preventDefault();
                this.props.onChangePage();
            }.bind(this)}>{this.props.title}</a></h1>
            {this.props.sub}
          </header>
        );
      }
    }
  
    export default Subject
  ```



- 글목록 이벤트처리

  - mode 바꾸기

    ```react
        return (
          <div className="App">
            <Subject 
            title={this.state.subject.title} 
            sub={this.state.subject.sub} 
            onChangePage={function(){
              this.setState({mode:'welcome'});
            }.bind(this)}
            />
            <TOC
              onChangePage={function(){
                this.setState({mode:"read"});
              }.bind(this)} 
              data={this.state.contents}
            />
            <Content title={_title} desc={_desc}/>
          </div>
        )
    ```

    TOC.js

    ```react
    import React, {Component} from 'react';
    
    class TOC extends Component {
        render() {
            var lists = [];
            var data = this.props.data
            var i = 0;
            while(i < data.length){
                lists.push(
                <li key={data[i].id}>
                    <a 
                    href={"/content/" + data[i].id}
                    onClick={function(e){
                        e.preventDefault();
                        this.props.onChangePage();
                    }.bind(this)}
                    >{data[i].title}</a>
                </li>);
                i = i+1;
            }
    
          return (
            <nav>
              <ul>
                  {lists}
              </ul>
            </nav>
          );
        }
      }
    
      export default TOC
    ```

  - 본문 내용 바꾸기

    app에 state에다가 selectedContentId를 줘서 contents의 값과 일치하는 것을 표시

    ```react
    import React, {Component} from 'react';
    import TOC from './components/TOC';
    import Content from './components/Content';
    import Subject from './components/Subject';
    
    class App extends Component {
      constructor(props){
        super(props);
        this.state = {
          mode: "read",
          selected_content_id:2,
          subject: {title: "WEB", sub: "World Wide Web."},
          welcome: {title: "React", desc: "Hello, React."},
          contents: [
            {id:1, title:"HTML", desc: "HTML is HyperText Markup Language."},
            {id:2, title:"CSS", desc: "CSS is for design."},
            {id:3, title:"JavaScript", desc: "JavaScript is for interactive."}
          ]
        }
      }
      render() {
        var _title, _desc = null;
        if(this.state.mode === "welcome"){
          _title = this.state.welcome.title;
          _desc = this.state.welcome.desc;
        } else if(this.state.mode === "read") {
          var i = 0;
          while(i < this.state.contents.length){
            var data = this.state.contents[i];
            if(data.id === this.state.selected_content_id) {
              _title = data.title;
              _desc = data.desc;
              break;
            }
            i = i + 1;
          }
        }
        return (
          <div className="App">
            <Subject 
            title={this.state.subject.title} 
            sub={this.state.subject.sub} 
            onChangePage={function(){
              this.setState({mode:'welcome'});
            }.bind(this)}
            />
            <TOC
              onChangePage={function(id){
                this.setState({
                  mode:"read",
                  selected_content_id:Number(id)
                });
              }.bind(this)} 
              data={this.state.contents}
            />
            <Content title={_title} desc={_desc}/>
          </div>
        )
      }
    }
    
    export default App
    ```

    TOC.js

    ```react
    import React, {Component} from 'react';
    
    class TOC extends Component {
        render() {
            var lists = [];
            var data = this.props.data
            var i = 0;
            while(i < data.length){
                lists.push(
                <li key={data[i].id}>
                    <a 
                    href={"/content/" + data[i].id}
                    data-id={data[i].id}
                    onClick={function(e){
                        e.preventDefault();
                        this.props.onChangePage(e.target.dataset.id);
                    }.bind(this)}
                    >{data[i].title}</a>
                </li>);
                i = i+1;
            }
    
          return (
            <nav>
              <ul>
                  {lists}
              </ul>
            </nav>
          );
        }
      }
    
      export default TOC
    ```

    data-id와 this.props.onChangePage(e.target.dataset.id);의 id이름을 일치시켜야한다.

    data-id가 data-iid라면 e.target.dataset.iid로 일치

  - 속성을 이용하지 않는 방법

    ```react
    import React, {Component} from 'react';
    
    class TOC extends Component {
        render() {
            var lists = [];
            var data = this.props.data
            var i = 0;
            while(i < data.length){
                lists.push(
                <li key={data[i].id}>
                    <a 
                    href={"/content/" + data[i].id}
                    onClick={function(id, e){
                        e.preventDefault();
                        this.props.onChangePage(id);
                    }.bind(this, data[i].id)}
                    >{data[i].title}</a>
                </li>);
                i = i+1;
            }
    
          return (
            <nav>
              <ul>
                  {lists}
              </ul>
            </nav>
          );
        }
      }
    
      export default TOC
    ```

    bind(this)의 두번째 인자로 data[i].id를 주면 대상 함수의 첫번째 매개변수 값으로 넣어준다.

    그면 e는 한칸씩 밀려남

    

    

## 12. Create

### 12.1. mode 변경 기능

TOC와 Content 사이에 버튼 반들기

delete는 링크태그가 아닌 버튼과 같은 오퍼레인션 기능을 사용 

```react
    return (
      <div className="App">
        <Subject 
        title={this.state.subject.title} 
        sub={this.state.subject.sub} 
        onChangePage={function(){
          this.setState({mode:'welcome'});
        }.bind(this)}
        />
        <TOC
          onChangePage={function(id){
            this.setState({
              mode:"read",
              selected_content_id:Number(id)
            });
          }.bind(this)} 
          data={this.state.contents}
        />
        <ul>
          <li><a href="/create">create</a></li>
          <li><a href="/update">update</a></li>
          <li><input type="button" value="delete"></input></li>
        </ul>
        <Content title={_title} desc={_desc}/>
      </div>
    )
```

Control.js를 만들어서 이동시키기

```react
import React, {Component} from 'react';
import TOC from './components/TOC';
import Content from './components/Content';
import Subject from './components/Subject';
import Control from './components/Control';

class App extends Component {
  constructor(props){
    super(props);
    this.state = {
      mode: "read",
      selected_content_id:2,
      subject: {title: "WEB", sub: "World Wide Web."},
      welcome: {title: "React", desc: "Hello, React."},
      contents: [
        {id:1, title:"HTML", desc: "HTML is HyperText Markup Language."},
        {id:2, title:"CSS", desc: "CSS is for design."},
        {id:3, title:"JavaScript", desc: "JavaScript is for interactive."}
      ]
    }
  }
  render() {
    var _title, _desc = null;
    if(this.state.mode === "welcome"){
      _title = this.state.welcome.title;
      _desc = this.state.welcome.desc;
    } else if(this.state.mode === "read") {
      var i = 0;
      while(i < this.state.contents.length){
        var data = this.state.contents[i];
        if(data.id === this.state.selected_content_id) {
          _title = data.title;
          _desc = data.desc;
          break;
        }
        i = i + 1;
      }
    }
    return (
      <div className="App">
        <Subject 
        title={this.state.subject.title} 
        sub={this.state.subject.sub} 
        onChangePage={function(){
          this.setState({mode:'welcome'});
        }.bind(this)}
        />
        <TOC
          onChangePage={function(id){
            this.setState({
              mode:"read",
              selected_content_id:Number(id)
            });
          }.bind(this)} 
          data={this.state.contents}
        />
        <Control />
        <Content title={_title} desc={_desc}/>
      </div>
    )
  }
}

export default App
```

Control.js

```react
import React, { Component } from 'react'

class Control extends Component {
    render() {
        return (
            <ul>
                <li><a href="/create">create</a></li>
                <li><a href="/update">update</a></li>
                <li><input type="button" value="delete"></input></li>
          </ul>
        )
    }
}

export default Control

```

- Control 컴포넌트에 이벤트 적용

  ```react
      return (
        <div className="App">
          <Subject 
          title={this.state.subject.title} 
          sub={this.state.subject.sub} 
          onChangePage={function(){
            this.setState({mode:'welcome'});
          }.bind(this)}
          />
          <TOC
            onChangePage={function(id){
              this.setState({
                mode:"read",
                selected_content_id:Number(id)
              });
            }.bind(this)} 
            data={this.state.contents}
          />
          <Control onChangeMode={function(_mode){
            this.setState({
              mode:_mode
            })
          }.bind(this)} />
          <Content title={_title} desc={_desc}/>
        </div>
      )
  ```

  Control.js

  ```react
  import React, { Component } from 'react'
  
  class Control extends Component {
      render() {
          return (
              <ul>
                  <li><a href="/create" onClick={function(e){
                      e.preventDefault();
                      this.props.onChangeMode("create");
                  }.bind(this)}>create</a></li>
                  <li><a href="/update" onClick={function(e){
                      e.preventDefault();
                      this.props.onChangeMode("update");
                  }.bind(this)}>update</a></li>
                  <li><input onClick={function(e){
                      e.preventDefault();
                      this.props.onChangeMode("delete");
                  }.bind(this)} type="button" value="delete"></input></li>
            </ul>
          )
      }
  }
  
  export default Control
  
  ```

  



### 12.2 mode 전환 기능

read를 create로 전환

Contents.js를 ReadContent.js로 변경

```react
import React, {Component} from 'react';

class ReadContent extends Component {
    render() {
      return(
        <article>
          <h2>{this.props.title}</h2>
          {this.props.desc}
        </article>
      );
    }
  }

  export default ReadContent
```

CreateContent.js 생성

```react
import React, {Component} from 'react';

class CreateContent extends Component {
    render() {
      return(
        <article>
          <h2>Create</h2>
          <form>
            
          </form>
        </article>
      );
    }
  }

  export default CreateContent
```

ReadContent 영역이 가변적으로 바뀔 수 있도록 변수처리

```react
import React, {Component} from 'react';
import TOC from './components/TOC';
import ReadContent from './components/ReadContent';
import Subject from './components/Subject';
import Control from './components/Control';
import CreateContent from './components/CreateContent';

class App extends Component {
  constructor(props){
    super(props);
    this.state = {
      mode: "read",
      selected_content_id:2,
      subject: {title: "WEB", sub: "World Wide Web."},
      welcome: {title: "React", desc: "Hello, React."},
      contents: [
        {id:1, title:"HTML", desc: "HTML is HyperText Markup Language."},
        {id:2, title:"CSS", desc: "CSS is for design."},
        {id:3, title:"JavaScript", desc: "JavaScript is for interactive."}
      ]
    }
  }
  render() {
    var _title, _desc, _article = null;
    if(this.state.mode === "welcome"){
      _title = this.state.welcome.title;
      _desc = this.state.welcome.desc;
      _article = <ReadContent title={_title} desc={_desc}/>      // mode가 welcome이나 read 일때 
          													// ReadContent가 출력되도록
    } else if(this.state.mode === "read") {
      var i = 0;
      while(i < this.state.contents.length){
        var data = this.state.contents[i];
        if(data.id === this.state.selected_content_id) {
          _title = data.title;
          _desc = data.desc;
          break;
        }
        i = i + 1;
      }
      _article = <ReadContent title={_title} desc={_desc}/>
    } else if (this.state.mode === "create"){
      _article = <CreateContent />
    }
    return (
      <div className="App">
        <Subject 
        title={this.state.subject.title} 
        sub={this.state.subject.sub} 
        onChangePage={function(){
          this.setState({mode:'welcome'});
        }.bind(this)}
        />
        <TOC
          onChangePage={function(id){
            this.setState({
              mode:"read",
              selected_content_id:Number(id)
            });
          }.bind(this)} 
          data={this.state.contents}
        />
        <Control onChangeMode={function(_mode){
          this.setState({
            mode:_mode
          })
        }.bind(this)} />
        {_article}     							// 변수처리
      </div>
    )
  }
}

export default App
```



### 12.3 form 

CreateContents.js

```react
import React, {Component} from 'react';

class CreateContent extends Component {
    render() {
      return(
        <article>
          <h2>Create</h2>
          <form action="/create_process" method="post">
            <p><input type="text" name="title" placeholder="title"></input></p>
            <p><textarea name="desc" placeholder="description"></textarea></p>
            <p><input type="submit"></input></p>
          </form>
        </article>
      );
    }
  }

  export default CreateContent
```

mode를 create로 변경하고 작업시작

```react
 mode: "create",
```



### 12.4 onSubmit 이벤트

alert로 확인

```react
import React, {Component} from 'react';

class CreateContent extends Component {
    render() {
      return(
        <article>
          <h2>Create</h2>
          <form action="/create_process" method="post"
            onSubmit={function(e){
              e.preventDefault();
              alert("submit")
            }.bind(this)}
          >
            <p><input type="text" name="title" placeholder="title"></input></p>
            <p><textarea name="desc" placeholder="description"></textarea></p>
            <p><input type="submit"></input></p>
          </form>
        </article>
      );
    }
  }

  export default CreateContent
```



- onSubmit 호출

App.js

```react
    } else if (this.state.mode === "create"){
      _article = <CreateContent onSubmit={function(_title, _desc){
        // add content to this.state.contents
        
      }.bind(this)} />
    }
```

CreateContent.js

```react
class CreateContent extends Component {
    render() {
      return(
        <article>
          <h2>Create</h2>
          <form action="/create_process" method="post"
            onSubmit={function(e){
              e.preventDefault();
              this.props.onSubmit(
                e.target.title.value,
                e.target.desc.value
              );
            }.bind(this)}
          >
```



### 12.5 content 변경

contents의 끝에 데이터를 추가할 건데 기존의 있던 아이디 값을 쭉 읽어서 하나 더 큰 아이디 값을 만들어야 한다.

this.max_content_id = 3; (마지막 contents의 id와 같아야 한다.)

```react
class App extends Component {
  constructor(props){
    super(props);
    this.max_content_id = 3;
    this.state = {
```

어떠한 데이터를 추가할 때 사용하는 값이고 UI에 변경을 주는 값이 아니기 때문에 state사용 안함.

```react
    } else if (this.state.mode === "create"){
      _article = <CreateContent onSubmit={function(_title, _desc){
        // add content to this.state.contents
        this.max_content_id = this.max_content_id + 1;
        var _contents = this.state.contents.concat(
          {id:this.max_content_id, title:_title, desc:_desc}
        )
        this.setState({
          contents:_contents
        });
      }.bind(this)} />
    }
```



## 13 Update

### 13.1 update 구현

updatd는 기존의 값을 불러와서 수정하는 개념

UpdateContent.js 생성

```react
import React, { Component } from 'react'

class UpdateContent extends Component {
    render() {
      return(
        <article>
          <h2>Update</h2>
          <form action="/create_process" method="post"
            onSubmit={function(e){
              e.preventDefault();
              this.props.onSubmit(
                e.target.title.value,
                e.target.desc.value
              );
            }.bind(this)}
          >
            <p><input type="text" name="title" placeholder="title"></input></p>
            <p><textarea name="desc" placeholder="description"></textarea></p>
            <p><input type="submit"></input></p>
          </form>
        </article>
      );
    }
  }


export default UpdateContent

```

App.js update추가

```react
    else if (this.state.mode === "update"){
      _article = <UpdateContent onSubmit={function(_title, _desc){
        // add content to this.state.contents
        this.max_content_id = this.max_content_id + 1;
        var _contents = this.state.contents.concat(
          {id:this.max_content_id, title:_title, desc:_desc}
        )
        this.setState({
          contents:_contents
        });
      }.bind(this)} />
    }
```



복잡한 render 분리

getContent( ){ }

```react
import React, {Component} from 'react';
import TOC from './components/TOC';
import ReadContent from './components/ReadContent';
import Subject from './components/Subject';
import Control from './components/Control';
import CreateContent from './components/CreateContent';
import UpdateContent from './components/UpdateContent';

class App extends Component {
  constructor(props){
    super(props);
    this.max_content_id = 3;
    this.state = {
      mode: "create",
      selected_content_id:2,
      subject: {title: "WEB", sub: "World Wide Web."},
      welcome: {title: "React", desc: "Hello, React."},
      contents: [
        {id:1, title:"HTML", desc: "HTML is HyperText Markup Language."},
        {id:2, title:"CSS", desc: "CSS is for design."},
        {id:3, title:"JavaScript", desc: "JavaScript is for interactive."}
      ]
    }
  }
  getContent(){
    var _title, _desc, _article = null;
    if(this.state.mode === "welcome"){
      _title = this.state.welcome.title;
      _desc = this.state.welcome.desc;
      _article = <ReadContent title={_title} desc={_desc}/>
    } else if(this.state.mode === "read") {
      var i = 0;
      while(i < this.state.contents.length){
        var data = this.state.contents[i];
        if(data.id === this.state.selected_content_id) {
          _title = data.title;
          _desc = data.desc;
          break;
        }
        i = i + 1;
      }
      _article = <ReadContent title={_title} desc={_desc}/>
    } else if (this.state.mode === "create"){
      _article = <CreateContent onSubmit={function(_title, _desc){
        // add content to this.state.contents
        this.max_content_id = this.max_content_id + 1;
        var _contents = this.state.contents.concat(
          {id:this.max_content_id, title:_title, desc:_desc}
        )
        this.setState({
          contents:_contents
        });
      }.bind(this)} />
    }
    else if (this.state.mode === "update"){
      _article = <UpdateContent onSubmit={function(_title, _desc){
        // add content to this.state.contents
        this.max_content_id = this.max_content_id + 1;
        var _contents = this.state.contents.concat(
          {id:this.max_content_id, title:_title, desc:_desc}
        )
        this.setState({
          contents:_contents
        });
      }.bind(this)} />
    }
    return _article;   				 // _article 리턴
  }
  render() {
    return (
      <div className="App">
        <Subject 
        title={this.state.subject.title} 
        sub={this.state.subject.sub} 
        onChangePage={function(){
          this.setState({mode:'welcome'});
        }.bind(this)}
        />
        <TOC
          onChangePage={function(id){
            this.setState({
              mode:"read",
              selected_content_id:Number(id)
            });
          }.bind(this)} 
          data={this.state.contents}
        />
        <Control onChangeMode={function(_mode){
          this.setState({
            mode:_mode
          })
        }.bind(this)} />
        {this.getContent()}    				// {article}을 수정
      </div>
    )
  }
}

export default App
```



UpdateContent 컴포넌트가 실행될 때 입력값으로 현재 선택된 아이디 값에 해당되는 컨텐트를 업데이트 컨텐트 컴포넌트에 주입

selected_id와 같은 원소를 찾아줘야 한다.

이전에 작업한 것을 그대로 복사하는 방법 말고 분리하여 새로운 함수생성

```react
	var i = 0;
      while(i < this.state.contents.length){
        var data = this.state.contents[i];
        if(data.id === this.state.selected_content_id) {
          _title = data.title;
          _desc = data.desc;
          break;
        }
        i = i + 1;
      }
```

리팩토링작업

````react
getReadContent(){
    var i = 0;
      while(i < this.state.contents.length){
        var data = this.state.contents[i];
        if(data.id === this.state.selected_content_id) {
          return data;
          break;
        }
        i = i + 1;
      }
  }
  getContent(){
    var _title, _desc, _article = null;
    if(this.state.mode === "welcome"){
      _title = this.state.welcome.title;
      _desc = this.state.welcome.desc;
      _article = <ReadContent title={_title} desc={_desc}/>
    } else if(this.state.mode === "read") {
      var _content = this.getReadContent();
      _article = <ReadContent title={_content.title} desc={_content.desc}/>
````

update도 수정

UpdateContent에 data 입력

```react
else if (this.state.mode === "update"){
      _content = this.getReadContent();
      _article = <UpdateContent data={_content} onSubmit={function(_title, _desc){
        // add content to this.state.contents
        this.max_content_id = this.max_content_id + 1;
        var _contents = this.state.contents.concat(
          {id:this.max_content_id, title:_title, desc:_desc}
        )
        this.setState({
          contents:_contents
        });
      }.bind(this)} />
    }
```



### 13. 2 form

https://reactjs.org/docs/forms.html

UpdateContents.js에 value값 추가

```react
            <p>
                <input 
                    type="text" 
                    name="title"
                    placeholder="title"
                    value={this.props.data.title}
                ></input>
            </p>
```

props를 value에 직접 넣어주거나 onChange라는 핸들러를 사용해 주지 않으면 에러가 발생한다.

props는 read-only이다.

그래서 state화를 시켜줘야 한다.

```react
import React, { Component } from 'react'

class UpdateContent extends Component {
    constructor(props){
        super(props);
        this.state ={
            title: this.props.data.title
        }
    }
    render() {
      return(
        <article>
          <h2>Update</h2>
          <form action="/create_process" method="post"
            onSubmit={function(e){
              e.preventDefault();
              this.props.onSubmit(
                e.target.title.value,
                e.target.desc.value
              );
            }.bind(this)}
          >
            <p>
                <input 
                    type="text" 
                    name="title"
                    placeholder="title"
                    value={this.state.title}
                ></input>
            </p>
            <p><textarea name="desc" placeholder="description"></textarea></p>
            <p><input type="submit"></input></p>
          </form>
        </article>
      );
    }
  }


export default UpdateContent

```

value에 state를 값을 넣어줘도 수정이 되지 않는다.

onChange를 사용해야 한다.

```react
            <p>
                <input 
                    type="text" 
                    name="title"
                    placeholder="title"
                    value={this.state.title}
                    onChange={function(e){
                        this.setState({title:e.target.value});
                    }.bind(this)}
                ></input>
            </p>
```



- textarea 수정

  ```react
              <p>
                  <textarea 
                      name="desc" 
                      placeholder="description" 
                      value={this.state.desc}
                      onChange={function(e){
                          this.setState({desc:e.target.value});
                      }.bind(this)}
                  ></textarea>
              </p>
  ```

반복되는 코드를 줄여주기 위해 inputFormHandler함수 생성

```react
    inputFormHandler(e){
        this.setState({title:e.target.value});
    }
    render() {
      return(
        <article>
          <h2>Update</h2>
          <form action="/create_process" method="post"
            onSubmit={function(e){
              e.preventDefault();
              this.props.onSubmit(
                e.target.title.value,
                e.target.desc.value
              );
            }.bind(this)}
          >
            <p>
                <input 
                    type="text" 
                    name="title"
                    placeholder="title"
                    value={this.state.title}
                    onChange={this.inputFormHandler.bind(this)}
                ></input>
            </p>
```

textarea도 똑같이 수정을 하면 inputFormHandler의 값이 title로 정해져있기 때문에 title이 바뀐다.

그 부분을 수정

```react
this.setState({[e.target.name]: e.target.value});
```

.bind(this)도 보기 싫으면  리팩토링

```react
       this.inputFormHandler = this.inputFormHandler.bind(this);
```

```react
import React, { Component } from 'react'

class UpdateContent extends Component {
    constructor(props){
        super(props);
        this.state ={
            title: this.props.data.title,
            desc: this.props.data.desc
        }
        this.inputFormHandler = this.inputFormHandler.bind(this);
    }
    inputFormHandler(e){
        this.setState({[e.target.name]:e.target.value});
    }
    render() {
      return(
        <article>
          <h2>Update</h2>
          <form action="/create_process" method="post"
            onSubmit={function(e){
              e.preventDefault();
              this.props.onSubmit(
                e.target.title.value,
                e.target.desc.value
              );
            }.bind(this)}
          >
            <p>
                <input 
                    type="text" 
                    name="title"
                    placeholder="title"
                    value={this.state.title}
                    onChange={this.inputFormHandler}
                ></input>
            </p>
            <p>
                <textarea 
                    name="desc" 
                    placeholder="description" 
                    value={this.state.desc}
                    onChange={this.inputFormHandler}
                ></textarea>
            </p>
            <p><input type="submit"></input></p>
          </form>
        </article>
      );
    }
  }


export default UpdateContent

```

* 추가*

update를 할 때 어디를 업데이트를 할 것인지 식별자가 필요하다.

id같은 경우 hidden폼 사용

onSubmit을 할 때 id값을 주면 더 좋다.

```react
import React, { Component } from 'react'

class UpdateContent extends Component {
    constructor(props){
        super(props);
        this.state ={
            id: this.props.data.id,
            title: this.props.data.title,
            desc: this.props.data.desc
        }
        this.inputFormHandler = this.inputFormHandler.bind(this);
    }
    inputFormHandler(e){
        this.setState({[e.target.name]:e.target.value});
    }
    render() {
      return(
        <article>
          <h2>Update</h2>
          <form action="/create_process" method="post"
            onSubmit={function(e){
              e.preventDefault();
              this.props.onSubmit(
                this.state.id,
                this.state.title,
                this.state.desc
              );
            }.bind(this)}
          >
            <input type="hidden" name="id" value={this.state.id}></input>
            <p>
                <input 
                    type="text" 
                    name="title"
                    placeholder="title"
                    value={this.state.title}
                    onChange={this.inputFormHandler}
                ></input>
            </p>
            <p>
                <textarea 
                    name="desc" 
                    placeholder="description" 
                    value={this.state.desc}
                    onChange={this.inputFormHandler}
                ></textarea>
            </p>
            <p><input type="submit"></input></p>
          </form>
        </article>
      );
    }
  }


export default UpdateContent


```



### 13.3 state변경

App.js

onSubmit부분에 _id값도 추가

```react
    else if (this.state.mode === "update"){
      _content = this.getReadContent();
      _article = <UpdateContent data={_content} onSubmit={
        function(_id, _title, _desc){
          this.max_content_id = this.max_content_id + 1;
          var _contents = this.state.contents.concat(
            {id:this.max_content_id, title:_title, desc:_desc}
          )
          this.setState({
            contents:_contents
        });
      }.bind(this)} />
    }
```

create를 할 때 필요한 불필요한 코드 삭제

```react
          this.max_content_id = this.max_content_id + 1;
```

concat은 기존에 있던 데이터를 추가할 때 사용하는 것이고 지금은 수정하려고 하는 것이기 때문에 코드 수정

```react
          var _contents = this.state.contents.concat(
            {id:this.max_content_id, title:_title, desc:_desc}
          )
```

```react
          var _contents = Array.from(this.state.contents);
```

contents안에 있는 원소를 하나하나 찾아서 id값이 수정하고자 하는 것과 같은 원소를 찾아야 한다.

```react
    else if (this.state.mode === "update"){
      _content = this.getReadContent();
      _article = <UpdateContent data={_content} onSubmit={
        function(_id, _title, _desc){
          var _contents = Array.from(this.state.contents);
          var i = 0;
          while(i < _contents.length) {
            if(_contents[i].id === _id) {
              _contents[i] = {id:_id, title:_title, desc:_desc};
              break;
            }
            i = i + 1;
          }
          this.setState({
            contents:_contents
        });
      }.bind(this)} />
    }
```

수정 후 화면을 바꾸기

```react
          this.setState({
            contents:_contents,
            mode: "read"
```

create도 수정

```react
    } else if (this.state.mode === "create"){
      _article = <CreateContent onSubmit={function(_title, _desc){
        // add content to this.state.contents
        this.max_content_id = this.max_content_id + 1;
        var _contents = this.state.contents.concat(
          {id:this.max_content_id, title:_title, desc:_desc}
        )
        this.setState({
          contents:_contents,
          mode: "read",
          selected_content_id: this.max_content_id
        });
      }.bind(this)} />
    }
    else if (this.state.mode === "update"){
      _content = this.getReadContent();
      _article = <UpdateContent data={_content} onSubmit={
        function(_id, _title, _desc){
          var _contents = Array.from(this.state.contents);
          var i = 0;
          while(i < _contents.length) {
            if(_contents[i].id === _id) {
              _contents[i] = {id:_id, title:_title, desc:_desc};
              break;
            }
            i = i + 1;
          }
          this.setState({
            contents:_contents,
            mode: "read"
        });
      }.bind(this)} />
    }
    return _article;
  }
```



## 14. Delete

create로 지정해둔 mode를 welcome으로 다시 수정

delete버튼을 눌렀을 때 삭제 

Control.js

```react
                <li><input onClick={function(e){
                    e.preventDefault();
                    this.props.onChangeMode("delete");
                }.bind(this)} type="button" value="delete"></input></li>
```

App.js

```react
<Control onChangeMode={function(_mode){
          this.setState({
            mode:_mode
          });
        }.bind(this)} />
```

mode가 delete면 삭제를 하고 아니면 화면전환

```react
        <Control onChangeMode={function(_mode){
          if(_mode === "delete"){

          } else {
            this.setState({
              mode:_mode
            });
          }

        }.bind(this)} />
```

누구를 삭제할 것인가는 selected_content_id를 통해서 알 수 있다. 

```react
        <Control onChangeMode={function(_mode){
          if(_mode === "delete"){
            if(window.confirm("really?")){
              var _contents = Array.from(this.state.contents);
              var i = 0;
              while(i < _contents.length){
                if(_contents[i].id === this.state.selected_content_id){
                  _contents.splice(i,1);
                  break;
                }
                i = i + 1;
              }
              this.setState({
                mode:"welcome",
                contents: _contents
              });
              alert("deleted!");
            }
```

