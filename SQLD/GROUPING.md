### 그룹함수란?

![image](https://user-images.githubusercontent.com/78454649/157841353-feacc611-df95-4706-a4d3-83ac8c7cfad9.png)

<br/><br/>


### ROLLUP

![image](https://user-images.githubusercontent.com/78454649/157841474-c9d7bb63-61d1-403d-ba8f-c51319f55daa.png)

<br/>

여기서 DNAME의 소계는 파란줄이고 DNAME과 A.JOB의 소계는 가장 아래줄

<br/>

![image](https://user-images.githubusercontent.com/78454649/157842145-cb7895bc-3a8d-431b-82f5-e950c3d4edee.png)

<br/>

### GROUPING 함수


집계가 일어난 부분(행)은 SALES(D.NAME)에서 집계가 일어났다면 JOB은 그 안에서 할 수 있는게 없으니 null 형성

![image](https://user-images.githubusercontent.com/78454649/157843060-26d01c3c-57e4-441b-b1bb-a3607904de9a.png)


JOB이라는 칼럼에서 집계가 일어났어? 일어났으면 1 아니면 0출력

여기서는 SALE를 기준으로 누가 그루핑이 되었어? JOB의 칼럼들이 합쳐짐을 당했으니 JOB에 1이 들어간 것

<br/>

### CUBE함수

가능한 모든 조합의 집계 

여기서는 DNAME 별로 한 번, JOB 별로 한 번, DNAME + JOB , 전체 통계

![image](https://user-images.githubusercontent.com/78454649/157843842-5d962efe-1867-4fde-ab6d-ad30ac9c4fc0.png)

<br/>

### GROUPING SET

![image](https://user-images.githubusercontent.com/78454649/157844888-0fb2926a-76e1-49ca-b0e7-bccb84c02570.png)


DNAME : ACCOUNTING 아래에서 JOB을 조회하는 것 , JOB들을 DNAME 하에서 집계한것

ACCOUNTING은 JOB을 총 합해서 3명이고 ,  ANALIST는 DNAME 총합해서 2명

<br/>

### 정리

![image](https://user-images.githubusercontent.com/78454649/157844981-e58f33e5-392d-47c1-9bfa-372385bb109e.png)

