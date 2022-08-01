---
title: "Heroku 초기 설정"
date: '2022-08-01 01:00'
---
# Heroku 초기 설정

## [https://www.heroku.com/](https://www.heroku.com/)

## 1. 회원가입하기

![Untitled](images/Heroku_Initial_setting/Untitled.png)

![Untitled](images/Heroku_Initial_setting/Untitled%201.png)

### 입력한 이메일에 들어가 메시지 확인, 링크 클릭

![Untitled](images/Heroku_Initial_setting/Untitled%202.png)

### 비밀번호 설정

```
sallyzmk@naver.com

5953uhfexhmk!
```

### 허용 누르기

### 로그인 완료

![Untitled](images/Heroku_Initial_setting/Untitled%203.png)

---

## 2. heroku 웹사이트에서 새 app 만들기


### heroku 설치

### [https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)

### 윈도우64비트 설치

![Untitled](images/Heroku_Initial_setting/Untitled%206.png)

### 관리자 권한으로 실행

![Untitled](images/Heroku_Initial_setting/Untitled%207.png)

### 환경변수 주의 (설정 별도 조정 없이 그대로 설치)

![Untitled](images/Heroku_Initial_setting/Untitled%208.png)

### 설치완료

---

## 3. 깃허브에서 **Repository** 만들기

- Repository name : heroku-human-본인이름
- Add a README file
- .gitignore template을 python으로 설정

<aside>
💡

### **주의**

- ‘_’ 쓰면 안됨 ‘-’는 괜찮음
- Repository name은 타인과 중복되면 안됨 (특이한 것 사용)
- Repository name : heroku-human-본인이름

### **[이유]**

git-repo —> 다운로드(로컬) —> Heroku에 배포

- 이름이 동일하면 안 먹을 수 있음

Heroku 앱 이름 생성 후 —> 다운로드 —> github에 올림

</aside>

![Untitled](images/Heroku_Initial_setting/Untitled%209.png)

### 바탕화면에 깃파일 땡겨오기

![Untitled](images/Heroku_Initial_setting/Untitled%2010.png)

![Untitled](images/Heroku_Initial_setting/Untitled%2011.png)

---

## 4. heroku-huma-sallyzmk99파일 vscode 실행

![Untitled](images/Heroku_Initial_setting/Untitled%2012.png)

![Untitled](images/Heroku_Initial_setting/Untitled%2013.png)

### 가상환경 접속

![Untitled](images/Heroku_Initial_setting/Untitled%2014.png)

```
virtualenv venv

source venv/Scripts/activate

pip install Flask gunicorn
```

### 파일 생성 (requirements.txt)

![Untitled](images/Heroku_Initial_setting/Untitled%2015.png)

```
pip freeze > requirements.txt
```

![Untitled](images/Heroku_Initial_setting/Untitled%2016.png)

### 파일 생성 (app.py)

![Untitled](images/Heroku_Initial_setting/Untitled%2017.png)

![Untitled](images/Heroku_Initial_setting/Untitled%2018.png)

```
# -*- coding:utf-8 -*-
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def index():
    return "Hello World!"
```

---

## 5. 임시 웹 생성(hexo server와 비슷)

![Untitled](images/Heroku_Initial_setting/Untitled%2019.png)

```
export FLASK_ENV=development

export FLASK_APP=app

flask run

# 이때 뜨는 링크로 이동하면 임시 웹사이트가 열린다.
```

![Untitled](images/Heroku_Initial_setting/Untitled%2020.png)

---

## 6. 배포를 위한 셋팅

### app.py 파일에 아래 코드를 추가 작성한다.

![Untitled](images/Heroku_Initial_setting/Untitled%2021.png)

```
if __name__ == "__main__":
    app.run(port=5000)
```

### 파일생성  (Procfile)

![Untitled](images/Heroku_Initial_setting/Untitled%2022.png)

