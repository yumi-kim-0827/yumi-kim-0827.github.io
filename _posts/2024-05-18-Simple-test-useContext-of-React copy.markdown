---
layout: post
title: "리액트 useContext 연습 ... Simple test of useContext for understanding (React js)"
date: 2024-05-18
categories: React
---

🖥️

React의 `useContext` 훅은 React 컴포넌트에서 전역으로 상태를 공유할 수 있게 해주는 기능입니다.
주로 react 애플리케이션에서 상태 관리를 위해 사용되며, 다른 컴포넌트 간에 데이터를 전달할 떄 유용합니다.

`CreateContext & Provider --- > useContext`

리액트의 CONTEXT 훅은 익히기 위해 다음과 같이 컴포넌트 구조를 구현하였습니다.
{% highlight ruby %}

<Grand1>
├─ <Child1>
│
├─ <Child2>
   │
   └─ <Child22>

{% endhighlight %}

Grand 1.jsx에서 생성한 name과 count state, 그리고 함수를 하위 컴포넌트와 공유할 것입니다.
`state값`을 내려주는 `valueContext`, `함수를 내려주는 FuncContext`로 따로 만들어
전역에 state값을 공유하고 자식 - 손자인 Child22에만 함수를 전달해줍니다.

{% highlight ruby %}

import React, { useState, createContext } from "react";
import Child1 from "./Child1";
import Child2 from "./Child2";

//컨택스트 선언
export const valueContext = createContext();
export const FuncContext = createContext();

const Grand1 = () => {
console.log(valueContext);
//값
const [name, setName] = useState("");
const [count, setCount] = useState(0);
//함수
const handleClickCount = () => {
setCount(count + 1);
};
const handleChangeName = () => {
setName("이름을 추가했어요!");
};
return (

<div class="test">
<h2>부모 컴포넌트 grand 1</h2>
<div class="child">
<valueContext.Provider value={{ name, count }}>
<Child1 />
<FuncContext.Provider value={{ handleClickCount, handleChangeName }}>
<Child2 />
</FuncContext.Provider>
</valueContext.Provider>
</div>
</div>
);
};

export default Grand1;

{% endhighlight %}

Child 1.jsx에서 생성한 name과 count state 값을 받아 호출합니다.
{% highlight ruby %}

import React, { useContext } from "react";
import { valueContext } from "./Grand1";

const Child1 = () => {
const data = useContext(valueContext);
console.log("Child1 자손 실행");

return (

<div className="test_child">
자식 컴포넌트 Child 1<p>카운트 : {data.count}</p>
<p>네임 : {data.name}</p>
</div>
);
};

export default Child1;

{% endhighlight %}

Child 2.jsx에서도 마찬가지로 state 값을 호출합니다.
{% highlight ruby %}
import React, { useContext } from "react";
import Child22 from "./Child22";
import { valueContext } from "./Grand1";

const Child2 = () => {
const data = useContext(valueContext);
console.log("Child2 자손 실행");

return (

<div className="test_child">
자식 컴포넌트 Child 2<p>카운트 : {data.count}</p>
<p>네임 : {data.name}</p>
<Child22 />
</div>
);
};

export default Child2;

{% endhighlight %}

버튼을 추가한 손자 컴포넌트 Child22에 함수를 전달하여
호출합니다.

{% highlight ruby %}

import React, { useContext } from "react";
import { FuncContext } from "./Grand1";

const Child22 = () => {
const data = useContext(FuncContext);
console.log("Child22 손자 실행");

return (

<div className="test_child">
손자 컴포넌트 Child 22<p>여기서 함수 실행</p>
<div>
<button onClick={data.handleChangeName}>이름추가</button>
<button onClick={data.handleClickCount}>더하기1</button>
</div>
</div>
);
};

export default Child22;

{% endhighlight %}

전역에서 count와 name값을 호출하고 손자인 Child22에서 함수를 호출하여 사용할 수 있습니다.

---

> 코딩 연습과 프로젝트 진행하면서 느낀 점들을 솔직하게 적었어요. [Yumee Naver Blog]

> 저의 포트폴리오 사이트에요. [Yumee Portfolio site]

> 깃헙에서 더 자세히 알아볼 수 있어요. [Yumee GitHub]

[Yumee Naver Blog]: https://blog.naver.com/hello_world_yum
[Yumee Portfolio site]: https://github.com/jekyll/jekyll
[Yumee GitHub]: https://github.com/yumi-kim-0827
