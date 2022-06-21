---
title: "노션 6.20 강의(R)"
output:
  html_document:
    keep_md: true
date: '2022-06-20'
---
# 오전강의 (R 벡터, 기본 함수)

Rmd 파일을 갓 생성하면 → 이렇게 나옴

아래처럼 바꿔줘야함

![Untitled](/images/6_20_class_note(R)/Untitled.png)

![Untitled](/images/6_20_class_note(R)/Untitled%201.png)

절대 건들지 말 것→

![Untitled](/images/6_20_class_note(R)/Untitled%202.png)

---

변수 저장은 a = 1 b= 1~~~ ctrl + enter

변수 삭제는 빗자루

![Untitled](/images/6_20_class_note(R)/Untitled%203.png)

- iris는 내장데이터

- c() 컴바인combin 묶어 주다 (c 리스트)

![Untitled](/images/6_20_class_note(R)/Untitled%204.png)

![Untitled](/images/6_20_class_note(R)/Untitled%205.png)

- class() # 타입을 물어보는 함수
- 남이 만든 함수를 쓰려면, 입력 조건을 확인해야 됨.
- help: 도움말,  #?str: help과 같음, 도움말

범주형 벡터는 

![Untitled](/images/6_20_class_note(R)/Untitled%206.png)

비었음 못들음…!! 49p~54p

비었음 못들음…!! 49p~54p

비었음 못들음…!! 49p~54p

데이터 프레임 생성

---

# 오후 강의 (데이터 활용)

### 분석용 데이터 받는 방법

[https://www.hannarae.net/data/d_room.php?code=data01&category=&searchopt=subject&searchkey=R��+�̿���+����������+�м�&x=31&y=19](https://www.hannarae.net/data/d_room.php?code=data01&category=&searchopt=subject&searchkey=R%C0%BB+%C0%CC%BF%EB%C7%D1+%B0%F8%B0%F8%B5%A5%C0%CC%C5%CD+%BA%D0%BC%AE&x=31&y=19)    R을 이용한 공공데이터 분석 검색

![Untitled](/images/6_20_class_note(R)/Untitled%207.png)

![Untitled](/images/6_20_class_note(R)/Untitled%208.png)

압축 해제 후, 서울특별시~~ 삭제(용량이 너무 커서 깃허브에 안 올라감. 최대 100 메가)

![Untitled](/images/6_20_class_note(R)/Untitled%209.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2010.png)

data에 있는 데이터를 source로 옮겨서 사용하면 됨.

---

### 데이터 내보내기 & 불러오기

- Rmd 파일이 아닌 R파일에서 실행
- 자세한건 day0620.Rmd에 필기

# ctrl+shift+k = knit

# write.csv(exam)

write.table(x, file = "", append = FALSE, quote = TRUE, sep = " ",
eol = "\n", na = "NA", dec = ".", row.names = TRUE,
col.names = TRUE, qmethod = c("escape", "double"),
fileEncoding = "")

>여기서 x에는 매트릭스 또는 데이터 프레임만 들어간다.

>고로 데이터 exam을 넣는다

![Untitled](/images/6_20_class_note(R)/Untitled%2011.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2012.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2013.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2014.png)

# getwd() : 현재 작업디렉토리 확인

# setwd()  : 새로운 작업디렉토리 지정

# dir() : 지정된 경로의 하위 폴더 및 파일의 이름을 문자형 벡터로 반환

# read.csv() : csv파일을 데이터프레임으로 읽기

# write.csv() : 데이터프레임을 cvs파일로 저장

[https://thebook.io/006723/ch04/02/01/](https://thebook.io/006723/ch04/02/01/)

60p~62p 내장 메모리

---

### 블로그에 R 이미지 업로드 방법

![Untitled](/images/6_20_class_note(R)/Untitled%2015.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2016.png)

R Markdown 이하 삭제

아래가 Rmd 기본, 저장 해 놓고 항상 복붙

```
output:
  html_document:
    keep_md: true
```

```
---
title: "test"
output:
  html_document:
    keep_md: true
date: '2022-06-20'
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
```

![Untitled](/images/6_20_class_note(R)/Untitled%2017.png)

데이터와 Rmd 파일의 위치가 일치해야 시각화가 됨.

knit 실행 > working directory 에 이미지가 생성됨

![Untitled](/images/6_20_class_note(R)/Untitled%2018.png)

rmd_0620 안에 있는 사진을 blog로 복붙(images 파일 생성, >rmd_0620 파일 생성)

![Untitled](/images/6_20_class_note(R)/Untitled%2019.png)

md파일은 _posts 파일로 복붙

![Untitled](/images/6_20_class_note(R)/Untitled%2020.png)

hexo server > 경로가 다르기 때문에 오류 나는 것

blog을 파이참으로 열어서 CSV 파일 확인하기

![Untitled](/images/6_20_class_note(R)/Untitled%2021.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2022.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2023.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2024.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2025.png)

![Untitled](/images/6_20_class_note(R)/Untitled%2026.png)

빈칸에 있던 내용은 삭제

ctrl+V 한 후 source 삭제

- hexo에서 이미지 경로

---

노션을 hexo 블로그에 올리는 법

![Untitled](/images/6_20_class_note(R)/Untitled%2027.png)