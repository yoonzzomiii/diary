============================================
8-1 판다스 데이터의 구조

* pandas는 외부 패키지이지만 아나콘다에 기본적으로 설치되어 제공되기 때문에 별도 설치할 필요가 없다.
* pandas는 관용적으로 pd라는 별칭을 사용한다.



import pandas as pd

# 데이터프레임 만들기
* 데이터프레임 : 엑셀의 시트(sheet)와 동일한 개념이다. (2차원 표 형태)

## 리스트로 만들기
* pd.DataFrame(2차원리스트, columns=컬럼리스트, index=인덱스리스트)
* 행 단위로 데이터프레임이 생성된다.
* 컬럼, 인덱스를 지정하지 않으면 디폴트로 0부터 시작하는 숫자가 지정된다.

df = pd.DataFrame(
    [['james',30,'programmer'],
    ['amy',20,'student'],
    ['david',25,'designer']],
    columns=['name','age','job'], #칼럼에 정의. 이름 부여  >> 헤더 생성
    index=['a','b','c']           #row(index) 정의
)

df

## 딕셔너리로 만들기   {키값:value값, 키값2:value값2}
* pd.DataFrame(딕셔너리, index=인덱스리스트)
* 딕셔너리는 {컬럼명1:컬럼값리스트, 컬럼명2:컬럼값리스트...}
* 컬럼 단위로 데이터프레임이 생성된다.
* 딕셔너리의 키가 컬럼명이 된다.
* 인덱스를 지정하지 않으면 디폴트로 0부터 시작하는 숫자가 지정된다.  0, 1, 2, ...

df = pd.DataFrame(
    {'name':['james',30,'programmer'], 'age': [30,20,25],
 'job':['programmer','student','designer']
})

df   # 인덱스를 지정하지 않으면 디폴트로 0부터 시작하는 숫자가 지정된다. 0, 1, 2, ...

{'name':['james','amy','david'],
 'age':[30,20,25],
 'job':['programmer','student','designer']
}

df = pd.DataFrame(
    {'name':['james','amy','david'],   #딕셔너리 {}
     'age':[30,20,25],
     'job':['programmer','student','designer']
    },
    index=['a','b','c']    #인덱스 정의 부여(없으면 0, 1, 2, ...)
)

df

## csv 파일에서 데이터를 읽어와 만들기
* pd.read_csv(파일경로)
* csv파일은 utf-8 형식이어야 한다.

import pandas as pd
pd.read_csv('C:\Pandas/data/scores.csv')

pwd

df = pd.read_csv('data/scores.csv')
df

=========================================
8-2 데이터 확인하기

import pandas as pd
df = pd.read_csv('data/scores.csv')

# 데이터 미리보기

## 가장 앞의 n행 보기
* 데이터프레임.head(n)
* 시리즈.head(n)
* n을 생략하면 5개의 행을 출력한다

df.head(3)

## 가장 뒤의 n행 보기
* 데이터프레임.tail(n)
* n을 생략하면 5개의 행을 출력한다

df.tail()

## 랜덤 보기

### 랜덤 n개 데이터 보기
* 데이터프레임.sample(n)
* n을 생략하면 1개의 샘플을 출력한다.

df.sample()

### 랜덤 샘플 비율로 보기
* 데이터프레임.sample(frac=0.2)
* 지정한 비율의 샘플을 출력한다

df.sample(frac=0.2)

## 높은 순/낮은순 보기

### 높은순 보기
* 데이터프레임.nlargest(갯수,컬럼명)
* 컬럼의 데이터가 숫자형일 때 사용할 수 있다.

# eng 높은 순으로 5개 보기
df.nlargest(5,'eng')

### 낮은순 보기
* 데이터프레임.nsmallest(갯수,컬럼명)
* 컬럼의 데이터가 숫자형일 때 사용할 수 있다.

# eng 낮은 순으로 5개 보기
df.nsmallest(5,'eng')

# 데이터 요약 보기

## (행,열)의 크기 보기
* 데이터프레임.shape

