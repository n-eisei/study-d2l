### 1. D2Lソースコードダウンロード　（d2l-pytorch フォルダが自動作成される）

```
git clone  https://github.com/d2l-ai/d2l-pytorch-colab.git
```
### 2. d2l-pytorch フォルダの下にdockerコンテナ実行

```
docker run --rm -ti --name jupyter -p 8188:8188 -v `pwd`:/root/study -ti  sunylab/d2l:1.1
```

### 3. Jupyter環境にアクセス
ブラウザを開く、URLに http://localhost:8188

### 4. Jupyter実行する
- 下記の修正したJupyterファイルを使ってください

  https://github.com/n-eisei/d2l-pytorch-colab/blob/master/chapter_multilayer-perceptrons/kaggle-house-price-modification.ipynb

### 5. 修正した箇所(赤い下線を示す３つの箇所）

#### 5.1 import numpy
  ![image](https://github.com/n-eisei/study-d2l/blob/main/kaggle-screen1.jpg)

#### 5.2 x.values   =>  numpy.array(x.values.tolist())
 ![image](https://github.com/n-eisei/study-d2l/blob/main/kaggle-screen2.jpg)

#### 5.3 data.val.values => numpy.array(data.val.values.tolist())
![image](https://github.com/n-eisei/study-d2l/blob/main/kaggle-screen3.jpg)



