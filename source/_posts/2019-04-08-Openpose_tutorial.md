---
title: "Openpose 설치 tutorial"
categories:
  - "code"
tag:
  - "deep learning"
toc: true
toc_sticky: true
date: 2019/4/8
comments: true
mathjax: true
updated: 2019-08-07
---

## Openpose install

### requirement

> NVIDIA CUDA_(그래픽카드 메모리가 1.6GB이상이여한다.)
> NVIDIA cuDNN 

### Clone OpenPose

`$ git clone https://github.com/CMU-Perceptual-Computing-Lab/openpose`

openpose/3rdparty 폴더에 가보면

![alt](/images/Deep-learning/Openpose/Openpose_tutorial.png)

이렇게 되어있을텐데 openpose github페이지에 가서 3rdparty에 들어간다.

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(2).png)

여기서 caffe,pybind11에 들어가 깔아둔 openpose/3rdparty에 복사한다.

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(3).png)

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(4).png)

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(5).png)

~~~ r
# openpose/3rdparty에서 터미널 실행하고

$ git clone https://github.com/CMU-Perceptual-Computing-Lab/caffe.git

$ git clone https://github.com/pybind/pybind11.git
~~~

### install library

~~~ r
$ sudo apt-get install wget vim cmake cmake-qt-gui

$ sudo apt-get install python-dev python-pip python-numpy

$ pip install --upgrade pip

$ sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev

$ sudo apt-get install libhdf5-serial-dev protobuf-compiler

$ sudo apt-get install libboost-all-dev libgoogle-glog-dev

$ sudo apt-get install liblmdb-dev libopenblas-dev libatlas-base-dev
~~~

### cmake

터미널 창에 `cmake-gui` 입력

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(6).png)

다음과같이 

where is the source code: Openpose 주소

where to build the binaries: openpose/build 로 바꿔준다.

그리고 configure를 눌러준다.

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(7).png)

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(8).png)

이런창이 나오면 generate 버튼을 클릭하고 완료되면 build 폴더로 간다.

`cd openpose/build/`

그리고 make 해준다

`make -j 8`

## Demo 실행

make가 완료되면 

`./build/examples/openpose/openpose.bin --video examples/media/video.avi`

을 시키고 잘작동하는지 확인한다

![alt](/images/Deep-learning/Openpose/Openpose_tutorial_(9).png)

## TODO

tf버전 Openpsoe 추가


