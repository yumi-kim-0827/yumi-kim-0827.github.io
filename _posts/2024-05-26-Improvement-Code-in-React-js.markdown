---
layout: post
title: "좋은 리액트 코드를 위한 팁 ... React Tip for my code"
date: 2024-05-25
categories: React
---

🖥️

# 더 나은 리액트 코드를 위한 팁 정리

**1.다수의 인자를 받는 함수를 하나의 인자만 받는 함수로 변환합니다.**

이를 통해 재사용할 수 있는 유연성을 높일 수 있습니다.

_예시_
{% highlight ruby %}

export default function App() {
const [user, setUser] = useState({
name: "",
surname: "",
address: ""
});

// name 핸들러
const handleNameChange = (e) => {
setUser((prev) => ({
...prev,
name: e.target.value
}));
};

// surname 핸들러
const handleSurnameChange = (e) => {
setUser((prev) => ({
...prev,
surname: e.target.value
}));
};

// address 핸들러
const handleAddressChange = (e) => {
setUser((prev) => ({
...prev,
address: e.target.value
}));
};

return (
<>
<input value={user.name} onChange={handleNameChange} />
<input value={user.surname} onChange={handleSurnameChange} />
<input value={user.address} onChange={handleAddressChange} />
</>
);
}
{% endhighlight %}

이런식으로 인풋값을 업데이트 함수가 더 추가되면 유지보수면에서
효율이 낮아지고 코드 가독성도 안좋습니다.

3가지의 다른 인풋요소를 각각 핸들러 함수를 통해서 객체를 업데이트합니다.

3개의 핸들러 함수는 비슷한 작동과 폼을 가지고 있기 때문에, 하나의 함수로
다수의 인자를 받을 수 있습니다.

{% highlight ruby %}

export default function App() {
const [user, setUser] = useState({
name: "",
surname: "",
address: ""
});

const handleInputChange = (field) => {
return (e) => {
setUser((prev) => ({
...prev,
[field]: e.target.value
}));
};
};

return (

      <input value={user.name} onChange={handleInputChange("name")} />
      <input value={user.surname} onChange={handleInputChange("surname")} />
      <input value={user.address} onChange={handleInputChange("address")} />

      {JSON.stringify(user)}

);
}
{% endhighlight %}

**2.만능 함수를 만들지 말고, 기능을 분리합니다.**

모든 기능과 데이터를 관리하는 GOD 컴포넌트를 만들기보단 기능과 컴포넌트를 나누어서
모듈화를 하는 것이 더욱 적합합니다.

**3.조건문을 사용하기 보단 Object Map을 사용하세요.**

_예시_

{% highlight ruby %}
function Account({type}) {
let Component = UsualAccount

if (type === 'red') {
Component = redAccount
}

if (type === 'blue') {
Component = blueAccount
}

if (type === 'pink') {
Component = pinkAccount
}

return (

<div className='account'>
<Component />
</div>
)
}
{% endhighlight %}

해결

{% highlight ruby %}

const CONDITION_MAP = {
'usual': UsualAccount,
'red': redAccount,
'blue': blueAccount,
'pink': pinkAccount,
}

function Account({type}) {
const Component = ACCOUNTS_MAP[type]

return (

<div className='account'>
<Component />
</div>
)
}
{% endhighlight %}

변수나 조건에 따라 다양한 요소를 렌더링해야하는 경우 객체를 통해서
쉽고 더욱 구조적으로 이해하기 쉬워집니다. 또한 기능을 확장하는 것도 더욱 간편해집니다.

기능과 컴포넌트 분리를 통해 코드를 단순화하고 재사용성을 높혀
효율적으로 일할 수 있습니다.

> 코딩 연습과 프로젝트 진행하면서 느낀 점들을 솔직하게 적었어요. [Yumee Naver Blog]

> 저의 포트폴리오 사이트에요. [Yumee Portfolio site]

> 깃헙에서 더 자세히 알아볼 수 있어요. [Yumee GitHub]

[Yumee Naver Blog]: https://blog.naver.com/hello_world_yum
[Yumee Portfolio site]: https://github.com/jekyll/jekyll
[Yumee GitHub]: https://github.com/yumi-kim-0827
