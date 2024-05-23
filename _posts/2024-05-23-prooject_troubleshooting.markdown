---
layout: post
title: "Error of not finding of node (javascript)"
date: 2024-05-23
categories: Go React
---

🖥️

`이벤트 리스터의 오류와 해결`

근본적으로 회원가입 페이지와, 로그인 페이지의 기능을 하나의 스크립트 파일에 선언해서 생긴 문제입니다.
로그인 페이지에 없는 회원 가입 페이지의 기능 중 해당이 안되는 eventlistner의 선언으로 properties of null이라는
타입 에러가 생겼습니다.

{% highlight ruby %}
Uncaught TypeError: Cannot read properties of null (reading 'addEventListener')
{% endhighlight %}

해석해보자면 addEventListner 특정 요소에 특정 행동이 포착되면 작동하게끔 만드는 함수에서
특정 요소를 찾을 수 없어서 발생한 문제입니다.

이 문제를 해결하기 위해 우선적으로 옵셔널 체이닝 기업으로 해당 요소를 읽을 수 있을 경우에면
함수를 실행하도록 수정했습니다.

{% highlight ruby %}
element?.addEventListner('click', handleEvent);
{% endhighlight %}

실습을 진행하기 위해 임시방편으로 해결했던 문제는 로그인 페이지의 기능과
회원가입 페이지의 기능을 파일 분리를 통해 근본적으로 해결하도록 했습니다.

- 코딩 연습과 프로젝트 진행하면서 느낀 점들을 솔직하게 적었어요. [Yumee Naver Blog]
- 저의 포트폴리오 사이트에요. [Yumee Portfolio site]
- 깃헙에서 더 자세히 알아볼 수 있어요. [Yumee GitHub]

[Yumee Naver Blog]: https://blog.naver.com/hello_world_yum
[Yumee Portfolio site]: https://github.com/jekyll/jekyll
[Yumee GitHub]: https://github.com/yumi-kim-0827
