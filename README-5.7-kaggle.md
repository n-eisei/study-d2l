
### 1. Jupyter実行する
- 下記の修正したJupyterファイルを使ってください

  https://github.com/n-eisei/d2l-pytorch-colab/blob/master/chapter_multilayer-perceptrons/kaggle-house-price-modification.ipynb

### 2. 修正した箇所(赤い下線を示す３つの箇所）

#### 2.1 import numpy
  ![image](https://github.com/n-eisei/study-d2l/blob/main/kaggle-screen1.jpg)

#### 2.2 x.values   =>  numpy.array(x.values.tolist())
 ![image](https://github.com/n-eisei/study-d2l/blob/main/kaggle-screen2.jpg)

#### 2.3 data.val.values => numpy.array(data.val.values.tolist())
![image](https://github.com/n-eisei/study-d2l/blob/main/kaggle-screen3.jpg)



