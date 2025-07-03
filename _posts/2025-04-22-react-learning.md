---
title: React 學習之路
categories:
- Tech
feature_image: "https://picsum.photos/2560/600?image=2"  
excerpt: |
 createRoot...
---

# React 學習之路
## createRoot
```tsx=
import React from 'react';
import { createRoot } from 'react-dom/client';

const element = <h1>Hello, world!</h1>;
const container = document.getElementById('root');
const root = createRoot(container);
root.render(element);

```
## StrictMode
:::info
StrictMode，也被稱為嚴格模式，他的主要功能是檢查應用程式內淺在的威脅
如同 Fragment，嚴格模式不會 render 任何可見的 UI。但是嚴格模式不會影響到正式的環境，也不應該，所以他們只存在在開發環境。
:::
* 發現擁有不安全生命週期的 component
* 警告使用了 legacy string ref API
* 警告使用到了被棄用的 findDOMNode
* 偵測意想不到的副作用
* 偵測 legacy context API
* 確保可重用的 state

## 空tag
return 返回只能包含一個tag
但是透過空標籤 可以返回多個tag
```tsx=
return (
    <>
        <div>
        </div>
        <div>
        </div>
    </>
)    
```
## 插值功能
```tsx=



const Block: React.FC = (flag = true) => {
    let divContent ;
    const divTitle = "標籤標題"
    divContent = flag ? <span>flag為true</span> : <p>flag為false</p>

    return (
        <div title={divTitle}>
            {divContent}
        </div>
    )
}

export default Block;
```

## 列表渲染
```tsx=
import { Fragment } from "react/jsx-runtime";

const List: React.FC = (props) => {
    const list = [
        { id: 1, name: 'lee' },
        { id: 2, name: 'wu' },
        { id: 3, name: 'wang' }
    ]
    const listContent = list.map(item =>
        <Fragment key={item.id}>
            <li>{item.name}</li>
            <li>------------</li>
        </Fragment>
    )
    return (<>
        <ul>
            {listContent}
        </ul>
    </>)
}

export default List;
```

## 事件操作
```tsx=
import { Fragment } from "react/jsx-runtime";

const List: React.FC = (props) => {
    const list = [
        { id: 1, name: 'lee' },
        { id: 2, name: 'wu' },
        { id: 3, name: 'wang' }
    ]
    const listContent = list.map(item =>
        <Fragment key={item.id}>
            <li>{item.name}</li>
            <li>------------</li>
        </Fragment>
    )

    const handleClick= (e:React.MouseEvent<HTMLButtonElement>)=>{
        console.log('安安')
    }

    return (<>
        <button onClick={handleClick}></button>
        <ul>
            {listContent}
        </ul>
    </>)
}

export default List;
```

## 狀態 aka useState
```tsx=
import { useState } from "react";
import { Fragment } from "react/jsx-runtime";

const List: React.FC = (props) => {
    const list = [
        { id: 1, name: 'lee' },
        { id: 2, name: 'wu' },
        { id: 3, name: 'wang' }
    ]
    const listContent = list.map(item =>
        <Fragment key={item.id}>
            <li>{item.name}</li>
            <li>------------</li>
        </Fragment>
    )

    const handleClick= (e:React.MouseEvent<HTMLButtonElement>)=>{
        console.log('安安')
        setContent('新內容')
    }

    let divContent = '預設內容'
    const [content,setContent]=  useState(divContent)

    return (<>
        <button onClick={handleClick}></button>
        <div>{content}</div>
        <ul>
            {listContent}
        </ul>
    </>)
}

export default List;

```

## 副作用
``` tsx
  useEffect(() => {
    setCheckedCount(todos.filter(todo => todo.completed).length);
    setUnCheckedCount(todos.filter(todo => !todo.completed).length);

  }, [todos]);
```


## 導出語法


| 語法 | export | import |
| -------- | -------- | -------- |
| default     | export default function Button() {}     | import Button from './Button.js';     |
| named     | export function Button() {}     | import { Button } from './Button.js';     |

