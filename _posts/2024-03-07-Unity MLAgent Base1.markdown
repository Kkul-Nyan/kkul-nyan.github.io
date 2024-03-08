---
layout: post
title:  유니티 ML-Agent를 위한 기본설치 및 문제해결
date:   2024-03-07
image: Unity/cat001.webp
tags: ["Unity"]
---



---
# 유니티 ML-Agent를 위한 기본설치 및 문제해결
---

1.Pytion3 및 Pytorch
  -Pytion설치 및 PIP설치
  -경로 문제가 생길수 있음. 그럴경우 ./zshrc를 통해 경로지정필요 
2.파이썬 가상환경폴더생성 (터미널을통해 mkdir ~/python-envs 명령어를 실행)
3.새로운 가상환경이름 생성 (python3 -m venv ~/python-envs/sample-env)
  -sample-env의 경우, 원하는 이름지정
4.가상환경실행(source ~/python-envs/sample-env/bin/activate) 
  -이후에도 MLAgents 사용을 위해 터미널에서 미리 가상환경을 실행해줘야한다.
5.실행된 가상환경에 pip및 setuptoos 설치(pip3 install --upgrade pip, pip3 install --upgrade setuptools)
6.MLAgents 설치(pip3 install mlagents==*version)
  -"==*version"에서 *version대신 원하는 버전을 넣거나, 통채로 아예 생략하면된다.
7.MLAgents 명령어를 통해 잘 설치가 되었는지 확인(mlagents-learn --help)
  -문제없을시 mlagents에 관련된 명령어 설명이 뜬다.
 
발생했던 문제 및 해결방법

1.Python 설치이후 PIP설치 과정에서 발생

```c#
WARNING: The scripts pip, pip3 and pip3.9 are installed in '/Users/jeonghyeongi/Library/Python/3.9/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  NOTE: The current PATH contains path(s) starting with `~`, which may not be expanded by all applications. 
```
문제원인 
pip, pip3, 및 pip3.9 스크립트가 현재 사용자의 PATH에 추가되지 않았고, 해당 스크립트들이 /Users/username/Library/Python/3.9/bin 디렉토리에 설치되었다는 것을 나타냅니다. 즉, 터미널에서 애들을 정확한 PATH를 모르게 된다는 겁니다. 무시할경우 5번과정에서 가상환경내에 pip설치가 되지 않습니다.

문제해결

```c#
vi ~/.zshrc
//터미널에서 위 명령어를 통해 프로파일 파일을 열어줍니다.

export PATH="/Users/username/Library/Python/3.9/bin:$PATH"
//맨밑에 줄에 추가로 작성해 줍니다 완료시 ESC+:wq로 종료해줍니다.
//username에는 정확한 사용자계정 폴더명을 적어줍니다.

source ~/.zshrc
//변경사항을 즉시 적용합니다.
//그냥 프로그램을 완전히 종료후 다시 시작하셔도 됩니다.
```

2.5번 과정에서 발생

```c#
User Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: pip in ./Library/Python/3.9/lib/python/site-packages (24.0) 
```
문제원인
전역 패키지 디렉토리에 대한 쓰기 권한이 없이 설치를 시도시 발생합니다.
사실 4번과정을 제대로 진행하면, 가상환경내에 설치를 하기 때문에 발생하지 않습니다.

해결방법
제대로 4번 과정인 가상환경을 실행해준뒤 명령어를 실행해서 가상환경내에 설치하면됩니다.