![Untitled](images/Heroku_Initial_setting/Untitled%2023.png)

```
web: gunicorn wsgi:app
```

### 파일생성  (wsgi.py)

![Untitled](images/Heroku_Initial_setting/Untitled%2024.png)

```
from app import app

if __name__ == "__main__":
    app.run()
```

### 터미널에서 python 버전 확인 (V는 반드시 대문자)

![Untitled](images/Heroku_Initial_setting/Untitled%2025.png)

```
python -V
```

### 파일생성  (runtime.txt)

![Untitled](images/Heroku_Initial_setting/Untitled%2026.png)

![Untitled](images/Heroku_Initial_setting/Untitled%2027.png)

```
# 띄어쓰기 주의! 다 붙여 써야한다. 안그럼 오류남.
# 본인의 python 버전을 써여한다. 작성자꺼 복붙하면 안됨.
python-3.9.12
```

### 아까 확인 한 python 버전을 적는다.

---

## 7. 깃허브 업로드

### 지금까지 작업한 내용을 깃허브에 업로드한다.

![Untitled](images/Heroku_Initial_setting/Untitled%2028.png)

```
git add .

git commit -m "update"

git push
```

![Untitled](images/Heroku_Initial_setting/Untitled%2029.png)

### 깃허브 repository에서 업로드 잘 되었는지 확인

---

## 8. heroku 로그인

```
heroku login

# 아무키 누르기
```

![Untitled](images/Heroku_Initial_setting/Untitled%2030.png)

![Untitled](images/Heroku_Initial_setting/Untitled%2031.png)

---

## 9. heroku 앱 생성

![Untitled](images/Heroku_Initial_setting/Untitled%2032.png)

```
heroku create heroku-human-본인이름
```

![Untitled](images/Heroku_Initial_setting/Untitled%2033.png)

### Creating~~이 뜬다면, heroku 앱이 만들어진 것.

### 만약 경고문이 뜬다면 이름 중복으로 인해 생성이 안된 것.

### 이름을 변경해야 한다.

![Untitled](images/Heroku_Initial_setting/Untitled%2034.png)

### 이때 뜨는 링크로 이동하면 임시 웹사이트가 열린다.

![Untitled](images/Heroku_Initial_setting/Untitled%2035.png)

---

## 10. heroku main

![Untitled](images/Heroku_Initial_setting/Untitled%2036.png)

```
git push heroku main
```

---

## 11. 기초설정을 완료했으면 앞으로 [app.py](http://app.py) 파일만 수정하면 된다.

### 폴더 생성(templates)

![Untitled](images/Heroku_Initial_setting/Untitled%2037.png)

### templates폴더 안에 파일 생성(index.html)

![Untitled](images/Heroku_Initial_setting/Untitled%2038.png)

![Untitled](images/Heroku_Initial_setting/Untitled%2039.png)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="{{ url_for('static', filename= 'css/style.css') }}">
    <title>FlaskBlog</title>
</head>
<body>
   <h1>aaaaa</h1>
</body>
</html>
```

### 임시 서버 생성

![Untitled](images/Heroku_Initial_setting/Untitled%2040.png)

```
flask run
```

![Untitled](images/Heroku_Initial_setting/Untitled%2041.png)

### 배포

```
git add .

git commit -m "update"

git push

git push heroku main
```

---

## 12.

### 폴더 생성(static)

### static폴더 안에 폴더 생성(css)

### static폴더 안에 css폴더 안에(staitic\css) 파일 생성(style.css)

```
h1 {
    border: 2px #eee solid;
    color: brown;
    text-align: center;
    padding: 10px;
}
```

### index.html 파일에 아래 코드를 추가 작성한다.

![Untitled](images/Heroku_Initial_setting/Untitled%2042.png)

```
<link rel="stylesheet" href="{{ url_for('static', filename= 'css/style.css') }}">
```

### 배포

```
git add .

git commit -m "update"

git push

git push heroku main
```