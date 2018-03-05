---
title: 'anaconda 를 통해 python 2, 3 환경 모두 관리하기'
date: 2018-03-05 17:07:46
tags:
---

## python 2.7 실행

anaconda는 여러 version의 python을 관리할 수 있게 해주는 툴입니다.  

python을 사용하다보면, 기본적으로 설치된 python 이외에 다른 version의 python을 사용해야 할 경우가 꽤 있습니다. 예를 들어, 제가 최근 보고 있는 [charades-algorithms](https://github.com/gsig/charades-algorithms) 코드 역시 python 2.7 version에서 구현되었습니다. 이를 활용하기 위해서는, anaconda를 사용하여 다른 version의 python 환경을 생성하고, 그에 접근해야 합니다.  

먼저, 윈도우 프롬포트에서 `conda` 명령어를 바로 사용하기 위해, 환경변수의 `Path`에 conda의 경로를 넣어줍시다. 환경변수의 `Path`는 `내 PC > 우클릭 > 속성 > 고급 시스템 설정 > 환경 변수 > 시스템 변수 > Path > 편집 > 새로 만들기` 에서 추가할 수 있으며, 저의 경우에는 `C:\Users\MCML-PJunhyuk-LabDT\Anaconda3\Scripts`가 그 경로였습니다.  

그 다음, 윈도우 프롬포트를 실행하여 다음의 명령어를 입력합니다.  

```
> conda create -n py27 python=2.7 anaconda
```

conda를 이용하여 새로운 환경을 생성하며, 그 이름은 py27, python 버전은 2.7이라는 것을 의미합니다. 이렇게 생성한 환경의 리스트는 다음의 명령어로 확인할 수 있습니다.

```
> conda info --envs
```

이제는 생성한 Python 2.7 환경을 사용해봅시다. 먼저 Anaconda Prompt 를 실행합니다. 커맨드 라인 앞의 괄호 안에 들어 있는 것이 현재 활성화된 환경입니다.  
앞서 제작한 환경의 이름이 py27이었으므로, 다음의 명령어를 통해 그 환경에 접근합니다.  

```
(base) > conda activate py27
(py27) >
```

그러면 괄호 안이 py27로 바뀌는 것을 확인하실 수 있습니다. 다음의 명령어를 통해 해당 환경의 python version을 확인해봅시다.  

```
(py27) > python --version
Python 2.7.14 :: Anaconda. Inc.
```

우리가 원하는대로 실행되었습니다!

###### References
[파이썬 아나콘다 Python3, Python2 동시 설치(다중 커널) :)](https://m.blog.naver.com/zzsza/220921730006)
[Anaconda 설치하기 - Python을 제대로 활용해보자](http://egloos.zum.com/mataeoh/v/7052271)