df.shape

## 데이터의 갯수 보기
* len(데이터프레임)

len(df)

## 컬럼명 보기
* 데이터프레임.columns
* 데이터프레임의 열 이름을 확인한다.

df.columns

## 인덱스 보기
* 데이터프레임.index
* 데이터프레임의 인덱스를 확인한다.

df.index

df

## 데이터의 자료형 보기
* 데이터프레임.dtypes
* 데이터프레임을 구성하는 값의 자료형을 확인한다.
* 판다스에서는 문자열의 데이터타입이 object이다.

df.dtypes

## 데이터프레임 정보 보기
* 데이터프레임.info()
* 데이터프레임의 총 샘플 갯수, 컬럼 수, 컬럼 별 정보 등을 확인한다.

df.info()

## 컬럼의 유니크한 데이터 뽑기
* 컬럼.unique()

df['kor'].unique()



## 컬럼의 유니크한 값의 갯수 보기
* 컬럼.**value_counts()**

df['kor'].value_counts()

## 요약통계 보기

df.describe()

df['kor'].mean()

===============================================
8-3 시리즈 다루기

import pandas as pd

# 시리즈 만들기
* pd.Series(리스트)
*시리즈 : 엑셀시트의 열 1개를 의미한다.(1차원 리스트형태)

# 시리즈 만들기
s = pd.Series(['amy',170,240])
s.index
s

s.values

s2 = pd.Series([10, 20, 30, 40, 50])
s2.std() #표준편차

s2 = pd.Series([10, 20, 30, 40, 50])
s2.describe()

s2 = pd.Series([10, 20, 30, 40, 50])
s2.sort_index()

s2 = pd.Series([10, 20, 30, 40, 50])
s2.reset_index()

s2 = pd.Series([10, 20, 30, 40, 50])
s2.replace(10,5)    #10을 5로 바꾸기   but 저장해야 5로 출력됨

s2

s2 = pd.Series([10, 20, 30, 40, 50])
s3 = s2.replace(10,5)    # 10 > 5 교체한 것 저장

s3

# 타입 확인하기
type(s)

# 시리즈의 index와 value 가져오기
* 시리즈에는 index와 value가 있다.
* 시리즈의 index 가져오기 : **시리즈.index**
* 시리즈의 value 가져오기 : **시리즈.values**
* 시리즈의 인덱스는 리스트의 인덱스와 다른 개념이다.       
시리즌의 인덱스는 데이터의 이름이고, 행번호는 따로 있다.


# 시리즈 인덱스 가져오기
s.index

# 시리즈 데이터 가져오기
s.values

# 시리즈의 index 지정하기
* 시리즈.index = 인덱스리스트
* 시리즈의 인덱는 숫자, 문자열 모두 가능하다.

# 시리즈 인덱스 지정하기
s.index = ['name','height','footsize']

# 시리즈 출력하기
s

# 인덱스 확인하기
s.index

# 데이터 확인하기
s.values

# 시리즈의 통계값 사용하기
* 평균 : 시리즈.mean()
* 최소값 : 시리즈.min()
* 최대값 : 시리즈.max()
* 중간값 : 시리즈.median()
* 표준편차 : 시리즈.std()
* 시리즈의 통계값은 시리즈의 value가 모두 숫자형일 때 사용할 수 있다.

s2 = pd.Series([10,20,30,40,50])

print('평균:',s2.mean())
print('최소값:',s2.min())
print('최대값:',s2.max())
print('중간값:',s2.median())
print('표준편차:',s2.std())

* 요약통계 : 시리즈.describe()

s2.describe()

# 시리즈 주요 메서드
* 값 정렬 : 시리즈.**sort_values( )**
* 인덱스 정렬 : 시리즈.**sort_index( )**
* 인덱스 리셋 : 시리즈.**reset_index( )**  --> 행번호로 인덱스 재지정
* 특정 값을 가진 시리즈 값을 교체 : **replace(찾을값, 교체할값)**
* 시리즈를 데이터프레임으로 변환 : **시리즈.to_frame( )**

