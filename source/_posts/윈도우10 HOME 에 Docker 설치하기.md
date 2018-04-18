---
title: 윈도우10 HOME 에 Docker 설치하기
date: 2018-04-18 16:54:42
tags:
---

윈도우10 HOME 에 Docker 를 설치해봅시다. Docker 에서 공식적으로 제공하는 윈도우10 용 클라이언트를 사용하기 위해서는 윈도우의 버전이 PRO 이상이어야 합니다. 그래야 HYPER-V를 사용할 수 있기 때문입니다. 저도 원래 이거 때문에 윈도우10 PRO 버전을 사용하였었지만, 이번에 새로 산 컴퓨터는 윈도우10 HOME 버전이더라구요. 윈도우 버전을 업그레이드할까, 다른 방법을 찾아볼까 하다가 후자를 선택하기로 했습니다.  

윈도우10 HOME을 위한 Docker 는 [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)를 통해 다운로드 받으실 수 있습니다.  

자세한 설치는 [Windows 10 Home에서 Docker 설치 하기](https://gwonsungjun.github.io/how%20to%20install/2018/01/28/DockerInstall/)에 아주 잘 나와있습니다!  

저는 추가로 [Kitematic](https://kitematic.com/)을 사용합니다. Docker를 통해 받은 이미지들을 관리할 수 있는 GUI 툴이라고 생각하면 될 것 같습니다.  

뭐 여하튼, cmd 창에 `$ docker` 명령어를 입력하였을 때 정상적으로 실행된다면 설치가 완료된 것입니다.  

## References
[Windows 10 Home에서 Docker 설치 하기](https://gwonsungjun.github.io/how%20to%20install/2018/01/28/DockerInstall/)  
