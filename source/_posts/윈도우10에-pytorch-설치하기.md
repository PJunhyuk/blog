---
title: 윈도우10에 pytorch 설치하기
date: 2018-03-05 14:16:21
tags:
---

윈도우에 pytorch를 설치해봅시다!  

## pytorch 란?
[pytorch](http://pytorch.org/)는 머신러닝 프레임워크 중 하나입니다. python 형식입니다.  

## pytorch 윈도우 설치

pytorch는 공식적으로 linux와 macOS 환경만 지원하기 때문에, 윈도우에 설치하기 위해서는 anaconda와, 어떤 개발자가 구현해놓은 것을 사용해야 합니다.  

anaconda prompt를 관리자 권한으로 실행시켜, 다음의 명령어를 입력합니다.  

```
(base) > conda install -c peterjc123 pytorch
```

그러면 pytorch가 설치됩니다.  

## 확인

pytorch가 정상적으로 설치되었는지, 그리고 CUDA를 통해 GPU를 사용할 수 있는지를 체크하기 위해서는 다음의 명령어를 anaconda prompt에 실행해봅니다.

```
(base) > python
>>> import torch
>>> torch.cuda.current_device()
0
>>> torch.cuda.device(0)
<torch.cuda.device at 0x000002299E83B780>
>>> torch.cuda.device_count()
1
>>> torch.cuda.get_device_name(0)
'GeForce GTX 1080 Ti'
```

정상적으로 GPU가 detect 된 모습을 확인할 수 있습니다!  

###### References
[윈도우 10 PyTorch 환경 구성 - 설치](http://bob3rdnewbiew.tistory.com/313)  
[How to check your pytorch / keras is using the GPU?](http://forums.fast.ai/t/how-to-check-your-pytorch-keras-is-using-the-gpu/7232)