## 元件內容嵌入(樂高)
![元件內容嵌入](https://zh-hans.react.dev/images/docs/illustrations/i_children-prop.png)


```tsx=
export const Card =({children})=>{
  return (
   <div className="card">
        <div className="card-content">
            {children}
          </div>
     </div>
  )
}

 export const Content1 = () =>{
    return (
      <div>
        <h1>Photo</h1>
          <img
            className="avatar"
            src="https://i.imgur.com/OKS67lhm.jpg"
            alt="Aklilu Lemma"
            width={70}
            height={70}
          />
     </div>
    )
}

export default function Profile() {
  return (
    <div>
      <Card >
          <Content1></Content1>
      </Card>
      <div className="card">
        <div className="card-content">
          <h1>About</h1>
          <p>Aklilu Lemma was a distinguished Ethiopian scientist who discovered a natural treatment to schistosomiasis.</p>
        </div>
      </div>
    </div>
  );
}

```

## immer

```tsx=
import { useState } from 'react';

export default function Form() {
  const [person, setPerson] = useState({
    name: 'Niki de Saint Phalle',
    artwork: {
      title: 'Blue Nana',
      city: 'Hamburg',
      image: 'https://i.imgur.com/Sd1AgUOm.jpg',
    }
  });

  function handleNameChange(e) {
    setPerson({
      ...person,
      name: e.target.value
    });
  }

  function handleTitleChange(e) {
    setPerson({
      ...person,
      artwork: {
        ...person.artwork,
        title: e.target.value
      }
    });
  }

  function handleCityChange(e) {
    setPerson({
      ...person,
      artwork: {
        ...person.artwork,
        city: e.target.value
      }
    });
  }

  function handleImageChange(e) {
    setPerson({
      ...person,
      artwork: {
        ...person.artwork,
        image: e.target.value
      }
    });
  }

  return (
    <>
      <label>
        Name:
        <input
          value={person.name}
          onChange={handleNameChange}
        />
      </label>
      <label>
        Title:
        <input
          value={person.artwork.title}
          onChange={handleTitleChange}
        />
      </label>
      <label>
        City:
        <input
          value={person.artwork.city}
          onChange={handleCityChange}
        />
      </label>
      <label>
        Image:
        <input
          value={person.artwork.image}
          onChange={handleImageChange}
        />
      </label>
      <p>
        <i>{person.artwork.title}</i>
        {' by '}
        {person.name}
        <br />
        (located in {person.artwork.city})
      </p>
      <img
        src={person.artwork.image}
        alt={person.artwork.title}
      />
    </>
  );
}

```

使用immer可以減少代碼

```tsx=
import { useImmer } from 'use-immer';

export default function Form() {
  const [person, updatePerson] = useImmer({
    name: 'Niki de Saint Phalle',
    artwork: {
      title: 'Blue Nana',
      city: 'Hamburg',
      image: 'https://i.imgur.com/Sd1AgUOm.jpg',
    }
  });

  function handleNameChange(e) {
    updatePerson(draft => {
      draft.name = e.target.value;
    });
  }

  function handleTitleChange(e) {
    updatePerson(draft => {
      draft.artwork.title = e.target.value;
    });
  }

  function handleCityChange(e) {
    updatePerson(draft => {
      draft.artwork.city = e.target.value;
    });
  }

  function handleImageChange(e) {
    updatePerson(draft => {
      draft.artwork.image = e.target.value;
    });
  }

  return (
    <>
      <label>
        Name:
        <input
          value={person.name}
          onChange={handleNameChange}
        />
      </label>
      <label>
        Title:
        <input
          value={person.artwork.title}
          onChange={handleTitleChange}
        />
      </label>
      <label>
        City:
        <input
          value={person.artwork.city}
          onChange={handleCityChange}
        />
      </label>
      <label>
        Image:
        <input
          value={person.artwork.image}
          onChange={handleImageChange}
        />
      </label>
      <p>
        <i>{person.artwork.title}</i>
        {' by '}
        {person.name}
        <br />
        (located in {person.artwork.city})
      </p>
      <img
        src={person.artwork.image}
        alt={person.artwork.title}
      />
    </>
  );
}

```

##  Set

使用数组的一个小缺点是，对于每个项目，你都需要调用 selectedIds.includes(letter.id) 来检查它是否被选中。如果数组非常大，则这可能会成为性能问题，因为带有 includes() 的数组搜索需要线性时间，并且你正在为每个单独的项目执行此搜索。

要解决这个问题，你可以在 state 中使用一个 Set 对象，它提供了快速的 has() 操作：
```tsx=
import { useState } from 'react';
import { letters } from './data.js';
import Letter from './Letter.js';

export default function MailClient() {
  const [selectedIds, setSelectedIds] = useState(
    new Set()
  );

  const selectedCount = selectedIds.size;

  function handleToggle(toggledId) {
    // Create a copy (to avoid mutation).
    const nextIds = new Set(selectedIds);
    if (nextIds.has(toggledId)) {
      nextIds.delete(toggledId);
    } else {
      nextIds.add(toggledId);
    }
    setSelectedIds(nextIds);
  }

  return (
    <>
      <h2>Inbox</h2>
      <ul>
        {letters.map(letter => (
          <Letter
            key={letter.id}
            letter={letter}
            isSelected={
              selectedIds.has(letter.id)
            }
            onToggle={handleToggle}
          />
        ))}
        <hr />
        <p>
          <b>
            You selected {selectedCount} letters
          </b>
        </p>
      </ul>
    </>
  );
}

```

## 相同位置保留狀態(state)
```tsx=
import { useState } from 'react';

export default function App() {
  const [isFancy, setIsFancy] = useState(false);
  if (isFancy) {
    return (
      <div>
        <Counter isFancy={true} />
        <label>
          <input
            type="checkbox"
            checked={isFancy}
            onChange={e => {
              setIsFancy(e.target.checked)
            }}
          />
          使用好看的样式
        </label>
      </div>
    );
  }
  return (
    <div>
      <Counter isFancy={false} />
      <label>
        <input
          type="checkbox"
          checked={isFancy}
          onChange={e => {
            setIsFancy(e.target.checked)
          }}
        />
        使用好看的样式
      </label>
    </div>
  );
}

function Counter({ isFancy }) {
  const [score, setScore] = useState(0);
  const [hover, setHover] = useState(false);

  let className = 'counter';
  if (hover) {
    className += ' hover';
  }
  if (isFancy) {
    className += ' fancy';
  }

  return (
    <div
      className={className}
      onPointerEnter={() => setHover(true)}
      onPointerLeave={() => setHover(false)}
    >
      <h1>{score}</h1>
      <button onClick={() => setScore(score + 1)}>
        加一
      </button>
    </div>
  );
}

```
你可能以为当你勾选复选框的时候 state 会被重置，但它并没有！这是因为 两个 <Counter /> 标签被渲染在了相同的位置。 React 不知道你的函数里是如何进行条件判断的，它只会“看到”你返回的树。

在这两种情况下，App 组件都会返回一个包裹着 <Counter /> 作为第一个子组件的 div。这就是 React 认为它们是 同一个 <Counter /> 的原因。你可以认为它们有相同的“地址”：根组件的第一个子组件的第一个子组件。不管你的逻辑是怎么组织的，这就是 React 在前后两次渲染之间将它们进行匹配的方式。


## 相同位置的不同组件会使 state 重置
![preserving_state_diff_pt1](https://hackmd.io/_uploads/rJ30Ze2a1e.png)
当 Counter 变为 p 时，Counter 会被移除，同时 p 被添加。
```tsx=
import { useState } from 'react';

export default function App() {
  const [isPaused, setIsPaused] = useState(false);
  return (
    <div>
      {isPaused ? (
        <p>待会见！</p> 
      ) : (
        <Counter /> 
      )}
      <label>
        <input
          type="checkbox"
          checked={isPaused}
          onChange={e => {
            setIsPaused(e.target.checked)
          }}
        />
        休息一下
      </label>
    </div>
  );
}

function Counter() {
  const [score, setScore] = useState(0);
  const [hover, setHover] = useState(false);

  let className = 'counter';
  if (hover) {
    className += ' hover';
  }

  return (
    <div
      className={className}
      onPointerEnter={() => setHover(true)}
      onPointerLeave={() => setHover(false)}
    >
      <h1>{score}</h1>
      <button onClick={() => setScore(score + 1)}>
        加一
      </button>
    </div>
  );
}

```

:::info
如果你想在重新渲染时保留 state，几次渲染中的树形结构就应该相互“匹配”。结构不同就会导致 state 的销毁，因为 React 会在将一个组件从树中移除时销毁它的 state。
:::


## 使用 key 来重置 state
:::info
相同位置想重置state的方式
:::

```tsx=
import { useState } from 'react';

export default function Scoreboard() {
  const [isPlayerA, setIsPlayerA] = useState(true);
  return (
    <div>
      {isPlayerA ? (
        <Counter key="Taylor" person="Taylor" />
      ) : (
        <Counter key="Sarah" person="Sarah" />
      )}
      <button onClick={() => {
        setIsPlayerA(!isPlayerA);
      }}>
        下一位玩家！
      </button>
    </div>
  );
}

function Counter({ person }) {
  const [score, setScore] = useState(0);
  const [hover, setHover] = useState(false);

  let className = 'counter';
  if (hover) {
    className += ' hover';
  }

  return (
    <div
      className={className}
      onPointerEnter={() => setHover(true)}
      onPointerLeave={() => setHover(false)}
    >
      <h1>{person} 的分数：{score}</h1>
      <button onClick={() => setScore(score + 1)}>
        加一
      </button>
    </div>
  );
}

```

在 Taylor 和 Sarah 之间切换不会使 state 被保留下来。因为 你给他们赋了不同的 key：

```tsx=
{isPlayerA ? (
  <Counter key="Taylor" person="Taylor" />
) : (
  <Counter key="Sarah" person="Sarah" />
)}
```

:::warning
请记住 key 不是全局唯一的。它们只能指定 父组件内部 的顺序。
:::

## Reducer
```tsx=
export default function tasksReducer(tasks, action) {
  switch (action.type) {
    case 'added': {
      return [
        ...tasks,
        {
          id: action.id,
          text: action.text,
          done: false,
        },
      ];
    }
    case 'changed': {
      return tasks.map((t) => {
        if (t.id === action.task.id) {
          return action.task;
        } else {
          return t;
        }
      });
    }
    case 'deleted': {
      return tasks.filter((t) => t.id !== action.id);
    }
    default: {
      throw Error('未知 action：' + action.type);
    }
  }
}

```

## Context
### Context 的使用场景 
* 主题： 如果你的应用允许用户更改其外观（例如暗夜模式），你可以在应用顶层放一个 context provider，并在需要调整其外观的组件中使用该 context。
* 当前账户： 许多组件可能需要知道当前登录的用户信息。将它放到 context 中可以方便地在树中的任何位置读取它。某些应用还允许你同时操作多个账户（例如，以不同用户的身份发表评论）。在这些情况下，将 UI 的一部分包裹到具有不同账户数据的 provider 中会很方便。
* 路由： 大多数路由解决方案在其内部使用 context 来保存当前路由。这就是每个链接“知道”它是否处于活动状态的方式。如果你创建自己的路由库，你可能也会这么做。
* 状态管理： 随着你的应用的增长，最终在靠近应用顶部的位置可能会有很多 state。许多遥远的下层组件可能想要修改它们。通常 将 reducer 与 context 搭配使用来管理复杂的状态并将其传递给深层的组件来避免过多的麻烦。

## 脱围机制（Escape Hatches）
:::info
有些组件可能需要控制和同步 React 之外的系统。例如，你可能需要使用浏览器 API 聚焦输入框，或者在没有 React 的情况下实现视频播放器，或者连接并监听远程服务器的消息。在本章中，你将学习到一些脱围机制，让你可以“走出” React 并连接到外部系统。大多数应用逻辑和数据流不应该依赖这些功能。
:::

```tsx=
import { useRef } from 'react';

export default function Counter() {
  let ref = useRef(0);

  function handleClick() {
    ref.current = ref.current + 1;
    alert('你点击了 ' + ref.current + ' 次!');
  }

  return (
    <button onClick={handleClick}>
      点我！
    </button>
  );
}

```


useRef 是 React 提供的一個 Hook，主要用於存取 DOM 元素或保存可變值，且不會因元件重新渲染而改變其值。以下是它的詳細功能與使用方式：
基本概念
useRef 返回一個包含 .current 屬性的物件，初始值由 useRef(initialValue) 中的 initialValue 設定.

該物件在元件的整個生命週期中保持持久性，不會因重新渲染而被重置.

修改 .current 屬性不會觸發元件重新渲染.
主要用途
1. 存取 DOM 元素
useRef 最常用於直接操作 DOM 元素，例如聚焦輸入框、取得元素屬性等。
```txt=
import React, { useRef } from 'react';

function InputFocus() {
  const inputRef = useRef(null);

  const handleFocus = () => {
    inputRef.current.focus(); // 將焦點設置到 input 元素
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={handleFocus}>Focus Input</button>
    </div>
  );
}

```
在此範例中，按下按鈕時，輸入框會獲得焦點

2. 保存可變值
useRef 可用於保存不需要觸發重新渲染的值，例如計數器、計時器 ID 等。

範例：
```tsx=
import React, { useRef } from 'react';

function Timer() {
  const timerId = useRef(null);

  const startTimer = () => {
    timerId.current = setInterval(() => {
      console.log('Timer running');
    }, 1000);
  };

  const stopTimer = () => {
    clearInterval(timerId.current);
  };

  return (
    <div>
      <button onClick={startTimer}>Start Timer</button>
      <button onClick={stopTimer}>Stop Timer</button>
    </div>
  );
}

```
此範例使用 useRef 保存計時器 ID，避免因狀態改變導致不必要的重新渲染.

3. 保存前一次的 props 或 state
可以用 useRef 保存元件上一次的 props 或 state 值，用於比較或其他邏輯。

範例：
```tsx=
import React, { useEffect, useRef } from 'react';

function PreviousValue({ value }) {
  const previousValue = useRef();

  useEffect(() => {
    previousValue.current = value; // 保存前一次的 value
  }, [value]);

  return (
    <div>
      <p>Current Value: {value}</p>
      <p>Previous Value: {previousValue.current}</p>
    </div>
  );
}
```
此範例展示如何追蹤前一次的值.

注意事項
修改 useRef 的 .current 屬性不會觸發元件重新渲染，因此不適合用來保存 UI 資料。

每次渲染時，React 保證返回相同的 ref 對象，而不是新建一個。

若需操作 UI 更新，應使用 useState 而非 useRef.

總結
useRef 是 React 中一個強大的工具，可以用於：

操作 DOM 元素。

保存跨渲染仍需持久化的可變值。

優化性能，避免不必要的重新渲染。

它在處理非 UI 更新相關資料時非常實用，且能與其他 Hook（如 useEffect）搭配使用以實現更複雜的功能。

## useMemo
如果getFilteredTodos() 的耗时很长，或者你有很多 todos。这些情况下，当 newTodo 这样不相关的 state 变量变化时，你并不想重新执行 getFilteredTodos()。

你可以使用 useMemo Hook 缓存（或者说 记忆（memoize））一个昂贵的计算。

```tsx=
import { useMemo, useState } from 'react';

function TodoList({ todos, filter }) {
  const [newTodo, setNewTodo] = useState('');
  const visibleTodos = useMemo(() => {
    // ✅ 除非 todos 或 filter 发生变化，否则不会重新执行
    return getFilteredTodos(todos, filter);
  }, [todos, filter]);
  // ...
}
```

## useEffectEvent
:::info
使用 useEffectEvent 这个特殊的 Hook 从 Effect 中提取非响应式逻辑：
:::
```tsx=
function ChatRoom({ roomId, theme }) {
  const onConnected = useEffectEvent(() => {
    showNotification('Connected!', theme);
  });

  useEffect(() => {
    const connection = createConnection(serverUrl, roomId);
    connection.on('connected', () => {
      onConnected();
    });
    connection.connect();
    return () => connection.disconnect();
  }, [roomId]); // ✅ 声明所有依赖项
  // ...
```
这里的 onConnected 被称为 Effect Event。它是 Effect 逻辑的一部分，但是其行为更像事件处理函数。它内部的逻辑不是响应式的，而且能一直“看见”最新的 props 和 state。

现在你可以在 Effect 内部调用 onConnected Effect Event


## useSyncExternalStore 

:::info
useSyncExternalStore 是 React 18 引入的一個 Hook，專門設計用來讓 React 元件「訂閱」外部狀態（external store），並在外部狀態變動時自動觸發元件重新渲染。這個 Hook 解決了以往用 useEffect 或 useLayoutEffect 訂閱外部資料時，可能出現的狀態不一致或渲染時機問題，特別是在 React 的並發模式（Concurrent Mode）下
:::

主要用途
* 訂閱外部狀態管理庫：如 Redux、MobX、Zustand 等，不是直接用 React 狀態管理的外部 store。
* 訂閱瀏覽器 API 狀態：如網路連線狀態（navigator.onLine）、localStorage、location 等。 
* 自訂全局狀態管理：自己實作的全局 store，也可以用這個 Hook 來同步狀態。
* SSR 支援：支援服務端渲染（Server Side Rendering）時同步快照，避免 hydration 不一致。

```tsx=
import { useSyncExternalStore } from 'react';

function subscribe(callback) {
  window.addEventListener('online', callback);
  window.addEventListener('offline', callback);
  return () => {
    window.removeEventListener('online', callback);
    window.removeEventListener('offline', callback);
  };
}

function getSnapshot() {
  return navigator.onLine;
}

function useOnlineStatus() {
  return useSyncExternalStore(subscribe, getSnapshot);
}
```
* subscribe：一個函式，接收一個 callback，當外部 store 狀態變動時要呼叫這個 callback。它要返回一個「取消訂閱」的函式。
* getSnapshot：一個函式，每次元件渲染時呼叫，用來取得當前的外部狀態快照。
* getServerSnapshot（選填）：SSR 時用來取得伺服器端的狀態快照。

## Reference 
[React 中的 JSX 是什麼？為什麼它長得像 HTML？](https://realnewbie.com/coding/javascript/what-is-jsx-in-react-and-why-it-looks-like-html/)