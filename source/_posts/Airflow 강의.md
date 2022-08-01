---
title: "Airflow 강의"
date: '2022-07-29 01:00'
---
# Airflow 강의

## [airflow tutorial]([https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html))

## [airflow 추천 도서]([http://www.yes24.com/Product/Goods/107878326](http://www.yes24.com/Product/Goods/107878326))

## 내가 생각하는 Airflow 정의

데이터는 끊임없이 생성이 된다.

하여 데이터 분석가는 데이터를 잘 정리하여 수시로 데이터 베이스DB에 업데이트 해야 한다.

Airflow는 수시로 데이터 베이스를 업데이트 하는 것을 자동으로 실행해 주는 프로그램이다.

---

# [3.1 파이썬으로 파일 쓰고 읽기]

- 교재 <실무 예제로 배우는 데이터 공학> 41p~50p

## step1.py 파일 생성 및 하단 코드 입력

```python
import pandas as pd
import faker

print(pd.__version__)
```

## write_df.py 파일 생성 및 하단 코드 입력

```python
from faker import Faker
import csv

def main():
    output = open('data.csv',mode='w')
    fake=Faker()
    header=['name','age','street','city','state','zip','lng','lat']
    mywriter=csv.writer(output)
    mywriter.writerow(header)

    for r in range(1000):
        mywriter.writerow([fake.name(),fake.random_int(min=18, max=80, step=1), fake.street_address(), fake.city(),fake.state(),fake.zipcode(),fake.longitude(),fake.latitude()])
    output.close()

if __name__ == "__main__":
    main()
```

## read_df.py 파일 생성 및 하단 코드 입력

```python
import csv

def main():
    with open('data.csv') as f:
        myreader = csv.DictReader(f)
        headers = next(myreader)
        for row in myreader:
            print(row['name'])

if __name__ =="__main__":
    main()
```

## write_df_pd.py 파일 생성 및 하단 코드 입력

```python
import pandas as pd

def main():
    data = {'Name':['Paul', 'Bob', 'Susan','Yolanda']
    ,'Age':[23,45,18,21]}
    df=pd.DataFrame(data)
    df.to_csv('fromdf.CSV',index=False)

if __name__ =="__main__":
    main()
```

## read_df_pd.py 파일 생성 및 하단 코드 입력

```python
import pandas as pd

def main():
    df = pd.read_csv('data.csv')
    df.head(10)
    # print(df)

    

if __name__=="__main__":
    main()
```

## write_json_df.py 파일 생성 및 하단 코드 입력

```python
# -*- coding: utf-8 -*-
from faker import Faker
import json

def main():
    output = open('data.json','w')
    fake = Faker()
    alldata ={}
    alldata['records'] = []

    for X in range(1000):
        data={"name":fake.name(),"age":fake.random_int(min=18, max=80, step=1),"street":fake.street_address(),"city":fake.city(),"state":fake.state(),"zip":fake.zipcode(),"lng":float(fake.longitude()),"lat":float(fake.latitude())}
        alldata['records'].append(data)
    json.dump(alldata,output)

if __name__ == "__main__":
    main()
```

## read_json_df.py 파일 생성 및 하단 코드 입력

```python
# _*- coding: utf-8 -*-

import json
import pandas as pd
import pandas.io.json as pd_JSON

def read_json():
    with open("data.json","r") as f:
        data= json.load(f)

    print(type(data))
    print(data['records'][0]['name'])

def read_pandas():
    df = pd.read_json('data.json')
    print("기본 방법은 조금 복잡해요! :\n", df.head())

    f=open('data.json','r')
    data = pd_JSON.loads(f.read())
    #print(data)
    df = pd.json_normalize(data,record_path='records')
    print("다른 방법도 복잡해요 :\n", df.head())

if __name__ == "__main__":
    # read_json()
    read_pandas()
```

---

# [3.2 아파치 에어플로 데이터 파이프라인 구축]

- 교재 <실무 예제로 배우는 데이터 공학> 51p~57p

## Airflow 들어가기

### dags 폴더 만들기

### data.csv 파일 dags폴더로 옮기기

### airflowcsv.py 파일 생성 및 하단 코드 입력

```python
# -*- coding: utf-8 -*-
# 51p
import datetime as dt
from datetime import timedelta

import airflow
from airflow import DAG
from airflow.operators.bash import BashOperator
from airflow.operators.python import PythonOperator

import pandas as pd

# print(pd.__version__)
# print(airflow.__version__)

def csvToJson():
    df=pd.read_csv('dags/data.csv')
    for i,r in df.iterrows():
        print(r['name'])
    df.to_json('fromAirflow.json',orient='records')

	

default_args = {
    'owner': 'evan',
    'start_date': dt.datetime(2022, 7, 27),
    'retries': 1,
    'retry_delay': dt.timedelta(minutes=1),
}

with DAG('MyCSVDAG',
         default_args=default_args,
         schedule_interval=timedelta(minutes=1),      # '0 * * * *',
         ) as dag:

    print_starting = BashOperator(task_id='starting',
                               bash_command='echo "I am reading the CSV now....."')
    
    csvJson = PythonOperator(task_id='convertCSVtoJson',
                                 python_callable=csvToJson)

print_starting >> csvJson
```

### airflow.cfg 파일에서 해당 코드 찾아서 False로 고쳐주기

```
load_examples = False
```

### 터미널 2개에서 하단 코드 실행

- 우리는 평소 1개의 터미널에서 명령어를 실행한다.
- 평소처럼 터미널을 1개 실행한 후 +버튼으로 새 터미널을 열면 된다.
- 그럼 터미널 2개 생김!!!

![Untitled](images/Airflow_lecture/Untitled.png)

```
# 경로 확인!!! airflow에서 실행, dags에서 실행하면 안됩니다.

source venv/bin/activate
airflow webserver -p 포트번호

source venv/bin/activate
airflow scheduler
```

### 인터넷 창에 ‘localhost: 포트번호’를 입력하면 아래 창이 뜬다.

localhost:1234

### 아래 버튼을 활성화 시킨다.

![Untitled](images/Airflow_lecture/Untitled%201.png)

![Untitled](images/Airflow_lecture/Untitled%202.png)

### MyC SVDAG 클릭

- 실시간으로 데이터 자동 업데이트가 잘 진행되고 있는지 확인할 수 있다.

![Untitled](images/Airflow_lecture/Untitled%203.png)