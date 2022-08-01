---
title: "PostgreSQL의 설치와 설정"
date: '2022-07-29 03:00'
---
# PostgreSQL의 설치와 설정

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled.png)

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%201.png)

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%202.png)

```
sudo apt-get install postgresql-11

sudo apt-get update

sudo apt-get -y upgrade

sudo apt-get install postgresql postgresql-contrib

psql --version

sudo pg_ctlcluster 12 main start

sudo -u postgres psql

postgres=# ALTER USER postgres WITH PASSWORD '1234';
ALTER ROLE
postgres=# \q

sudo -u postgres createdb dataengineering

sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add

sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list && apt update'
```

```
## Install pgAdmin (아래3개 중 선택)
# Install for both desktop and web modes:
sudo apt install pgadmin4

# Install for desktop mode only:
sudo apt install pgadmin4-desktop

# Install for web mode only: 
sudo apt install pgadmin4-web
```

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%203.png)

```
sudo /usr/pgadmin4/bin/setup-web.sh

Email address: sallyzmk@naver.com
password: 123456
```

password: 1234

```
sudo -b unshare --pid --fork --mount-proc /lib/systemd/systemd --system-unit=basic.target

sudo -E nsenter --all -t $(pgrep -xo systemd) runuser -P -l $USER -c "exec $SHELL"
```

password: 1234

```
sudo vi /etc/postgresql/12/main/postgresql.conf
```

i 누르고 —INSERT— 상태로 만든다.

listen_addresses = 'localhost’ 주석처리를 풀어준다

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%204.png)

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%205.png)

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%206.png)

```
sudo /usr/pgadmin4/bin/setup-web.sh
```

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%207.png)

### [http://localhost/pgadmin4/](http://localhost/pgadmin4/)

password: 123456

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%208.png)

add new server 들어가서

이름 바꾸고

Host name/address : locallhost

Username : postgress

Password : 1234

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%209.png)

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%2010.png)

![Untitled](images/PostgreSQL_installation_and_configuration/Untitled%2011.png)

## 끝낼 때 명령어

```
sudo service postgresql stop
```