s3 = pd.Series([1,3,2,4,10])

# s3의 value 중 10을 5로 교체
s3 = s3.replace(10,5)
s3

# s3 sort : 정렬 (디폴트는 오름차순 : ascending=True)
s3.sort_values()   #인덱스 깨짐. 값을 오름차순으로

s3 = pd.Series([1,3,2,4,10])
s4 = s3.sort_values()  

s4.reset_index()

s3.sort_values(ascending=False)

# s3을 데이터프레임으로 만들기
s3.to_frame()

# 시리즈 인덱스 새로 만들기
s.reset_index()

=============================================
9-1 컬럼 명으로 데이터 추출하기

import pandas as pd
df = pd.read_csv('C:\Pandas/data/scores.csv')
df.head(3)

df

# 컬럼명으로 데이터 추출하기

## 시리즈 형태로 추출하기
* **데이터프레임명['컬럼명']  / 데이터프레임명["컬럼명"]**         
: 컬럼명은 1개만 지정할 수 있으며 대괄호 1개를 사용한다.
* **데이터프레임명.컬럼명**     
: 컬럼명에 공백이나 특수문자가 섞여있을 때는 사용할 수 없다.

# 'name'컬럼 추출하기
df1 = df['name']
df1.head(3)

df2 = df['name']
df2

# type
#df = df['name']
type(df)

# index
df.index

# values
df.values

# shape (30,) 30개의 인덱스, 1개의 칼럼. 칼럼 하나일 때는 표시x
df.shape

df = df[['name', 'kor','eng']]
print(df)

df = df[df['kor'] == 100]
print(df)

# 'eng'컬럼 추출하기
df.eng


import pandas as pd
df = pd.read_csv('C:\Pandas/data/scores.csv')
df.head(3)

df

# 'matn'컬럼 추출하기

df['math'].head(3)

df

## 데이터프레임 형태로 추출하기
* 데이터프레임명[**컬럼명리스트**]
* 대괄호안에 컬럼리스트가 들어간다.(**대괄호 2개**로 표현되어야한다.)

# 'name','kor' 컬럼 데이터 추출하기
df_name_kor = df[['name','kor']]   
df_name_kor.head(3)

import pandas as pd
df = pd.read_csv('C:\Pandas/data/scores.csv')
df.head(3)

df

# 'math' 컬럼을 데이터프레임 형태로 추출하기
df_math = df[['math']] 
df_math

# type
type(df_math)

## 조건에 따라 데이터 추출하기

### 조건의 결과에 따른 불린인덱스 추출
* 조건식의 결과에 따른 결과가 불린인덱스로 만들어진다.

# kor 점수가 100점인 데이터 불린인덱스
df['kor']==100

### 불린인덱스로 데이터 추출
* 불린인덱스를 **데이터프레임명[ ]**으로 감싸주면 True인 데이터만 추출된다.

# kor 점수가 100점인 데이터 추출
df[df['kor']==100]

df['kor']==100

### 여러 조건
* 논리연산자는 **'&' , '|' ,'~', '^'** 기호를 사용한다.
* 논리연산자를 사용할 때에는 **각 조건을 ()로 감싼다.**

# 한 과목이라도 100을 받은 학생 추출
df[(df.kor==100)|(df.eng==100)|(df.math==100)]   # or

# kor의 값이 60~90인 학생의 name, kor 추출

df[(df['kor']>=60)&(df['kor']<=90)] [['name','kor']]

### 특정 값을 가진 데이터만 추출
* 컬럼.isin(값리스트)

# 이름이 Amy인 데이터 추출
df[df['name'].isin(['Amy'])]

# 이름이 Amy, Rose인 데이터 추출
df[df['name'].isin(['Amy','Rose'])]

# kor이 50,100 데이터 추출
df[df['kor'].isin([50,100])]

### null 여부에 따른 데이터 추출
* 컬럼.isnull()   --> 해당 컬럼의 값이 null인 데이터 추출
* 컬럼.notnull()  --> 해당 컬럼의 값이 null이 아닌 데이터 추출

