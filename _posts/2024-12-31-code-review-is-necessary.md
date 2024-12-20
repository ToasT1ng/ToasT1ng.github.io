---
layout: post
title: 코드리뷰? 귀찮은데 왜 해?
date: 2024-12-31 00:01:01 +09:00
categories: [개발, 코드리뷰]
tags: [코드 리뷰, Code Review]                    
---

# 코드리뷰? 귀찮은데 왜 해야 돼?
<img src="/assets/img/post/LGTM.jpg">

코드리뷰. 개발자 중에 이 단어를 모르는 사람은 없습니다.

코드리뷰를 아직 안했던 시절에 저는 이렇게 생각했었습니다.

"코드리뷰 좋다 좋다 말만 들었지 대체 뭐가 좋다는거야? 왜 해야되는건데? 또 쓸데없는 프로세스 하나만 늘어나는거 아냐?"

## 왜 안해야하나?
우리팀은 아직 안된다고 생각하고 있나요?

여러분의 팀이 어떤 상황에 놓여있는지 잘은 모르겠지만, 코드리뷰는 반드시 해야만 합니다!

왜냐고요? 지금부터 설명 드리겠습니다. 조금만 더 시간을 내서 글을 읽어주세요.

## 코드리뷰 반드시 하세요!
### 첫번째 장점 : 실력 상승
여러분 팀이 어떤 상황에 놓여있던 간에 구성원 전체 실력 상승 효과를 **반드시** 볼 수 있습니다.

구성원간에 실력 차이가 조금 있는 팀이라면?
- 더 낮은 실력을 갖고 있는 사람의 실력이 비약적으로 상승할 수 있습니다.
- 시니어의 코드 노하우를 자연스럽게 배울 수 있게 되어 팀 전력에 보탬이 될 수 있게 됩니다.
- 또한 주니어라고 배울점이 없지 않죠.
- 시니어가 보지 못하는 부분을 주니어가 봐줄 수도 있습니다.

비슷한 실력을 갖고 있는 팀이라면?
- 함께 실력이 상승하는 효과를 누릴 수 있습니다.
- 사람마다 더 잘하는 부분이 다릅니다. ~~상호보완되어 실력이 다 같이 상승됩니다.
 
모두의 실력이 상승되면?
- 더 많은 시도를 할 수 있게 된다 => 기능 개발의 속도가 빨라진다
- 빠른 기능 개발이 가능해진다!

### 두번째 장점 : 코드 컨벤션 생성
서로의 코드를 읽으며 자연스레 비슷하게 코드를 짤 수 있게 됩니다.

컨벤션은 만들어나가는 것입니다. 처음부터 모든 규칙을 다 정할순 없습니다.

<img src="/assets/img/post/code_review_war.png">

컨벤션이 맞춰지면?
1. 깨진 창문이론에서 한걸음 멀어질 수 있다. (유지보수성이 확대된다.)
2. 코드 생산성이 높아질 수 있다. (네이밍 규칙이나 프로젝트 구조에 대해 고민하는데 드는 시간이 감소된다.)
- 빠르고 안정적인 유지보수가 가능해진다!

### 세번째 장점 : 휴먼 에러 감소
여러 명이 교차 검증 가능

### 한줄 요약
코드리뷰는 빠르고 안정적이고 정확한 코드를 만들 수 있습니다!

<br/>

---
# 코드리뷰엔 장점만 있나?
코드 리뷰를 하면 무조건 좋아지기만 할까요? 안좋아지는건 없을까요?
모든 기술이 그렇듯, 코드리뷰에도 일부 단점이 존재합니다. 
## 코드리뷰가 내 맘을 아프게 해
<img src="/assets/img/post/how_was_your_review_today.webp">

처음 코드리뷰를 받아보면, 조금 우울해질 수도 있습니다.

컨벤션이 서로 맞지 않은 상태이기 때문에 그 부분에 대해서 얘기하는 것 만으로도 많은 양의 코멘트가 쌓일수도 있어요.

