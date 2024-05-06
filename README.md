- about
    
    00:00
    
    - はい、それでは今回はpropsについて解説します。
        
        ```tsx
        // App.tsx
        import { useState } from 'react';
        import reactLogo from './assets/react.svg';
        import viteLogo from '/vite.svg';
        import './App.css';
        import PageTitle from './components/PageTitle';
        
        function App() {
          const [count, setCount] = useState(0);
        
          return (
            <>
              <div>
                <a href="https://vitejs.dev" target="_blank">
                  <img src={viteLogo} className="logo" alt="Vite logo" />
                </a>
                <a href="https://react.dev" target="_blank">
                  <img src={reactLogo} className="logo react" alt="React logo" />
                </a>
              </div>
              <h1>Vite + React</h1>
              <div className="card">
                <button onClick={() => setCount((count) => count + 1)}>
                  count is {count}
                </button>
                <p>
                  Edit <code>src/App.tsx</code> and save to test HMR
                </p>
                <PageTitle />
              </div>
              <p className="read-the-docs">
                Click on the Vite and React logos to learn more
              </p>
            </>
          );
        }
        
        export default App;
        
        ```
        
    
    まず、コンポーネントにpropsを渡す方法ですが、propsのタグの中に渡したいデータを設定します。任意の値で大丈夫ですが、今回はタイトルを変更しますので、「タイトル」という値で設定します。こちらはアップコンポーネントから呼び出されるページタイトルのコンポーネントですので、「アップ」と設定してあります。まずは、これを一度コピーします。今回のページタイトルはindex.tsxから呼ばれていますので、
    
    - こちらにも設定します。
        
        ```tsx
        // main.tsx
        import React from 'react';
        import ReactDOM from 'react-dom/client';
        import App from './App.tsx';
        import './index.css';
        import PageTitle from './components/PageTitle';
        
        ReactDOM.createRoot(document.getElementById('root')!).render(
          <React.StrictMode>
            <PageTitle title="main"/>
            <App />
          </React.StrictMode>
        );
        ```
        
        ```tsx
        // App.tsx
        import { useState } from 'react';
        import reactLogo from './assets/react.svg';
        import viteLogo from '/vite.svg';
        import './App.css';
        import PageTitle from './components/PageTitle';
        
        function App() {
          const [count, setCount] = useState(0);
        
          return (
            <>
              <div>
                <a href="https://vitejs.dev" target="_blank">
                  <img src={viteLogo} className="logo" alt="Vite logo" />
                </a>
                <a href="https://react.dev" target="_blank">
                  <img src={reactLogo} className="logo react" alt="React logo" />
                </a>
              </div>
              <h1>Vite + React</h1>
              <div className="card">
                <button onClick={() => setCount((count) => count + 1)}>
                  count is {count}
                </button>
                <p>
                  Edit <code>src/App.tsx</code> and save to test HMR
                </p>
                <PageTitle title="App" />
              </div>
              <p className="read-the-docs">
                Click on the Vite and React logos to learn more
              </p>
            </>
          );
        }
        
        export default App;
        
        ```
        
    
    こちらはインデックスページから呼ばれていますので、「インデックス」に変更します。このままではまだ内容の変更はありません。
    
    01:05
    
    次に、PageTitle.tsxを開き、関数の引数でpropsを受けます。
    
    - ここでpropsを定義しましょう。
        
        ```tsx
        // PageTitle.tsx
        
        // import { useState } from 'react';
        // import reactLogo from './assets/react.svg';
        // import viteLogo from '/vite.svg';
        // import './App.css';
        import * as React from 'react';
        
        function PageTitle(props) {
          return <h1>Hello</h1>;
        }
        
        // export default App;
        export default PageTitle;
        
        ```
        
    
    その後、propsからタイトルを受け取る方法ですが、jsxの中でJavaScriptを記述するために波括弧を使用します。この中にpropsを記述しましょう。propsはオブジェクト形式で渡されますので、
    
    - 「props.タイトル」という名前を設定します。
        
        ```tsx
        // PageTitle.tsx
        
        // import { useState } from 'react';
        // import reactLogo from './assets/react.svg';
        // import viteLogo from '/vite.svg';
        // import './App.css';
        import * as React from 'react';
        
        function PageTitle(props) {
          return <h1>Hello {props.title} </h1>;
        }
        
        // export default App;
        export default PageTitle;
        
        ```
        
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70b41a1b-afe9-4147-ba52-ba4de2c3c4ff/fae52e82-e7ac-4035-8259-b0253f763164/Untitled.png)
    
    それにより、右側の表示が「アップコンポーネントから呼ばれたページタイトル」「インデックスから呼ばれたページタイトル」と変わり、それぞれの内容が変わったことを確認できます。
    
    02:08
    
    propsはオブジェクト形式で渡されますので、波括弧を使ってオブジェクトの中身を取り出し、
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70b41a1b-afe9-4147-ba52-ba4de2c3c4ff/e93a8d6e-153d-4dc4-b7cc-1e1cb87e0268/Untitled.png)
    
    - 「タイトル」だけにすることも可能です。
        
        ```tsx
        // PageTitle.tsx
        
        // import { useState } from 'react';
        // import reactLogo from './assets/react.svg';
        // import viteLogo from '/vite.svg';
        // import './App.css';
        import * as React from 'react';
        
        // function PageTitle(props) {
          //   return <h1>Hello {props.title} </h1>;
          // }
          function PageTitle({title}) {
            return <h1>Hello {title} </h1>;
          }
          
        // export default App;
        export default PageTitle;
        
        ```
        
    
    このようにpropsを使うと、コンポーネントの柔軟性を広げることが可能になります。
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/70b41a1b-afe9-4147-ba52-ba4de2c3c4ff/34aca7d5-eea1-4178-8408-801cf5df5579/Untitled.png)
