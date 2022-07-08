---
title: "R파일을 GitHub에 업로드하는 방법"
output:
  html_document:
    keep_md: true
date: '2022-06-17 07:00'
---
# R파일을 GitHub에 업로드하는 방법

## **R을 깃허브에 올리고 싶을 때_1** (생성)

### 1. github에서 저장소 생성 (add a readme file 체크!!)

![Untitled](images/R_file_github_commit//Untitled.png)

### 1.(2) git clone으로 바탕화면에 깃허브 파일 땡겨오기

![Untitled](images/R_file_github_commit//Untitled%201.png)

![Untitled](images/R_file_github_commit//Untitled%202.png)

```
git clone [https://github.com/sallyzmk/R_lectue.git](https://github.com/sallyzmk/R_lectue.git)
```

### 2. Rtools 실행하기 (생성된 R_lectue 파일을 R로 실행해야됨)

### 3. R 들어가서 create a project 클릭

![Untitled](images/R_file_github_commit//Untitled%203.png)

### 4. existing dirextory 클릭 (directory = 폴더)

![Untitled](images/R_file_github_commit//Untitled%204.png)

![Untitled](images/R_file_github_commit//Untitled%205.png)

### 5. R_lectue 파일 찾기 (파일명 한글 X)

![Untitled](images/R_file_github_commit//Untitled%206.png)

### 6. 셋팅이 됨

![Untitled](images/R_file_github_commit//Untitled%207.png)

### 7. 파일 나누기 (개인 스타일)

![Untitled](images/R_file_github_commit//Untitled%208.png)

### 8. source 파일에 들어가서 > set as working directory 기본 파일 저장 위치(경로) 설정

![Untitled](images/R_file_github_commit//Untitled%209.png)

---

## **R을 깃허브에 올리고 싶을 때_2 (업로드)**

### 1. R에서 source 폴더 안으로 들어가, set as working directory 입력

![Untitled](images/R_file_github_commit//Untitled%2010.png)

### 2. 파일을 R Markdowm 눌러서 마크 다운으로 변환 시키기 (누르면 ~설치할거냐 뜸, 설치하기.)

![Untitled](images/R_file_github_commit//Untitled%2011.png)

![Untitled](images/R_file_github_commit//Untitled%2012.png)

presentation : 프레젠테이션으로도 만들 수 있음

shiny : 데스크탑 같은거 블로그 처럼? (확실X)

pdf, word : 이런건 또 무언가를 설치해야됨

### 3. title 변경하기 ,

```
title: "Day-1 Visualization"
output:
  html_document:
    keep_md: true
date: '2022-06-17'
```

![Untitled](images/R_file_github_commit//Untitled%2013.png)

### 4. 저장하기, 이름 같아도 Rmd라 생성가능

![Untitled](images/R_file_github_commit//Untitled%2014.png)

생성된 모습

![Untitled](images/R_file_github_commit//Untitled%2015.png)

### 5. knit 누르면 새로운 창이 열림

![Untitled](images/R_file_github_commit//Untitled%2016.png)

![Untitled](images/R_file_github_commit//Untitled%2017.png)

### 6. 맨 밑에 아래 코드 복사 붙여넣기

```
## ggplot2 시각화
- 다음과 같이 시각화를 작성한다.

```{r}
library(ggplot2)
ggplot(data = iris, aes(x = Sepal.Length,
                        y = Sepal.Width)) +
  geom_point()
```
```

*옆에 초록색 버튼 누르면 해당 언어 코드 입력 창이 생성 됨

![Untitled](images/R_file_github_commit//Untitled%2018.png)

![Untitled](images/R_file_github_commit//Untitled%2019.png)

![Untitled](images/R_file_github_commit//Untitled%2020.png)

![Untitled](images/R_file_github_commit//Untitled%2021.png)

### 8. md 파일 복사해서 blog>source>_posts>파일 안에 복붙

![Untitled](images/R_file_github_commit//Untitled%2022.png)

![Untitled](images/R_file_github_commit//Untitled%2023.png)

![Untitled](images/R_file_github_commit//Untitled%2024.png)

### 9. blog 파일 파이참 실행

- 터미널창 git bash 에서 hexo server 실행 > hexo 블로그에 업데이트 됨.

![Untitled](images/R_file_github_commit//Untitled%2025.png)

![Untitled](images/R_file_github_commit//Untitled%2026.png)

### 10. 업로드 하기

git add .
git commit -m “update”
git push -u origin main

---

## **R을 깃허브에 올리고 싶을 때_3 (이미지)**

![Untitled](images/R_file_github_commit//Untitled%2027.png)

![Untitled](images/R_file_github_commit//Untitled%2028.png)

1. R Markdown 이하 삭제
2. 아래가 Rmd 기본, 저장 해 놓고 항상 복붙

```
output:
  html_document:
    keep_md: true
```

1. 데이터와 Rmd 파일의 위치가 일치해야 시각화가 됨.
2. knit 실행 > working directory 에 이미지가 생성됨

![Untitled](images/R_file_github_commit//Untitled%2029.png)

1. rmd_0620 안에 있는 사진을 blog로 복붙(images 파일 생성, >rmd_0620 파일 생성(이 때 이미지를 담을 파일명은 반드시 영문으로!!))

![Untitled](images/R_file_github_commit//Untitled%2030.png)

1. md파일은 _posts 파일로 복붙

![Untitled](images/R_file_github_commit//Untitled%2031.png)

1. hexo server > 경로가 다르기 때문에 오류 나는 것
2. blog을 파이참으로 열어서 CSV 파일 확인하기

![Untitled](images/R_file_github_commit//Untitled%2032.png)

![Untitled](images/R_file_github_commit//Untitled%2033.png)

![Untitled](images/R_file_github_commit//Untitled%2034.png)

![Untitled](images/R_file_github_commit//Untitled%2035.png)

![Untitled](images/R_file_github_commit//Untitled%2036.png)

1. 빈칸에 있던 내용은 삭제
2. ctrl+V 한 후 source 삭제
3. hexo에서 이미지 경로