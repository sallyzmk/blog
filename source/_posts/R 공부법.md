---
title: "R 공부법"
date: '2022-06-17 10:00'
---

# R 공부법

분석가 희망 : R 매우 중요, 통계

>t.test, anova, 회귀분석, 로지스틱회귀 : 한학기

>챗봇 서비스 : 설문조사 만족도 조사 →통계 분석

---

## 분석가 희망한다면 추천

[데이터 시각화 교과서]([http://www.yes24.com/Product/Goods/87631760](http://www.yes24.com/Product/Goods/87631760))

[RStudio > Cheat Sheets> ggplot2]([http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html](http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html))

![Untitled](images/How_to_study_R/Untitled.png)

---

## [R함수 공부하는 방법]

파이썬 라이브러리 = **R 패키지**

**CRAN** : R 패키지 설명서  [https://cran.r-project.org/](https://cran.r-project.org/)

1. packages 클릭

![Untitled](images/How_to_study_R/Untitled%201.png)

1. sorted by name 클릭

![Untitled](images/How_to_study_R/Untitled%202.png)

1. ruference manual: 옆에 클릭하면 패키지 설명 나옴

![Untitled](images/How_to_study_R/Untitled%203.png)

---

1. **geom_point** : 코드 설명 보기

![Untitled](images/How_to_study_R/Untitled%204.png)

**ggplot 예시**

```
p <- ggplot(mtcars, aes(wt, mpg))
p + geom_point()

# Add aesthetic mappings
p + geom_point(aes(colour = factor(cyl)))
p + geom_point(aes(shape = factor(cyl)))
# A "bubblechart":
p + geom_point(aes(size = qsec))
# Set aesthetics to fixed value
ggplot(mtcars, aes(wt, mpg)) + geom_point(colour = "red", size = 3)
# Varying alpha is useful for large datasets
d <- ggplot(diamonds, aes(carat, price))
d + geom_point(alpha = 1/10)
d + geom_point(alpha = 1/20)
d + geom_point(alpha = 1/100)
# For shapes that have a border (like 21), you can colour the inside and
# outside separately. Use the stroke aesthetic to modify the width of the
# border
ggplot(mtcars, aes(wt, mpg)) +
  geom_point(shape = 21, colour = "black", fill = "white", size = 5, stroke = 5)
# You can create interesting shapes by layering multiple points of
# different sizes
p <- ggplot(mtcars, aes(mpg, wt, shape = factor(cyl)))
p +
  geom_point(aes(colour = factor(cyl)), size = 4) +
  geom_point(colour = "grey90", size = 1.5)
p +
  geom_point(colour = "black", size = 4.5) +
  geom_point(colour = "pink", size = 4) +
  geom_point(aes(shape = factor(cyl)))
# geom_point warns when missing values have been dropped from the data set
# and not plotted, you can turn this off by setting na.rm = TRUE
mtcars2 <- transform(mtcars, mpg = ifelse(runif(32) < 0.2, NA, mpg))
ggplot(mtcars2, aes(wt, mpg)) +
  geom_point()
ggplot(mtcars2, aes(wt, mpg)) +
  geom_point(na.rm = TRUE)
```

```
ggplot(data = mtcars, aes(x = wt, y = mpg))

p <- ggplot(mtcars, aes(wt, mpg))
p + geom_point()
```

---

**데이터 넣어서 그래프 그리기** (iris 활용)

![Untitled](images/How_to_study_R/Untitled%205.png)

**코드 해석**

150 obs. of 5 variables:   150줄 5 항

칼람 내용, num: 숫자, factor: 

#help: 도움말,  #?str: help과 같음, 도움말

# ggplot(data = mtcars, aes(x = 가로축에 iris의 Sepal.Length활용, y = 세로축에 iris의 Sepal.Width활용))

geom_point() # 그래프 종류

![Untitled](images/How_to_study_R/Untitled%206.png)

![Untitled](images/How_to_study_R/Untitled%207.png)

geom_smooth(method=lm)  # 그래프 종류

![Untitled](images/How_to_study_R/Untitled%208.png)

![Untitled](images/How_to_study_R/Untitled%209.png)

---

## 분석용 데이터 받는 방법

[https://www.hannarae.net/data/d_room.php?code=data01&category=&searchopt=subject&searchkey=R��+�̿���+����������+�м�&x=31&y=19](https://www.hannarae.net/data/d_room.php?code=data01&category=&searchopt=subject&searchkey=R%C0%BB+%C0%CC%BF%EB%C7%D1+%B0%F8%B0%F8%B5%A5%C0%CC%C5%CD+%BA%D0%BC%AE&x=31&y=19)    R을 이용한 공공데이터 분석 검색

![Untitled](images/How_to_study_R/Untitled%2010.png)

![Untitled](images/How_to_study_R/Untitled%2011.png)

압축 해제 후, 서울특별시~~ 삭제(용량이 너무 커서 깃허브에 안 올라감. 최대 100 메가)

![Untitled](images/How_to_study_R/Untitled%2012.png)

![Untitled](images/How_to_study_R/Untitled%2013.png)

data에 있는 데이터를 source로 옮겨서 사용하면 됨.

---

## 데이터 내보내기 & 불러오기

- Rmd 파일이 아닌 R파일에서 실행
- 자세한건 day0620.Rmd에 필기

# 

# write.csv(exam)

write.table(x, file = "", append = FALSE, quote = TRUE, sep = " ",
eol = "\n", na = "NA", dec = ".", row.names = TRUE,
col.names = TRUE, qmethod = c("escape", "double"),
fileEncoding = "")

>여기서 x에는 매트릭스 또는 데이터 프레임만 들어간다.

>고로 데이터 exam을 넣는다

![Untitled](images/How_to_study_R/Untitled%2014.png)

![Untitled](images/How_to_study_R/Untitled%2015.png)

![Untitled](images/How_to_study_R/Untitled%2016.png)

![Untitled](images/How_to_study_R/Untitled%2017.png)

# getwd() : 현재 작업디렉토리 확인

# setwd()  : 새로운 작업디렉토리 지정

# dir() : 지정된 경로의 하위 폴더 및 파일의 이름을 문자형 벡터로 반환

# read.csv() : csv파일을 데이터프레임으로 읽기 “” 잊지 말 것!!!

# write.csv() : 데이터프레임을 cvs파일로 저장 “” 잊지 말 것!!!

[https://thebook.io/006723/ch04/02/01/](https://thebook.io/006723/ch04/02/01/)

60p~62p 내장 메모리

---

## Rmd 파일 기초설정

![Untitled](images/How_to_study_R/Untitled%2018.png)

---

## R 기본 함수

변수 저장은 a = 1 b= 1~~~ ctrl + enter

변수 삭제는 빗자루

![Untitled](images/How_to_study_R/Untitled%2019.png)

- iris는 내장데이터

![Untitled](images/How_to_study_R/Untitled%2020.png)

- class() # 타입을 물어보는 함수
- 남이 만든 함수를 쓰려면, 입력 조건을 확인해야 됨.
- help: 도움말,  #?str: help과 같음, 도움말