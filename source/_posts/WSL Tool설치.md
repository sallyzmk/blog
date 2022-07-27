
---
title: "WSL Tool설치"
date: '2022-07-27 01:00'
---
## [실무 예제로 배우는 데이터 공학]

백엔드 개발자 - 243p 아파치 카프카

머신러닝 - 271p 스파크 pyspark

머신러닝 엔지니어 - 69p, 99p 챕터 4,5

---

## 윈도우 사양 > 버전> 20H1, 20H2, 21H1, 21H2 확인

![Untitled](images/WSL_Tool_installation/Untitled.png)

![Untitled](images/WSL_Tool_installation/Untitled%201.png)

## 윈도우즈 기능/켜기 - 하이퍼 바이저 플랫폼 클릭, 가상머신 플랫폼, Hyper-V 클릭, 컴퓨터마다 조금씩 다름.

![Untitled](images/WSL_Tool_installation/Untitled%202.png)

![Untitled](images/WSL_Tool_installation/Untitled%203.png)

## power shell 실행

![Untitled](images/WSL_Tool_installation/Untitled%204.png)

![Untitled](images/WSL_Tool_installation/Untitled%205.png)

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

## 다운로드 및 설치

`[https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)`  (다운로드, 설치)

## microsoft store 에서 ubuntu 20.04.4LST 설치

![Untitled](images/WSL_Tool_installation/Untitled%206.png)

![Untitled](images/WSL_Tool_installation/Untitled%207.png)

![Untitled](images/WSL_Tool_installation/Untitled%208.png)

![Untitled](images/WSL_Tool_installation/Untitled%209.png)

- 가상환경에 접속이 안돼있음

![Untitled](images/WSL_Tool_installation/Untitled%2010.png)

![Untitled](images/WSL_Tool_installation/Untitled%2011.png)

```
username: human
password: 1234
```

![Untitled](images/WSL_Tool_installation/Untitled%2012.png)

## powershell 끄고 관리자로 재실행

![Untitled](images/WSL_Tool_installation/Untitled%2013.png)

```
wsl --set-default-version 2

wsl -l -v
```

![Untitled](images/WSL_Tool_installation/Untitled%2014.png)

## version 2 확인