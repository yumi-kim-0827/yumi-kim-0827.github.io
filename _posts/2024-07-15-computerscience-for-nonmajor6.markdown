---
layout: post
title: "비전공자를 위한 CS기초 7 ... 데이터의 표현"
date: 2024-07-15
categories: CS
---

### CS basis for non-major

# 자료 압축

자료를 저장하는데 필요한 공간을 줄이는 것입니다.

`비손실압축` 원래 자료와 동일하게 복원

`손실압축` 압축과정에서 약간의 정보를 잃어버림

# 텍스트의 표현

각 문자들에 대해서 이진 비트열을 할당합니다.

`확장형 ASCII 문자` 128문자까지 표현합니다.

`UNICODE 문자집합` 한자, 러시아 등 전세계 모든 문자를 포함하고 표현합니다.

# 텍스트의 압축

- 키워드 압축 : 자주 사용되는 단어를 한개의 문자로 대체합니다.

- 실행길이 압축:연속되는 문자를 압축합니다. ('xxxxxxdq' => 'x6dq')

- 후프만 압축 : 가장 자주 사용되는 문자를 후프만 코드로 대체합니다.

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
