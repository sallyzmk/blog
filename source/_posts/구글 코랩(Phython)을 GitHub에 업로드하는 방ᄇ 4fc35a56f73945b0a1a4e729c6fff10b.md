# 구글 코랩(Phython)을 GitHub에 업로드하는 방법

### [GitHub Repository 초기 설정]

1. 우선  Github에 가서 새 repository를 만든다.
- ’Add a README file’ 체크
    
    - ’Add .gitignore > .gitignore template:**Python’** 으로 변경
    

![Untitled](/images/google_colab_github_commit/Untitled.png)

1. 파일 용량이 너무 크면 GitHub에 안 올라간다. 그래서 미리 data 파일 안에 있는 내용은 안 올라가게 설정해둘 수 있다.
    
    - .gitignore 파일을 열어 아래 코드를 적는다.
    
    ```
    # data
    data/파일명.csv # 특정 파일만 업로드 X
    data # data 파일 내에 있는 전체 파일 업로드 X
    ```
    
    - 터미널에서 git add, commit, push를 할 때 gitignore 부터 git add . 해줘야 반영이 된다.
    
    ```
    git add .gitignore
    git commit -m "update"
    git push
    ```
    
    - 초기 설정 때 한 번만 git add .gitignore해주고 이후로는 이전처럼 커밋(업로드)하면 된다.
    
    ```
    git add .
    git commit -m “update”
    git push -u origin main
    ```
    

![Untitled](/images/google_colab_github_commit/Untitled%201.png)

![Untitled](/images/google_colab_github_commit/Untitled%202.png)

1. 이제 Python을 사용해 보자. 파이썬을 실행할 수 있는 도구는 다양하다. 그 중에서 **구글 코랩**으로 파이썬을 사용했을 시에 GitHub에 저장하는 방법을 알아보자. 

### [구글 코랩 기본설정]

- 우선 구글 코랩에서 인공지능과 관련하여 파이썬을 실행 할 때는 

  시작과 동시에 구글코랩 GPU로 바꿔줘야한다!! 중요!!

![Untitled](/images/google_colab_github_commit/Untitled%203.png)

![Untitled](/images/google_colab_github_commit/Untitled%204.png)

- 귀여운 것 설정 (소소한 행복이다)

![Untitled](/images/google_colab_github_commit/Untitled%205.png)

![Untitled](/images/google_colab_github_commit/Untitled%206.png)

- 코드 창 왼쪽에 코드 행 번호 표시하는 설정

![Untitled](/images/google_colab_github_commit/Untitled%207.png)

### [구글 코랩을 GitHub에 커밋하는 방법 1]

- MD 파일로 전환 및 다운로드하여 각각 blog, python_lectures에 커밋하는 방법.

1. 구글 코랩에서 ‘다운로드 > .ipynb 다운로드’를 한다.

![Untitled](/images/google_colab_github_commit/Untitled%208.png)

1. 구글 코랩에서 다운로드 받은 파일을 python_lectures로  복붙한다.

![Untitled](/images/google_colab_github_commit/Untitled%209.png)

1. 아나콘다 네비게이터 > 관리자 권한으로 실행한다.
2. 아나콘대 네비게이터에서 Jupyter lab/ Jupyter notebook 을 실행하여 해당 파일을 찾아간다.

![Untitled](/images/google_colab_github_commit/Untitled%2010.png)

![Untitled](/images/google_colab_github_commit/Untitled%2011.png)

1. markdown로 바꿔준다.

![Untitled](/images/google_colab_github_commit/Untitled%2012.png)

![Untitled](/images/google_colab_github_commit/Untitled%2013.png)

1. MD 파일로 저장
    
    - Jupyter lab은 save and~ markdown으로 저장
    

![Untitled](/images/google_colab_github_commit/Untitled%2014.png)

- Jupyter note은 download as > markdown으로 저장

![Untitled](/images/google_colab_github_commit/Untitled%2015.png)

1. 저장된 MD 파일을 각각 blog, python_lectures > source파일에 복붙해서 커밋한다.

### [구글 코랩을 GitHub에 커밋하는 방법 2] 복잡, 비추

- GitHub에 바로 저장하는 방법.

- 경로 지정 잘 하기, 블로그에 올릴 거라면 다운로드가 편하다.

- *주의* 나중에 로컬에서 깃허브로 업로드 할 때 git pull 먼저 해야 git push가 실행된다. 

![Untitled](/images/google_colab_github_commit/Untitled%2016.png)

![Untitled](/images/google_colab_github_commit/Untitled%2017.png)