---
layout: post
title: "비전공자를 위한 CS기초 5 ... 브라우저가 렌더링하는 과정"
date: 2024-06-18
categories: CS
---

### CS basis for non-major

# 브라우저의 구조

![ds1](https://github.com/yumi-kim-0827/yumi-kim-0827.github.io/assets/116349476/334ef113-2bd4-479f-9819-abbaaff2b1fa)

`사용자 인터페이스` : 뒤로가기 버튼, 홈, 주소창 등, 어떤 웹 페이지로 이동해도 항상 사용자에게 보여지는 영역

`브라우저 엔진` : 사용자 인터페이스와 렌더링 엔진 사이에서 상호작용하는 엔진

`렌더링 엔진` : 파싱하여 화면에 그려내는 엔진

`통신` : 웹 브라우저의 네트워크를 담당

`자바스크립트 해석기` : 자바스크립트를 인식해서 작동

`UI 백엔드` : 브라우저의 action을 담당

`자료 저장소` : 브라우저 렌더링에 필요한 자료를 저장

# 브라우저의 렌더링 과정

![ASD](https://github.com/yumi-kim-0827/yumi-kim-0827.github.io/assets/116349476/56a18cc6-d4d4-420b-80c2-96f183ca99d1)

- DNS에서 해당 주소의 ip 주소를 찾아옴.

- 얻어낸 ip 주소에서 HTML 과 CSS 파일을 가져옴

- HTML을 파싱하여 DOM TREE를 생성

- CSS를 파싱하여 CSSOM TREE를 생성

- DOM TREE와 CSSOM TREE를 결합하여 RENDER TREE 생성

- RENDER TREE를 통해 레이아웃의 위치와 크기를 계산하여 결정

- 화면에 요소들을 페인팅하여 웹 페이지를 렌더링

- 페인트 단계에서 여러개의 레이어를 합쳐서 웹 페이지를 보여준다.

<br/>
<br/>
<br/>

---

<br/>
<br/>
<br/>
> 코딩 연습과 프로젝트 진행하면서 느낀 점들을 솔직하게 적었어요. [Yumee Naver Blog]

> 저의 포트폴리오 사이트에요. [Yumee Portfolio site]

> 깃헙에서 더 자세히 알아볼 수 있어요. [Yumee GitHub]

[Yumee Naver Blog]: https://blog.naver.com/hello_world_yum
[Yumee Portfolio site]: https://github.com/jekyll/jekyll
[Yumee GitHub]: https://github.com/yumi-kim-0827
