---
title: docker contaniner에 개발환경 세팅하기
date: 2018-04-13 14:28:55
tags:
---

docker로 만든 container에 개발환경을 세팅해봅시다.  

## Tested Environments
#### Image
- [tensorflow/tensorflow:latest-gpu-py3](https://hub.docker.com/r/tensorflow/tensorflow/)

## Git

#### 설치

```
# apt-get update
```
> 먼저 apt-get을 업데이트합니다.  

```
# apt-get install git
```

#### 확인

```
# git --version
```
> git version 2.7.4

#### 설정

```
# git config --global user.name '{유저명}'
# git config --global user.email {유저이메일}
# git config --list
```

#### 클론

```
# git clone {repo주소}
```

## Python dependencies

#### cv2
> ImportError: No module named 'cv2' 해결  

linux에 python-opencv를 설치하는 것은 몹시 귀찮은 일입니다ㅠㅠ 다음의 링크를 참조합시다.  
[Install OpenCV3 on Ubuntu](https://www.learnopencv.com/install-opencv3-on-ubuntu/)

#### pip (upgrade)
> You are using pip version 9.0.1, however version 9.0.3 is available. 해결  

```
# pip install --upgrade pip
```

#### tensorflow
