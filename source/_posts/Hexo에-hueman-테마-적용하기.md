---
title: Hexo에 hueman 테마 적용하기
date: 2018-01-12 11:24:03
tags:
---

이번에는 앞서 Hexo로 제작한 GitHub Pages의 Blog에 hueman이라는 플러그인을 적용해봅시다.

## hueman이란?

> A redesign of Alx's wordpress theme hueman, ported to Hexo.  
> Probably the most beautiful theme for Hexo.  

hueman은 Hexo 기반의 blog theme 입니다. 다음의 링크에서 Preview를 확인해보실 수 있습니다.  
[hueman-preview](http://blog.zhangruipeng.me/hexo-theme-hueman/)

## 설치
앞서 Hexo blog를 설치해놓았던 blog 디렉토리에서 다음의 명령어를 입력합니다. Heuman 테마를 clone 하는 과정입니다.  

```
$ git clone https://github.com/ppoffice/hexo-theme-hueman.git themes/hueman
```

그 후 blog 폴더의 `_config.yml` 에서 theme를 `landscape`가 아닌 `hueman`으로 수정합니다.  

```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: hueman
```

다음으로 `themes/hueman` 폴더에 있는 `_config.yml.example` 파일의 이름을 `_config.yml`로 바꿔줍니다.  
마지막으로 `Insight Search` 엔진을 사용하기 위해 npm으로 `hexo-generator-json-content` 패키지를 설치합니다.  

```
$ npm install -S hexo-generator-json-content
```

설치가 완료되었습니다! 변경 사항을 다음의 명령어를 통해 GitHub에 업로드합니다.  

```
$ git add *
$ git commit -m "Install hueman"
$ git push origin master
```

## 재배포
테마 설치 완료 후에는 Hexo를 재배포해야 합니다.

```
$ hexo clean
$ hexo generate
$ hexo deploy
```

처음에는 좀 깨져 보일 수 있는데, (css 로딩이 늦어서 그런 것 같습니다) 한 5분 정도 기다린 후 새로고침하니 잘 되는 것을 확인할 수 있었습니다.  
끝입니다! 이젠 Hexo의 hueman 테마가 적용된 블로그를 커스터마이징 할 수 있습니다.  

###### References
[Hexo 테마 적용하기](https://simhyejin.github.io/2016/06/24/hexo-themes/)
[Hexo 추천 테마, Hueman 적용하기](http://futurecreator.github.io/2016/06/14/hexo-apply-hueman-theme/)
