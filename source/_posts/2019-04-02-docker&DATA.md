---
title: "Docker,XML,JSON,CSV 간단 공부"
date: 2019/4/2
categories:
  - "theory"
tag:
  - "deep learning"
last_modified_at: 2019-08-07
comments: true
mathjax: true

---

머신러닝, 딥러닝 실전 개발 입문 강의를 보고 공부한 내용입니다.

<https://www.youtube.com/watch?v=l_XFlB1Wwz8&list=PLBXuLgInP-5m_vn9ycXHRl7hlsd1huqmS&index=1>

## Docker
먼저 docker 이미지를 가져온다(miniconda: anaconda 패키지중 가장 기본적인것만 설치되어있음)
```
docker pull continuumio/miniconda3
```
설치가 다되었으면 아래 명령어로 이미지를 실행한다.
```
docker run -i -t continuumio/miniconda3 /bin/bash
```
|{% raw %}![alt](/images/Deep-learningetc/docker.png){% endraw %}|

위 이미지처럼 환경이 바뀌었으면 잘 작동한 것이다.

```
exit
```
를통해서 환경을 종료 할 수 있다.

아래 명령어를 입력하면

```
docker ps -a
```

|{% raw %}![alt](/images/Deep-learningetc/docker (2).png){% endraw %}|

위 그림과 같이 컨테이너 실행 기록을 확인할 수 있다.

```
docker commit 컨테이너 ID 이름:태그

ex) docker commit <a4997a3ede6e> mlearn:init
```
위 명령어로 통해 컨테이너 이미지를 저장할 수 있다.

```
docker run -i -t mlearn:init
```
위 명령어로 위에서 사용했던 환경과 똑같은 환경을 이용할 수 있다.

```
docker run -i -t -v 자신이 가진폴더:컨테이너의 폴더 이미지 이름:태그 이름

ex) docker run -i -t -v /home/kist-student/docker_sample:/sample mlearn:init
```
위 명령어로 폴더 마운트해서 이미지를 실행시킨다.

## XML(Extensible Markup Language)

### XML 형태

#### 여는 태그와 닫는 태그

1. <태그></태그> #요소(element)
2. <태그 />

#### 콘텐츠

<태그>콘텐츠</태그>
<태그>
    <태그>콘텐츠</태그>
    <태그>콘텐츠</태그>
</태그>

#### 속성: "" => 문자열
<태그  속성="값" 속성="값" 속성="값" 속성="값">콘텐츠</태그>
<태그  속성="값" 속성="값" 속성="값" 속성="값" />

|{% raw %}![alt](/images/Deep-learningetc/XML.png){% endraw %}|

Root tag 항상 하나
,CDATA 내부 글자가 클때 데이터 보호용,
rss는 태그이름

참고: <https://sjh836.tistory.com/118>

## JSON(JavaScript Object Notation)

### JSON 구조

#### 가능한 자료형

>숫자: 10, 253, 52.3

>문자열: "안녕하세요"

>bool: true false

>null: null

>배열:[10, 273, "안녕하세요", true]

객체:
```
{
    "키A": "값",
    "키B": 273,
    "키C": true,
    "키D": [12, 52]
    "키E": { "name": 52 }
}
```
|{% raw %}![alt](https://www.w3resource.com/w3r_images/json-introduction.png){% endraw %}|

처음에는 배열이나 객체가 먼저오는게 일반적

## CSV(Comma-Seperated Values) 

### CSV 특징
> 1. 한 줄에 데이터 하나
> 2. 첫 번쨰 줄은 헤더로 사용 가능
```
ID, 이름, 가격
1000,비누,300 # 1번 데이터
1001,장갑,150 # 2번 데이터
1002,마스크,230 # 3번 데이터
```

SSV: 뛰어쓰기
TSV: tab
CSV > TSV, SSV

xml 글자 많음(데이터 많음) > json > csv

표현력 많음: xml > json > csv

xml은 잘 쓰이지 않고 있다고함

## 참고

<https://www.youtube.com/watch?v=dmwBi_JiYMs&list=PLBXuLgInP-5m_vn9ycXHRl7hlsd1huqmS&index=12>

<https://sjh836.tistory.com/118>

<https://stophyun.tistory.com/162>

##TODO
데이터형 parsing 코드추가 및 docker 설명 추가