# kor이 null인 데이터 추출
df[df.kor.isnull()]

# kor이 null이 아닌 데이터 추출
df[df.kor.notnull()]

==================================================
9-2 인덱스로 데이터 추출하기

import pandas as pd
df = pd.read_csv('C:\Pandas/data/scores.csv')
df.index = 'i'+df.index.astype('str')
df.head()

# 인덱스로 행 데이터 추출하기
* 데이터프레임명.**loc[인덱스]**       
: 시리즈 형태로 추출한다. 하나의 인덱스만 사용 가능하다.
* 데이터프레임명.**loc[인덱스리스트]**    
: 데이터프레임 형태로 추출한다. 한개 이상의 인덱스를 사용할 수 있다.

## 시리즈 형태로 추출하기

df.loc['i2']

# 인덱스가 i3인 행 추출하여 s1에 담기
s1=df.loc['i3']
s

df

df.loc[:, ['name', 'kor'] ]   #인덱스 2개 이상이면 대괄호로
                              # : 모든 행을 가져옴

df.loc['i0':'i2',['name', 'kor'] ]   #0부터 2까지

df.loc['i0'::2,['name', 'kor'] ]    #0부터 2 간격으로 

df.loc['i0':'i10':2,['name', 'kor'] ]  #0부터 10까지 2 간격으로

df.loc[::2,['name', 'kor'] ] #처음부터 끝까지 2 간격으로 출력

# s1 type
type(s1)
s1

# s1 index
s1.index

# s1 value
s1.values

## 데이터프레임 형태로 추출하기

# 인덱스가 i1,i3,i5인 행 추출하기
df.loc[['i1','i3','i5']]

# 인덱스가 i3인 행을 데이터프레임 형태로 추출하기
df.loc[['i3']]

# 인덱스에 없는 값을 사용하면 error
df.loc[-1]

# 인덱스로 행,열 추출하기

## 인덱스, 컬럼에 해당하는 한개의 데이터 뽑아오기
* **loc[인덱스, 컬럼명]**

df.head(6)

# 인덱스 i1의 kor점수
df.loc['i1','kor']

# type
type(df.loc['i1','kor'])

## 특정 인덱스의 여러 컬럼 데이터 추출하기
* **loc[인덱스, 컬럼명리스트]**

# 인덱스 i1 name, kor
df.loc['i1',['name','kor']]

# type
type(df.loc['i1',['name','kor']])

## 여러 인덱스의 특정 컬럼 데이터 추출하기
* **loc[인덱스리스트,컬럼명]**

# 인덱스 i1,i3,i5의 name
df.loc[['i1','i3','i5'],'name']

# type
type(df.loc[['i1','i3','i5'],'name'])

## 여러 인덱스의 여러 컬럼 가져오기
* **loc[인덱스리스트, 컬럼명리스트]**

# 인덱스 i1,i3,i5의 name, kor
df.loc[['i1','i3','i5'],['name', 'kor']]

## 모든 행에서 특정 열 가져오기
* loc[:,컬럼명] 
* loc[:,컬럼명리스트]  

# 모든 행에서 'name' 가져오기
df.loc[:,'name']

# 모든 행에서 'name','math' 가져오기
df.loc[:,['name','math']]

# 모든 행에서 'name' 가져오기(데이터프레임)
df.loc[:,['name']]

================================================
9-3 행번호, 열번호로 데이터 추출하기

import pandas as pd
df = pd.read_csv('C:\Pandas/data/scores.csv')
#df.index = range(10,310,10)
df.index = 'i'+df.index.astype('str')
df.head()

# 행번호로 행 데이터 추출하기(iloc)
* 데이터프레임명.**iloc[행번호]**
* 데이터프레임명.**iloc[행번호리스트]**
* 데이터프레임명.**iloc[행번호슬라이스]**
* **음수**를 사용하면 행번호를 뒤에서부터 센다.


