---
title: "VSCode Remote WLS 연동"
date: '2022-07-27 02:00'
---
## [강사님 링크]([https://dschloe.github.io/settings/vscode_wsl2/](https://dschloe.github.io/settings/vscode_wsl2/))

## [환경 변수가 중요한 이유]

빅데이터 플랫폼 구축

웹사이트 구축

— Configuration // 각 설치 프로그램끼리 환경변수로 유기적으로 연결시킴

— 레고 블록

## microsoft vs code 가 있는 것을 확인

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled.png)

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%201.png)

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%202.png)

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%203.png)

## vscode 실행하기

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%204.png)

## dataEngineering폴더 생성

## 아무 마크다운 파일 집어 넣기

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%205.png)

## 우분투 실행하기

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%206.png)

- 해당 마크다운을 리눅스로 다운 받는 중

## vscode 자동 실행됨

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%207.png)

---

# 가상환경 설치하기

(반드시 타이핑하기)

## 우분투 실행하기

```
username: human
password: 1234
```

ls 를 치면 아무 것도 안나옴

cd ..

mkdir : 파일 생성

```
cd home/
cd human/
cd airflow/

# 모든 파일 삭제
rm -rf *

# 설치
sudo apt-get update

sudo apt install python3-pip

sudo pip3 install virtualenv

# 가상환경 설치
virtualenv venv

# 리눅스는 bin/ 윈도우는 Script
source venv/bin/activate

# venv 가상환경 들어왔는지 확인
ls

# 경로 확인 및 복사 /home/human/airflow
pwd

# <실무 예제로 배우는 데이터 공학> 25p
pip3 install 'apache-airflow[postgres, slack, celery]'

# 이상한 코드 주루룩 뜸
vi ~/.bashrc
```

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%208.png)

## i를 치면 —INSERT—가 뜬다 (enter가 쳐짐)

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%209.png)

```
# pwd에서 나온 경로(/mnt/c/dataEngineering)를 복붙한다.
export AIRFLOW_HOME=/mnt/c/dataEngineering

## 저장하기
# step1. esc 누르고 
:wq! # step2. 저장하고 닫기
:q # step2. 저장 안하고 닫기

# step3. bash 터미널에서
source ~/.bashrc
source venv/bin/activate
echo $AIRFLOW_HOME # 저장됐는지 확인
```

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%2010.png)

```
# 가상환경에 접속한 후!!!!
airflow db init

airflow users create --username airflow --password airflow --firstname evan --lastname airflow --role Admin --email your_email@some.com

airflow webserver -p 8081
```

[http://localhost:8081](http://localhost:8081/home)

들어가서 --username airflow --password airflow

## 환경설정 끝

```
## 노트 ##

가상 환경 구성
virtualenv venv

가상환경 접속
source venv/bin/activate

가상환경 해제
deactivate
```

## 3장 강의를 위한 준비

```
pip3 install faker pandas

code .
```

## vscode 실행, 파일 생성 후 버전 확인

![Untitled](images/VSCode_Remote_WLS_Peristalsis/Untitled%2011.png)

```
# step1.py

import pandas as pd
import faker
print(pd.__version__)
```

## vi 편집기 공부!!