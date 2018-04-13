---
title: LINUX 작업환경 세팅하기
date: 2018-04-13 11:01:12
tags:
---

LINUX에 작업환경을 세팅해봅시다!  

## 환경 체크
(환경에 따라 명령어에 조금의 차이가 있을 수 있습니다.)  

### Linux version
`$ cat /etc/*-release | uniq `  

### CPU
`$ lshw -class processor`  

### GPU (only for NVIDIA)
`$ nvidia-smi`  

### GPU
`$ lshw -C display`  

### Tested environments
- Linux version: Linux Mint 18.3 (Sylvia) / ubuntu  
- CPU: Intel(R) Xeon(R) CPU E5-2687W v3 @ 3.10GHz 2개  
- GPU: Tesla K80 8개  

## Git
저는 코드는 메인 작업환경(맥이나 윈도우)에서 작성하고, 이를 실행하는 용도로만 Linux를 활용합니다. 이를 위해 코드를 옮기는 것은 Git을 사용하므로, 가장 먼저 해야 할 일은 Git을 설치하는 일입니다.  
Linux에는 기본적으로 Git이 설치되어 있는 것 같습니다. 그러면 설치는 생략하고, 기본 세팅을 진행합시다.  

`$ git config --list`
> 현재 설정을 확인합니다.  

```
$ git config --global user.name "{사용자 이름}"  
$ git config --global user.email jgravity@naver.com
```
> 사용자의 이름과 이메일을 세팅합니다.  

이제는 본격적으로 repo를 clone하여 작업을 진행해봅시다.  

```
$ git clone {repo 주소}
```

이제 clone이 완료되었습니다!  

## Dependencies

코드를 실행하려고 봤더니, 다음과 같은 에러 메세지가 뜨는 것을 확인할 수 있었습니다.  

```
> ImportError: No module error numpy
```

numpy module이 없다는 뜻이네요. 설치해줍시다. 저는 python3 을 사용할 것이라 pip3을 사용하였습니다.  

```
$ pip3 install numpy
```

numpy module이 설치되었습니다! 이런 식으로 세팅을 해나가면 됩니다.  

## References  
[리눅스 종류 확인, 리눅스 버전 확인](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%EC%A2%85%EB%A5%98_%ED%99%95%EC%9D%B8,_%EB%A6%AC%EB%88%85%EC%8A%A4_%EB%B2%84%EC%A0%84_%ED%99%95%EC%9D%B8)  
[8 commands to check cpu information on Linux](https://www.binarytides.com/linux-cpu-information/)  
[How to get the GPU info?](https://askubuntu.com/questions/5417/how-to-get-the-gpu-info)  
