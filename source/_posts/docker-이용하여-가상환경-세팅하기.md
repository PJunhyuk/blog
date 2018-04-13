---
title: docker 이용하여 가상환경 세팅하기
date: 2018-04-13 14:02:58
tags:
---

[Docker](http://docker.com/)은 제가 본 소프트웨어 중 가장 인상적인 것 중 하나입니다. 이에 대한 자세한 설명은 언젠가 기회가 될 때 하겠습니다.  

이번에는 Docker를 통해 가상환경을 세팅해보도록 하겠습니다.  

저는 tensorflow 가상환경을 세팅할 것입니다. 그러면 먼저 그 이미지를 받아야 합니다.

```
$ nvidia-docker pull {유저명/이미지명:태그명}
```

> ` $ nvidia-docker pull tensorflow/tensorflow:latest-gpu-py3 `

> GPU를 사용하기 위해 docker 대신 nvidia-docker 명령어를 사용합니다.  

` $ docker images ` 명령어를 통해 지금까지 받은 모든 image들을 확인할 수 있습니다.  

이제 image를 받았으니 그를 실행시켜 container로 만들어야 합니다.  

```
$ nvidia-docker run -it --name {container명} {유저명/이미지명:태그명} {기본명령어}
```

> ` $ nvidia-docker run -it --name jgravity_HAR_1 tensorflow/tensorflow:latest-gpu-py3 /bin/bash `  

> 마지막에 `/bin/bash` 를 추가한 이유는, 그러지 않으면 jupyter notebooks로 실행되기 때문입니다. 저는 그냥 bash 명령어 창을 원하므로, 이렇게 설정하였습니다.  

그러면 터미널 앞의 명령어가 바뀌는 것을 통해 container에 접속했음을 확인할 수 있습니다!  

이제 container 에 나왔다가 다시 접속해봅시다!  

Ctrl+D를 통해 현재 container에서 나올 수 있습니다. ` $ nvidia-docker ps ` 명령어를 통해 현재 구현되어 있는 모든 container를 확인할 수 있습니다.

```
$ nvidia-docker rm {container명}
```
> container 삭제

```
$ nvidia-docker start {container명}
```
> container 시작

```
$ nvidia-docker attach {container명}
```
> container 접근

그러므로, `start` - `attach` 명령어를 차례로 사용함으로써 해당 container에 접근할 수 있습니다.  

이제 docker을 이용하여 가상환경 세팅을 완료하였습니다! 신나게 코딩을 해봅시다:)  
