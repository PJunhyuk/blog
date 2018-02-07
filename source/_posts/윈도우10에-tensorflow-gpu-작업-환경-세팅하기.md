---
title: 윈도우10에 tensorflow-gpu 작업 환경 세팅하기
date: 2018-02-07 13:36:45
tags:
---

윈도우10 컴퓨터에 tensorflow-gpu 를 설치해봅시다.

> CUDA Toolkit 9.0 + cuDNN 7.0.5 + Python 3.6.4 + TensorFlow 1.5.0  

> Environment: Windows 10 Home + Inter(R) Core(TM) i7-8700K CPU @ 3.70GHz 3.70 GHz + NVIDIA GeForce GTX 1080 Ti

## CUDA Toolkit 9.0 설치
현재(2018년 2월 7일) 기준 CUDA Toolkit의 가장 최신 버전은 9.1입니다. 그러나 테스트해보니 latest version의 tensorflow가 CUDA Toolkit 9.1을 지원하지 않는 것 같아, 9.1을 설치했다가 삭제 후 9.0을 설치하였습니다ㅠㅠ  
삭제는 그냥 제어판에서 NVIDIA가 들어가는 것을 (그래픽카드 드라이버 빼고) 다 날려줬습니다. 중간에 한 번 재시작하라고 하는데, 말을 잘 들어줍시다. 중간에 화면이 이상해지거나, 클릭이 안되는 현상이 발생할 수도 있지만, 무시하고 기다리면 될 것 같습니다.  

여튼 설치를 위해, [CUDA Toolkit 9.0 설치 페이지](https://developer.nvidia.com/cuda-90-download-archive)에서 `Windows - x86-64 - 10 - exe (local)` 을 차례로 선택하여 Installer를 다운로드 받습니다.  
다운로드 후 쭉 클릭하여 설치를 완료해줍니다.  

설치 완료 후 cmd 창에 `nvcc --version` 을 입력하여 정상 설치를 체크해봅니다. 여러 줄이 뜨고, 마지막 줄에 release 9.0 이 뜨면 정상입니다.  

## cuDNN 설치
[cuDNN Download 페이지](https://developer.nvidia.com/rdp/cudnn-download)에 가면, 여러 버전 중 원하는 것을 선택할 수 있습니다. (로그인이 필요합니다!) CUDA Toolkit을 9.0 버전으로 설치하였으니, `Download cuDNN v7.0.5 for CUDA 9.0` 을 클릭하고, `cuDNN v7.0.5 for Windows 10` 을 클릭하여 다운로드 받습니다.  
다운로드가 완료되면, 압축을 풉니다. 내부에 있는 bin, include, lib 폴더를 `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0` 의 경로에 덮어써줍니다.  

## Python 설치
Python을 설치해봅시다. [Python 공식 홈페이지](https://www.python.org) 에서 다운로드 받으면 됩니다.  
이 때, 제 컴퓨터는 64비트이고, 32비트의 Python이 돌아가는데 에러가 나서, 64비트의 Python을 설치하였습니다. release에서 원하는 버전을 선택하고, 페이지 하단의 Files에서 `Windows x86-64 executable installer` 을 다운로드 받아서 설치하면 됩니다.  
저는 3.6.4 버전을 설치하였습니다.  

설치 완료 후 cmd 창에 `python --version` 을 입력하여 정상 설치를 체크해봅니다. `Python 3.6.4`라는 내용이 뜨면 정상입니다.  

## tensorflow-gpu 설치
Python과 함께 설치된 pip를 활용하여 tensorflow-gpu를 설치해봅시다. cmd 창에서 `pip install tensorflow-gpu`를 입력하면 설치가 진행됩니다.

설치 완료 후 cmd 창에 다음의 명령어를 통해 정상 작동을 체크해봅니다.

```
python
>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TF!')
>>> sess = tf.Session()
>>> sess.run(hello)
b'Hello, TF!'
>>> a = tf.constant(10)
>>> b = tf.constant(32)
>>> sess.run(a + b)
42
```

실행해보니, `>>> sess = tf.Session()` 명령어 입력 후 조금 텀이 존재하였습니다.  

아무튼 위의 명령어들이 잘 작동한다면 제대로 설치된 것입니다!  

## References
[1-2. 텐서플로우(TensorFlow) GPU버전(Tensorflow-Gpu) 설치하기](http://solarisailab.com/archives/1581)  
[TensorFlow GPU 설치 (Windows 10, Python 3.6)](http://deltacola.tistory.com/7)   
