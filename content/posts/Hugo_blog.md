---
title: "Github.io로 배포하는 Hugo 블로그 시작하기"
date: 2022-04-04T23:08:07+09:00
categories:
- Hugo
- Blog
tags:
- hugo
- blog
- github
keywords:
- tech
- hugo
#thumbnailImage: //example.com/image.jpg
---


## Hugo 설치

- 설치

```bash
brew install hugo
```

- 버전 확인

```bash
hugo version
```

→ 출력 결과 :  `hugo v0.95.0+extended darwin/arm64 BuildDate=unknown`

→ 정상 설치

## Github repository

blog

<USERNAME>.github.io

두 개의 레포지토리 준비하기

## Hugo로 프로젝트 만들기

- 현재 위치 확인

출력결과로 현재 경로 확인

```bash
$ pwd                          
/Users/jules/Projects/Projects
```

- hugo 프로젝트 생성

```bash
$ hugo new site blog  
# 생성 완료되면 아래 문구가 출력됨.         
Congratulations! Your new Hugo site is created in /Users/jules/Projects/Projects/blog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cfd984eb-3081-4911-8490-28136244e68a/Untitled.png)

만들어진 프로젝트 구조 ⬇️

```
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
```

```bash
$ pwd
# 프로젝트 루트 경로
/Users/.../blog

$ git init
# git initialize
$ git branch -M main
# 브렌치를 main으로 변경

# git submodule add https://github.com/<theme 경로>.git themes/<theme 이름>
$ git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder

# cp themes/hugo-tranquilpeak-theme/exampleSite/config.toml config.toml
```

**휴고 테마 페이지**

[https://themes.gohugo.io/](https://themes.gohugo.io/)

→ `Downloads`를 눌러보면 해당 `Github` 페이지로 이동되는데, 설치할 수 있는 방법이 적혀져 있다.

`pwd`로 현재 위치를 확인하고 

blog 폴더 내에서 테마를 다운로드 한다.

```bash
git submodule add https://github.com/luizdepra/hugo-coder.git themes/hugo-coder
```

`blog/themes` 디렉토리의 구조

```bash
└── hugo-coder
    ├── archetypes
    ├── docs
    │   └── img
    ├── exampleSite
    │   ├── content
    │   │   └── post
    │   └── static
    │       └── img
    ├── i18n
    ├── images
    ├── layouts
    │   ├── _default
    │   ├── partials
    │   │   ├── internal
    │   │   └── post
    │   ├── shortcodes
    │   └── taxonomy
    ├── src
    │   ├── images
    │   ├── js
    │   └── scss
    │       ├── base
    │       ├── components
    │       ├── layouts
    │       ├── pages
    │       ├── themes
    │       └── utils
    │           └── mixins
    ├── static
    │   ├── css
    │   ├── images
    │   └── js
    ├── tasks
    │   ├── config
    │   └── register
    ├─ theme.toml
    ├─ ...
```

- `blog/themes/hugo-coder/exampleSite/config.toml`을 복사해서 `blog/config.toml`에 붙여넣는다.

```bash
# 여기를 변경해야 한다.
# https://<username>.github.io/
baseURL = "https://jinieun.github.io/"