코멘트가 많으면 많을 수록 자괴감이 들 수도 있습니다. 내가 만든 코드가 그렇게 별론가..?

아닙니다. 세상에 나쁜 코드는 없습니다. (~~Clean Code에선 그렇게 생각하지 않는것 같지만..~~)

<img src="/assets/img/post/good_code_bad_code.png">

우리는 단지 "서로에게 좋은" 코드를 만드는 법을 모르고 있는거에요.

코드리뷰로 같이 맞춰나가면 됩니다.

후술할 Pn룰로 이런 긴장감을 완화시킬 수도 있어요!

## 텍스트로 소통하려니까 너무 어렵다..
코드와 텍스트로 이루어지는 비대면적 소통이 어렵게 느껴질 수도 있어요.

비대면적인 소통은 대면소통에서 얻어지는 "뉘앙스"가 거세되어지기 때문에 쉽게 오해가 생길 수 있고,   
이 뉘앙스를 글로 표현하기 위해 오랜시간 고민하는 것보다 말로 소통하는게 더 빠르고 정확하다고 여길 수도 있죠.

너무 어렵다면 처음엔 육성으로 소통해도 괜찮습니다.

육성으로 소통하다보면 기록에 대한 필요성이 자연스럽게 생기게 됩니다. 인간은 망각의 동물이기에 쉽게 잊어버리곤 하니까요.

일단 육성으로 리뷰하고, 리뷰 결론을 정리해서 코멘트로 남겨보세요. 

조금 익숙해지면 육성 리뷰 빈도를 줄이고, 텍스트 리뷰 빈도를 서서히 높여보세요. 

이렇게하다보면 자연스럽게 비대면적인 소통에 익숙해지게 됩니다.

## 개발할 시간도 부족한데 리뷰는 또 언제하나..
<img src="/assets/img/post/wake_up_you_have_to_do_code_review.jpeg">

시간이 촉박할땐 코드 리뷰가 압박으로 느껴질 수도 있습니다.

개발자에게 시간은 금입니다. 그렇기 때문에 더더욱 리뷰를 해야합니다.

<br/>

---
# 코드리뷰. 그게 뭔데. 그거 어떻게 하는건데.
문득 나의 첫 코드리뷰 코멘트가 어떤 내용이었는지 궁금해져서 찾아봤습니다.

## 기초
- Git 브랜치 관리 방법
- PR 템플릿

## 이런 부분을 중점적으로 생각해요

<img src="/assets/img/post/what_are_these_lines_for.png">

- 아주 간단해요
- 제일 중요하게 생각하는 부분
- 이외 더 생각해야하는 부분

## 이런 마음가짐을 갖고 해요
- 통과된 PR은 우리 모두의 책임입니다.
  - 오늘 우리 팀이 새로운 기능을 성공적으로 배포했습니다.
  - 아니, 그런줄로만 알았습니다.
  - 저녁 시간쯤 되니 갑자기 크리티컬한 버그가 발견됐습니다.
  - 으악. 누가 이 버그를 만든거지? 아니 이거 ㅇㅇ님이 작성한 코드잖아?
  - 누가 PR 통과 시켰어?!
  - 어.. 나네..
  -
- 내 코드를 리뷰해주는 사람을 배려해야합니다.
  - 내 시간이 소중한 만큼 다른 사람의 시간도 소중합니다.
  - 같이 일하는 동료의 시간을 배려할 수 있어야합니다.
  - 그러기 위해 다음과 같은 마음가짐이 필요합니다.
    - 리뷰를 위한 배경 지식을 최대한 상세히 기재하기


# 코드리뷰를 시작했나요?
## 코드리뷰를 더 잘하려면?
이런것들을 공부해보는게 좋아요
- 클린코드 or 리팩터링 연관 책 읽기
- 클린 아키텍쳐 책 읽기
## 코드리뷰 방법론
- Pn룰, Dn룰
- 작은 PR 규칙



