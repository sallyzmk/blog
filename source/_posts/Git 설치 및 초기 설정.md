---
title: "Git 설치 및 초기 설정"
output:
  html_document:
    keep_md: true
date: '2022-06-17 03:00'
---

- git 다운로드 웹사이트 : [https://git-scm.com/download/win](https://git-scm.com/download/win)
- 관리자 권한으로 실행
- 설정 별도 수정 불필요, 마지막에 Lanch Git Bash만 체크)

![Untitled](images/Git_download/Untitled.png)

- 로그인을 하기 위해 로컬PC와 Github 연결
- Github에서 우측 상단 프로필 클릭> Your repositories > New > Add a README file 체크하지 않고 > 생성

![Untitled](images/Git_download/Untitled%201.png)

- 시작화면에서 우클릭 > Git Bash Here 클릭

![Untitled](images/Git_download/Untitled%202.png)

- **mkdir human0616**    #mkdir : 새 폴더 생성
- **cd human0616**/    #cd : change directory, cd human Tab 누르면 파일명 자동 완성
- #pwd : 현재 경로
- #Github 코드 한 줄 씩 복사해서 우클릭 Paste (붙여넣기)

![Untitled](images/Git_download/Untitled%203.png)

- `echo "# human0616" >> README.md`
    
    >human0616 파일 안에 생성된 파일 우클릭>연결프로그램>메모장
    

![Untitled](images/Git_download/Untitled%204.png)

- #`git init` : 파일 초기화
    
    숨긴 항목 확인하면 .git 파일 있음
    

![Untitled](images/Git_download/Untitled%205.png)

- #`git add` 파일명 : 파일 한개만 업로드
- #`git add.(X)` `git add . (O)`
    
    `git add .` : 폴더 내 모든 파일 업로드
    
- `git commit -m "first commit"`
    
    #에러 뜸, Please teall me who you are.
    
    git config —global user.email 가입 시 기입한 본인 메일 주소
    
    git config —global user.name 내 닉네임
    
    `git commit -m "first commit"` 재실행
    
    ![Untitled](images/Git_download/Untitled%206.png)
    
    #`git branch -M main` : 별거 없음
    
    #`git remote add origin [https://github.com/sallyzmk/human0616.git](https://github.com/sallyzmk/human0616.git)` : 로컬이랑 git hub 연결
    
    #`git push -u origin main` : 입력하면 아래 화면 뜸
    
    >sign in with your browser 
    
    > Authorize GitcredentialManager
    
    >GitHub 새로 고침하면 화면이 바뀌어 있음
    
    ![Untitled](images/Git_download/Untitled%207.png)
    
    ![Untitled](images/Git_download/Untitled%208.png)
    
    ![Untitled](images/Git_download/Untitled%209.png)
    
    끝!!!
    
    ---
    
    # **GIT 동기화** (컴퓨터 시작했을 때)
    
    #**git clone** https://github.com~~~(주소 복붙): 기초 작업이 안돼 있을 때, 폴더 없을 때
    
    ![Untitled](images/Git_download/Untitled%2010.png)
    
    #**git pull** : 폴더는 존재하고 내용만 새로 다운 받을 때 사용 
    
               (기초 작업이 되어있는 상태에서, 코드 재 다운)
    
    - 다른 컴에서 파일을 조작한 적 있다면
    - 앉자마자 git pull 부터!
    - 새로운 작업을 할 땐,  git pull을 해서 원격 저장소에 있는 최신 프로젝트를 가져와 준 뒤, 작업을 하고 그리고 나서 git push를 해주어야 한다.
    
    ---
    
    # **커밋하는 방법 (업로드)**
    
    [커밋 (commit) : 파일을 추가하거나 변경 내용을 **저장소**에 업로드하는 작업]
    
    git add . 
    
    git commit -m “your_message”  
    
    git push -u origin main
    
    #”” 입력 메새지는 일종의 제목 같은 것
    
    #git push -u 만 쳐도 괜찮지만 정석은 git push -u origin main