```

- 전체 - `blog/config.toml`
    
    ```bash
    baseURL = "https://JiniEun.github.io/"
    title = "jinieun"
    theme = "hugo-coder"
    languageCode = "en"
    defaultContentLanguage = "en"
    paginate = 20
    pygmentsStyle = "bw"
    pygmentsCodeFences = true
    pygmentsCodeFencesGuessSyntax = true
    enableEmoji = true
    # Enable Disqus comments
    # disqusShortname = "yourdiscussshortname"
    
    [params]
    author = "Eun Jin"
    # license = '<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA-4.0</a>'
    description = "John Doe's personal website"
    keywords = "blog,developer,personal"
    info = ["Backend Developer", "Java Developer"]
    avatarURL = "images/avatar.jpg"
    #gravatar = "john.doe@example.com"
    dateFormat = "January 2, 2006"
    since = 2019
    # Git Commit in Footer, uncomment the line below to enable it
    commit = "https://github.com/luizdepra/hugo-coder/tree/"
    # Right To Left, shift content direction for languagues such as Arabic
    rtl = false
    # Specify light/dark colorscheme
    # Supported values:
    # "auto" (use preference set by browser)
    # "dark" (dark background, light foreground)
    # "light" (light background, dark foreground) (default)
    colorScheme = "auto"
    # Hide the toggle button, along with the associated vertical divider
    hideColorSchemeToggle = false
    # Series see also post count
    maxSeeAlsoItems = 5
    # Custom CSS
    customCSS = []
    # Custom SCSS, file path is relative to Hugo's asset folder (default: {your project root}/assets)
    customSCSS = []
    # Custom JS
    customJS = []
    
    # If you want to use fathom(https://usefathom.com) for analytics, add this section
    # [params.fathomAnalytics]
    # siteID = "ABCDE"
    # serverURL = "analytics.example.com" # Default value is cdn.usefathom.com, overwrite this if you are self-hosting
    
    # If you want to use plausible(https://plausible.io) for analytics, add this section
    # [params.plausibleAnalytics]
    # domain = "example.com"
    # serverURL = "analytics.example.com" # Default value is plausible.io, overwrite this if you are self-hosting or using a custom domain
    
    # If you want to use goatcounter(https://goatcounter.com) for analytics, add this section
    # [params.goatCounter]
    # code = "code"
    
    # If you want to use Cloudflare Web Analytics(https://cloudflare.com) for analytics, add this section
    # [params.cloudflare]
    # token = "token"
    
    # If you want to use Matomo(https://matomo.org) for analytics, add this section
    # [params.matomo]
    # siteID = "ABCDE" # Default value is "1", overwrite this if you are cloud-hosting
    # serverURL = "analytics.example.com" # For cloud-hosting, use provided URL, e.g. example.matomo.cloud
    
    # If you want to use Google Tag Manager(https://analytics.google.com/) for analytics, add this section
    # [params.googleTagManager]
    # id = "gid"
    
    # If you want to implement a Content-Security-Policy, add this section
    [params.csp]
    childsrc = ["'self'"]
    fontsrc = ["'self'", "https://fonts.gstatic.com", "https://cdn.jsdelivr.net/"]
    formaction = ["'self'"]
    framesrc = ["'self'"]
    imgsrc = ["'self'"]
    objectsrc = ["'none'"]
    stylesrc = [
      "'self'",
      "'unsafe-inline'",
      "https://fonts.googleapis.com/",
      "https://cdn.jsdelivr.net/"
    ]
    scriptsrc = [
      "'self'", 
      "'unsafe-inline'", 
      "https://www.google-analytics.com",
      "https://cdn.jsdelivr.net/"
    ]
    prefetchsrc = ["'self'"]
    # connect-src directive – defines valid targets for to XMLHttpRequest (AJAX), WebSockets or EventSource
    connectsrc = ["'self'", "https://www.google-analytics.com"]
    
    [taxonomies]
    category = "categories"
    series = "series"
    tag = "tags"
    author = "authors"
    
    [[params.social]]
    name = "Github"
    icon = "fa fa-2x fa-github"
    weight = 1
    url = "https://github.com/jinieun/"
    
    #[[params.social]]
    #name = "Gitlab"
    #icon = "fa fa-2x fa-gitlab"
    #weight = 2
    #url = "https://gitlab.com/johndoe/"
    
    #[[params.social]]
    #name = "Twitter"
    #icon = "fa fa-2x fa-twitter"
    #weight = 3
    #url = "https://twitter.com/johndoe/"
    
    #[[params.social]]
    #name = "LinkedIn"
    #icon = "fa fa-2x fa-linkedin"
    #weight = 4
    #url = "https://www.linkedin.com/in/johndoe/"
    
    #[[params.social]]
    #name = "Medium"
    #icon = "fa fa-2x fa-medium"
    #weight = 5
    #url = "https://medium.com/@johndoe"
    
    [[params.social]]
    name = "Blog"
    icon = "fa fa-2x fa-tag"
    weight = 5
    url = "https://jules-jc.tistory.com/"
    
    [[params.social]]
    name = "RSS"
    icon = "fa fa-2x fa-rss"
    weight = 6
    url = "https://myhugosite.com/index.xml"
    rel = "alternate"
    type = "application/rss+xml"
    
    [languages.en]
    languageName = ":us:"
    
    [[languages.en.menu.main]]
    name = "About"
    weight = 1
    url = "about/"
    
    [[languages.en.menu.main]]
    name = "Blog"
    weight = 2
    url = "posts/"
    
    [[languages.en.menu.main]]
    name = "Projects"
    weight = 3
    url = "projects/"
    
    [[languages.en.menu.main]]
    name = "Contact me"
    weight = 5
    url = "contact/"
    
    [languages.pt-kr]
    languageName = ":kr:"
    title = "김은진"
    
    [languages.pt-kr.params]
    author = "김은진"
    info = "백엔드 개발자"
    description = "백엔드 개발자"
    keywords = "blog,developer,pessoal"
    
    [[languages.pt-kr.menu.main]]
    name = "About"
    weight = 1
    url = "about/"
    
    [[languages.pt-kr.menu.main]]
    name = "Blog"
    weight = 2
    url = "posts/"
    
    [[languages.pt-kr.menu.main]]
    name = "Projets"
    weight = 3
    url = "projects/"
    
    [[languages.pt-kr.menu.main]]
    name = "Contact"
    weight = 5
    url = "contact/"
    ```
    

hugo 실행

→ 로컬 서버 실행

```bash
$ hugo server
Start building sites … 
hugo v0.95.0+extended darwin/arm64 BuildDate=unknown

                   | EN | PT-BR  
