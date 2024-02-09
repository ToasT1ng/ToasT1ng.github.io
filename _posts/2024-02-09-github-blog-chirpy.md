---
layout: post
title: Github 블로그 만들기 (feat. Chirpy 테마)  
date: 2024-02-09 04:07:01 +09:00
categories: [블로그]
tags: [gitblog, github-blog, github, chirpy]                    
---

## 테마 유람기
처음 Git 블로그를 만들었을 때 적용한 테마는 [Type-on-Strap](https://github.com/sylhare/Type-on-Strap) 이었다.

데모를 보면 알겠지만 매우 깔끔한 편이고, 포트폴리오 페이지도 따로 구성되어있어서 프로젝트 관리가 편하다.

그런데 글씨체도 별론거 같고.. 전체적인 레이아웃도 뭔가 별로 맘에 안들고... 여튼 디자인적인 단점들이 많이 보였다.

'커스터마이징 한다고 해서 이게 많이 나아질 수 있나? 그냥 나중에 더 좋은 테마를 찾아봐야겠다.' 이렇게 생각하고 넘어갔다.

오늘 미뤄뒀던 숙제를 하나 해치웠다. 아주 맘에 드는 테마를 찾은 것이다!

<br/>

## Chirpy 테마!
1) 기존 티스토리 블로그에서 사용하던 레이아웃과 비슷한 테마 없을까?  
2) 그러면서 코드 레이아웃이 적당히 예뻤으면 좋겠다.

여기 두 가지 조건에 부합하는 테마가 존재한다. 바로 [Chirpy](https://github.com/ToasT1ng/jekyll-theme-chirpy) 다.

테마의 데모 페이지를 확인해보고 다른 사람들은 어떻게 쓰고 있나 구글에 검색해보고 나니 아, 이거다! 싶었다.

그 길로 바로 세팅을 시작했다.

그런데 아래 두 개의 글을 참고하여 세팅하던 중, 계속 문제가 발생했다.    
> [Github 블로그 만들기 (1)](https://devpro.kr/posts/Github-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0-(1)/)       
[Jekyll Chirpy 테마 사용하여 블로그 만들기](https://www.irgroup.org/posts/jekyll-chirpy/)

![이미지](/assets/post_imgs/2024-02-10-github-blog-chirpy_git_action_error.png)

```
Error:  Logging at level: debug Configuration file: /github/workspace/./_config.yml Theme: jekyll-theme-chirpy github-pages 228 | Error: The jekyll-theme-chirpy theme could not be found.
```

왜 안되는걸까 답답해 죽는줄 알았는데 `.github` 디렉토리를 git에 등록해주지 않아서 그런 문제였다.

`.github` 아래 `pages-deploy.yml` 파일을 보니 Git Action Workflow 연관한 어떤 설정들이 지정되어있는 것 같다.

테마를 세팅한 사람이 뭔가 커스터마이징 해둔거 같은데 Git Action에 대해서 잘 모르므로... 자세한건 더 공부해봐야겠다.

<br/>

## 세팅

### 기본 설정
```yml
# The language of the webpage › http://www.lingoes.net/en/translator/langcode.htm
lang: ko-KR   # 상단 주소 확인

# Change to your timezone › https://kevinnovak.github.io/Time-Zone-Picker
timezone: Asia/Seoul  # 상단 주소 확인

# jekyll-seo-tag settings › https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/usage.md
title: ToasT1ng # 좌상단 아바타 밑에 큰 글씨
tagline: 끄적끄적 개발 블로그 # title 밑에 글씨
description: >- # 검색어를 위한 설정
  ToasT1ng의 끄적끄적 개발 블로그
url: "https://ToasT1ng.github.io"  # 본인 Git 블로그 주소에 맞게 변경
github:
  username: ToasT1ng # 본인 github 이름, 좌하단 링크 정보에서 사용됨
social:
  name: ToasT1ng # 하단 Footer에서 사용됨 (Powered by 있는곳)
  email: email@address.com # 본인 이메일 주소, 좌하단 링크 정보에서 사용됨
```

### 좌하단 링크 정보들 변경
`_data/contact.yml` 안의 정보들을 수정해주면 된다. 

링크를 새로 추가하고 싶은 경우, 아래와 같이 하면 된다.
```yml
# _data/contact.yml
- type: tistory
  icon: "fa-solid fa-t"  # https://fontawesome.com/icons 에서 검색해서 원하는 것으로 바꾸기
```
```yml
#_config.yml
tistory:
  url: https://toast1ng.tistory.com/
```
```html
<!-- includes/sidebar.html -->
<!-- 태그 정확하지 않음. 정확한 코드는 직접 확인할 것. -->
for entry in site.data.contact
    case entry.type
        when 'github', 'twitter'
            capture url
                https://{{ entry.type }}.com/{{ site[entry.type].username }}
            endcapture
        <!-- 이런식으로 추가 -->
        when 'tistory'
            capture url
                site[entry.type].url
                <!-- site ==> _config.yml  //  entry.type ==> tistory, github 등등 -->
```

### 좌상단 아바타 이미지 변경
```yml
#_config.yml
avatar: /assets/img/free-icon-bread-3348021.png  # 원하는 Local, CDN 등등의 주소로 설정하면 된다.
```

### 글 공유하기 관련 설정 변경
`_data/share.yml` 파일에서 적절히 삭제/추가/변경하면 된다.

<br/>

### 관련 주소
이 글을 보는 사람에게 도움이 될까하여, 나의 Git 블로그 레포 주소를 남기고 글을 마친다.
> [Git Repository](https://github.com/ToasT1ng/ToasT1ng.github.io)    
[필요 기본 세팅 업데이트 관련 Commit](https://github.com/ToasT1ng/ToasT1ng.github.io/commit/64ae77b287ceacbac13683d3b217958a2e45d835)

  


