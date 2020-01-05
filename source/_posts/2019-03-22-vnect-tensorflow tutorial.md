---
title: "VNect-tensorflow"
date: 2019/3/22
categories:
  - "code"
tag:
  - "deep learning"
updated: 2019-08-07
comments: true
mathjax: true
---

VNect Tensorflow버전 github: <https://github.com/timctho/VNect-tensorflow>

## 1. 먼저 VNect-Tensorflow를 git clone 해준다.

``` 
$ git clone https://github.com/timctho/VNect-tensorflow.git
```

## 2. caffe python버전과 opengl을 설치한다. 

caffe는 여러가지 설치법이 있지만 anaconda에서 Python3로 쉽게 설치하는 방법은 아래 사이트를 참고한다

<https://yangcha.github.io/Caffe-Conda3/>

opengl의 경우는

```
$ pip install PyOpenGL PyOpenGL_accelerate
```

으로 설치해주면 된다.

## 3. Vnect-Tensorflow가 설치된 폴더로 이동하고 caffe_weights_to_pickle.py를 실행한다.

먼저 Vnect-Tensorflow가 설치된 폴더로 이동한다.

``` 
$ cd VNect-tensorflow
```

그다음 환경을 자신이 caffe를 설치한 환경으로 바꿔준다.

``` 
$ source activate testcaffe 
```

이제 caffe로 만들어진 모델을 pickle 형식으로 바꿔준다.

``` 
$ python caffe_weights_to_pickle.py 
--prototxt=../Documents/VNECT/mpii_vnect_model_code/mpii_vnect_model_demo/models/vnect_net.prototxt      
--caffemodel=../Documents/VNECT/mpii_vnect_model_code/mpii_vnect_model_demo/models/vnect_model.caffemodel
```

주소가 복잡하면 VNect-Tensorflow에 있는 models 폴더안에

vnect_net.prototxt 와 

vnect_model.caffemodel 을 복사한후 

아래와 같이 실행시키면 

```
$ python caffe_weights_to_pickle.py 
```


`vnect.pkl` 이라는 파일이 만들어졌을것이다.

## 4. models 폴더안에 vnect_model.py 수정하고 실행에 필요한 모델파일 만들기

이유는 모르겠지만 직접 실행할때 필요한 모델을 만드는 파일이 없기에 models 폴더안에 vnect_model.py를 조금 수정해야한다.
코드를 보시면 맨아래 

` if __name__ == 'name':` 아래를

``` python
    model_file = '../vnect.pkl'
    model = VNect(368)

    with tf.Session() as sess:
        saver = tf.train.Saver()
        model.load_weights(sess, model_file)
        save_path = saver.save(sess, "./vnect_tf")
```

으로 바꿔주고 실행시키면 

```
 vnect_tf.data-00000-of-00001
 vnect_tf.index
 vnect_tf.meta 
```
세가지 파일이 만들어 졌을것이다.
이제 이 파일을 models/weights 안에 복사한다.

(weights폴더가 없으니 만들어주자)

## 5. demo_tf_gl.py로 테스트 해보자.

cudnn 오류때문에  
```
sess_config = tf.ConfigProto(device_count=gpu_count)
```

아래에 

```
sess_config.gpu_options.allow_growth = True
```

을 추가해준다.

그리고 
`--demo_type', default='image'`를 `--demo_type', default='webcam'`

으로 바꿔주면 웹캠으로 테스트가 가능하다.

## TODO

caffe 설치 오류 확인해보기