-------------------+----+--------
  Pages            | 11 |    11  
  Paginator pages  |  0 |     0  
  Non-page files   |  0 |     0  
  Static files     |  5 |     5  
  Processed images |  0 |     0  
  Aliases          |  1 |     0  
  Sitemaps         |  2 |     1  
  Cleaned          |  0 |     0  

Built in 53 ms
Watching for changes in /Users/jules/Projects/Projects/blog/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /Users/jules/Projects/Projects/blog/config.toml, /Users/jules/Projects/Projects/blog/themes/hugo-coder/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

→ [localhost:1313](http://localhost:1313) 들어가면 확인 가능

→ `hugo server -D` : 웹서버 실행명령.

→ D 옵션은 Draft문서도 표시한다는 옵션이다. 위에서 만든 helloworld.md 파일을 열어보면 문서의 front matter 부분에 `draft = True`라고 되어있을 것이다. 현재 작업중인 문서라는 의미이다. 그냥 `hugo`라는 명령어는 웹사이트를 빌드해주는데, `hugo server` 명령어는 빌드와 웹서버 실행을 같이 해준다.

## Git repository 연결

`pwd`로 현재 위치를 확인하고 blog 폴더 내에서 실행한다.

blog→ blog repo에 연결하기

```bash
git remote add origin https://github.com/JiniEun/blog.git
```

#blog/public → <USERNAME>.github.io에 연결

```bash
git submodule add -b main https://github.com/JiniEun/JiniEun.github.io.git public
```

blog/deploy.sh

→ 배포를 보다 쉽게 하기 위해서 쉘 스크립트를 작성한다. `blog` 프로젝트 루트 디렉토리에, `deploy.sh`를 만들고 다음을 입력한다.

```bash
#!/bin/bash

echo -e "\033[0;32mDeploying updates to GitHub...\033[0m"

# Build the project.
# hugo -t <여러분의 테마>
hugo -t hugo-coder

# Go To Public folder, sub module commit
cd public
# Add changes to git.
git add .

# Commit changes.
msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

# Push source and build repos.
git push origin main

# Come Back up to the Project Root
cd ..

# blog 저장소 Commit & Push
git add .

msg="rebuilding site `date`"
if [ $# -eq 1 ]
  then msg="$1"
fi
git commit -m "$msg"

git push origin main
```

터미널에 실행하기

```bash
# deploy.sh 실행 파일 권한 부여
$ chmod 777 deploy.sh

# 배포 실행
$ ./deploy.sh
```

## 새로운 글 작성하기

```bash
# hugo new posts/<원하는 path>/파일 이름.md
$ hugo new posts/test.md
Content "/Users/user/workspace/blog/content/post/test.md" created
```

`blog/content/posts/` 에 `test.md`가 생성된다. 그걸 수정해서 블로그를 작성하면 되겠다.터미널에서 로컬 서버 열어본다.

```
# 로컬 서버 실행
$ hugo server -D
# http://localhost:1313 접속하여 확인
```

- test.md
    
    ```bash
    ---
    title: "Test"
    date: 2022-03-23T16:50:52+09:00
    categories:
    - category
    - subcategory
    tags:
    - tag1
    - tag2
    keywords:
    - tech
    #thumbnailImage: //example.com/image.jpg
    ---
    
    <!--more-->
    테스트입니다.
    ```
    

## 댓글 위젯 U**tterances 설치**

[https://github.com/apps/utterances](https://github.com/apps/utterances)

블로그 레포지터리(repo)에 Utterances 앱을 설치한다.

Utterances를 사용하면 댓글 기능을 구현하는 데 드는 시간은 10분이면 충분하다. 그만큼 간단하기 때문이다.

> 블로그 레포지터리의 공개 상태는 Public으로 설정되어 있어야만 Utterances 플러그인을 사용 가능하다.
> 
- [utterances 설치 홈페이지](https://github.com/apps/utterances)에 접속한 후 본인의 깃허브 계정으로 로그인한다.
- 이후 우측에 초록색 Install 버튼 클릭
- Only select repositories → 블로그 repo 선택 (내 경우는 seyslee/blog)

### **utternaces 작성**

[https://utteranc.es/](https://utteranc.es/)

[utterances 공식 홈페이지](https://utteranc.es/)
에 접속한다. 중간에 configuration 이후 ‘repo:’ 값이 있다.

repo:

```bash
jinieun/blog-comments
```

blog/themes/hugo-coder/layouts/partials/post/disqus.html

```bash
<!--추가 코드-->
<script src="https://utteranc.es/client.js" 
repo="JiniEun/blog-comments" 
issue-term="title" 
theme="github-light"
  crossorigin="anonymous" async>
  </script>
```

### **Hugo에 커스텀 shorcodes 생성**

> 간단한 설명은 여기 참고.자세한 사용법은 이 튜토리얼 영상 참고
> 
- `themes/본인테마/layouts` 디렉토리에 `shortcodes` 폴더를 생성
- `shortcodes` 폴더 내에 `gist.html` 파일 생성 (파일명은 상관없지만 gist로 하는게 정체성이 분명함)
- `gist.html`에 아래 코드 입력

```bash
<script type="text/javascript" src="http://gist.github.com/{{ .Get 0 }}.js"></script>
```

- 여기서 `{{ . GET 0 }}`에 들어갈 부분이 위에서 복사해둔 각 gist의 sha1 hash(url 끝부분)이다.

### **shortcode 삽입**

- 글 내용 중 코드가 들어갈 부분에 {{< gist url끝부분 >}} 을 넣어주면,

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/40b44326-cd91-42a4-b084-09609e9788d5/Untitled.png)

→ 위 이미지 처럼 마크다운 파일(.md)에도 gist 삽입 가능


Reference

# If you want to implement a Content-Security-Policy, add this section 부분 참고 사이트

[https://developers.google.com/web/fundamentals/security/csp?hl=ko](https://developers.google.com/web/fundamentals/security/csp?hl=ko)

[https://gurumee92.github.io/2020/08/블로그-구축기-1-hugo-github으로-개인-블로그-만들기/](https://gurumee92.github.io/2020/08/%EB%B8%94%EB%A1%9C%EA%B7%B8-%EA%B5%AC%EC%B6%95%EA%B8%B0-1-hugo-github%EC%9C%BC%EB%A1%9C-%EA%B0%9C%EC%9D%B8-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0/)