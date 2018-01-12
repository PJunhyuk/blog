---
title: Hexo로 GitHub Pages에 Blog 설치
date: 2018-01-12 10:36:54
tags:
---

GitHub Pages에 [Hexo](https://hexo.io/ko/index.html)를 설치해봅시다.

## Hexo란?
Hexo는 Node.js 기반의 블로그 프레임워크입니다. Hexo 공식 소개를 살펴보면 Hexo가 무엇인지 쉽게 알 수 있습니다.

> Hexo is a fast, simple & powerful blog framework powered by Node.js.

## Dependencies

### Node.js & npm
Hexo를 설치하기 위해서는 Node.js가 설치되어야 있어야 합니다.  
맥에 Node.js를 설치하는 방법은 여러 가지가 있습니다. 가장 쉬운 방법은 Node.js 사이트에서 공식 설치 파일을 받는 것이지만, 이는 다음과 같은 문제가 있다고 합니다.  

- 관리자 권한 없이 제대로 실행되지 않음.  
- Node.js의 여러 버전을 관리할 수 없어, 서로 다른 버전을 사용하는 여러 프로젝트를 동시에 테스트하기 어려움.  

때문에 homebrew나, nvm(Node Version Manager) 등을 사용하여 Node.js를 설치하곤 합니다.  
그러나 저는 위의 두 방법 모두 이상한 에러가 떠서, 기존 파일을 모두 삭제 후 공식 설치 파일을 통해 설치를 진행하였습니다ㅎㅎ;  
공식 설치 파일을 사용하여 Node.js와 npm을 모두 설치해줍시다.

###### References
[Mac에서 Node.js 설치하기
](http://junsikshim.github.io/2016/01/29/Mac%EC%97%90%EC%84%9C-Node.js-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0.html)  

### ETC
손쉬운 설치를 위해 hexo 관련 몇몇 npm 패키지를 설치하여야 합니다.  

```
$ npm install hexo-cli -g
```

## 설치
### Hexo 설치
Hexo를 사용하여 개인/팀 블로그를 설치해보도록 하겠습니다. 원하는 그림은 <code>https://<개인/팀계정>.github.io/blog</code> 에 Hexo blog가 설치되는 것입니다.  
workspace 폴더에서 다음의 명령어를 실행합니다.

```
$ hexo init blog
```

그러면 폴더 내부에 blog라는 폴더가 생성됩니다. node modules 설치를 진행합니다.

```
$ cd blog
$ npm install
```

기본적인 Hexo 설치가 완료되었습니다!

### GitHub 세팅
GitHub Pages 사용을 위해서는 위에서 사용한 개인/팀의 계정에 blog라는 repository를 만들어야 합니다. GitHub 사이트에 접속하여 New를 누르고, blog라는 이름의 repository를 만들어줍시다. 이 때 README.md나 .gitignore과 같은 파일은 생성하지 않습니다.  
이제 앞서 설치해놓은 Hexo를 GitHub repository에 업로드해야합니다. blog 폴더로 이동하여 다음의 명령어를 입력합니다.

```
$ git init
$ git remote add origin https://github.com/virus-lab/blog.git
$ git add *
$ git commit -m "Initiate Hexo"
$ git push origin master
```

GitHub의 repository로 이동하면 잘 업로드 된 것을 확인할 수 있습니다. 웹 상에서 dependencies 에러 메세지가 나오면 Dismiss - Risk is tolerable to this project 를 선택합시다.

### 배포 준비
GitHub Pages에 배포하기 위해 blog 디렉토리의 `_config.yml` 파일을 수정합니다.  
위의 URL 부분은 다음과 같이 수정합니다.  

```
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://<개인/팀계정>.github.io/blog
root: /blog/
permalink: :year/:month/:day/:title/
permalink_defaults:
```

아래 Deployment 부분은 다음과 같이 추가 및 수정합니다.  

```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/<개인/팀계정>/blog.git
  branch: gh-pages
```

### 배포
먼저 다음의 명령어를 통해 deployment(배포) 패키지를 설치합니다.  

```
$ npm install hexo-deployer-git --save
```

다음의 명령어를 통해 repository를 clean 한 후 배포합니다. d, -g 태그는 각각 deploy와 generate의 약자입니다.

```
$ hexo clean
$ hexo d -g
```

끝입니다!  
GitHub 웹의 repository에서 branch를 gh-pages로 수정한 후 보면 방금 한 것들이 commit 되어 있는 것을 확인할 수 있습니다. 이제 <code>https://<개인/팀계정>.github.io/blog</code> 의 링크에 블로그가 설치된 것을 확인하실 수 있습니다!

###### References
[Github으로 개인페이지 만들기](http://jooooon.com/blog/2017/09/30/create-a-personal-page-with-github/)  
[Hexo+GitHub pages](https://simhyejin.github.io/2016/06/20/hexo-github-pages/)  
[Hexo 기본 사용법](http://futurecreator.github.io/2016/06/21/hexo-basic-usage/)  
