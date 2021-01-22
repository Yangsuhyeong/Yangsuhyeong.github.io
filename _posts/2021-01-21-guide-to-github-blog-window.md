---
layout: post
title: Making Github Blog first time
summary: 윈도우에 지킬 사용해서 github page blog 처음 만들기
categories: github blog
---

내가 잊지 않고 계속 쓰려고 정리하는 github blog 사용 관련된 명령어 포스팅

#### 1. ruby와 jekyll은 깔려있다는 가정 하에 시작. 또한, 본인의 github에서 `{username}.github.io`로 시작되는 repository를 우선 생성해 주어야 함. 

#### 2. 로컬 컴퓨터에 github repository용 폴더 만들고 원격 폴더와 연결하기. 
* "blog/`username`.github.io" 폴더를 만들어서 github repository와 연결함 : 

```bash
$ cd C:/blog/{username}.github.io
$ git init

$ git remote add origin "https://{username}@github.com/{username}/{username}.github.io.git"

# pull 
$ git pull "https://{username}@github.com/{username}/{username}.github.io"

# push
$ git push -u origin master
```

'C:/blog/{username}.github.io' 폴더에 파일을 생성하고 pull할 경우 github repository에 올라감. 

브라우저에서 현재 깃허브 블로그 생성되었는지 확인 : 

```html
https://{username}.github.io/
```

#### 3. 원하는 지킬 테마 찾기
- 편하게 clone or downlaod -> zip 풀기 -> blog/{username}.github.io 폴더에 전부 복사 

#### 4. 설정 변경 
- `_config.yml` 설정 변경 :

```html
# site settings
title: Github Blog total title
email: 
author:
baseurl: ""
url: "blog url"
```

#### 5. 로컬에서 실행해서 블로그 보기 : 
```bash
$ bundle install
$ bundle exec jekyll serve --watch
```
```
 Incremental build: disabled. Enable with --incremental
      Generating...
                    done in 0.845 seconds.
  Please add the following to your Gemfile to avoid polling for changes:
    gem 'wdm', '>= 0.1.0' if Gem.win_platform?
 Auto-regeneration: enabled for 'C:/blog/Yangsuhyeong.github.io'
    Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.
```

이런 output이 나오면 성공, 로컬(브라우저)에서 열어보기 : 
```bash
http://localhost:4000/
```

#### 6. 포스팅 : 

* `_posts` 폴더에 `year-month-day-name.md`파일 생성 

* 헤더 기입 : 
```html
---
layout: <span class="red">post</span>
title: <span class="red">post title</span>
summary: <span class="red">summary for your own info</span>
category: <span class="red">github blog making</span>
---
```

* Image : 
`http://{username}.com/images/Image_Name`으로 지정시 깃허브 페이지나 서버에서 정상적으로 확인할 수 있다고 함. 

* 한글폰트 : 
`_includes/head.html` 안의 `<!--fonts-->` 밑에 원하는 폰트 넣으면 됨!

```html
<!--fonts-->
<link rel="stylesheet" href="https://fonts.googleapis.com/earlyaccess/nanumgothic.css">
```
이후, `_sass/variables.scss`의 `// Typography`에 `'Nanum Gothic'` 추가하기 


#### 7. upload online

- 이미 remote 되어있는 상황에서, 

```bash
$ cd C:/blog/{username}.github.io
$ git status
$ git add . 
# 한꺼번에 변경사항 기록
$ git commit -m "Add test"

$ git push 
```

'C:/blog/{username}.github.io' 폴더에 파일을 생성하고 pull할 경우 github repository에 올라감. 

브라우저에서 현재 깃허브 블로그 생성되었는지 확인 : 

```html
https://{username}.github.io/
```

### Reference 
- http://enshahar.com/%EB%B8%94%EB%A1%9C%EA%B7%B8/jekyll/pixyll/2017/11/14/blog-transferring/