df.head()

## 시리즈 형태로 추출하기

# 첫번째 행 추출하기
df.iloc[0]   #loc는 명칭으로 찾고, iloc는 순서로 찾음

## 데이터프레임 형태로 추출하기

# 1,3,5번 행 추출하기
df.iloc[[1,3,5]]

# 첫번째 행 추출하기(데이터프레임)
df.iloc[[0]]

## 행번호 슬라이스로 추출하기

# 1~3행 추출하기
df.iloc[1:4]

# 1,3,5행 슬라이스
df.iloc[1:6:2]

# 1행 추출하기
df.iloc[1:2]

# 짝수 행번호의 데이터 추출하기
df.iloc[::2]

# 홀수 행번호의 데이터 추출하기
df.iloc[1::2]

df.iloc[0,[0,2]] #1번째 row에 대해 0, 2번 행 데이터 출력

print(df.iloc[:, 0:2])  #전체 행, 0-1까지의 열

print(df.iloc[:, [0,2]])

print(df.iloc[[0,2],[0,2]])

print(df.iloc[::,::])

## 음수 행번호로 추출하기

# 마지막행 추출하기
df.iloc[-1]

# 마지막 2개 행 추출하기(리스트)
df.iloc[[-2,-1]]  #뒤에서 두번째, 뒤에서 첫번째

# 마지막 2개 행 추출하기(슬라이스)
df.iloc[-2:-1]

# 마지막 2개 행 추출하기(슬라이스)
df.iloc[-2:]

# 행번호로 행,열 추출하기

## iloc[행번호,열번호]

df.head()  #head() : 앞에서부터 5개 출력

# 0번째 행, 0번째 열
df.iloc[0,0]

## iloc[행번호,열번호리스트]

# 0번째 행 kor, eng
df.iloc[0,[1,2]]

## iloc[행번호리스트,열번호]

# 1,3,4번째 행 kor
df.iloc[[1,3,4],1]

## iloc[행번호리스트,열번호리스트]

# 1,3,4번째 행 name, eng
df.iloc[[1,3,4],[0,2]]

## iloc[행번호슬라이싱, 열번호슬라이싱]
* iloc에서는  슬라이싱을 사용할 수 있다.
* iloc에서는 음수를 사용할 수 있다.

df.head()

# 0,1번째 행 0,1번째 열 슬라이싱
df.iloc[:2, :2]

# 1,3,5번째 행 0,2번째 열 슬라이싱
df.iloc[1:6:2, :3:2]

df.tail()

# 마지막행 1,3열 슬라이싱
df.iloc[-1,1:4:2]

# 모든행, 1열 
df.iloc[:,1]

# 모든행, 1,2열 
df.iloc[:,[1,2]]

===============================================
9-4 기본 그래프 그리기

import pandas as pd

# 멧플롯립 라이브러리 임포트

import matplotlib.pyplot as plt

import matplotlib.pyplot as pit

# x축 y축 데이터 준비

x = ['a','b','c','d','e']
y = [1,3,2,10,7]



# 그래프 그리기

## 선그래프

plt.plot(x,y)
plt.show()

## 막대그래프

plt.bar(x,y)
plt.show()

## 가로 막대그래프

plt.barh(x,y)
plt.show()

## 산점도

plt.scatter(x,y)
plt.show()

## 세가지 그래프를 한번에 그리고 옵션 추가하기

plt.scatter(x,y,label='scatter')
plt.bar(x,y,label='bar')
plt.plot(x,y,label='plot')
plt.title('Test Graph', size=15)
plt.xlabel('x')
plt.ylabel('y')
plt.legend()  #범례
plt.show()

# kor을 막대그래프로 비교하기

df = pd.read_csv('C:\Pandas/data/scores.csv')
df.head()

x = df['name']
y = df['kor']
plt.bar(x,y)
plt.xticks(rotation=90)  #값 90도로 회전
plt.title('Scores', size=20)
plt.xlabel('name')
plt.ylabel('kor_score')
plt.show()

