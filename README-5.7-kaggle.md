### D2Lソースコードダウンロード　（d2l-pytorch フォルダが自動作成される）

```
git clone  https://github.com/d2l-ai/d2l-pytorch-colab.git
```
### d2l-pytorch フォルダの下にdockerコンテナ実行

```
docker run --rm -ti --name jupyter -p 8188:8188 -v `pwd`:/root/study -ti  sunylab/d2l:1.1
```

### localhost:8188にアクセス


### Jupyter実行する
- [修正したJupyterファイル](https://github.com/n-eisei/d2l-pytorch-colab/blob/master/chapter_multilayer-perceptrons/kaggle-house-price-modification.ipynb)を開き、すべてのcellsを実行する

### 修正した箇所

- [import numpy](./kaggle-screen1.jpg)

- [x.values   =>  numpy.array(x.values.tolist())](./kaggle-screen1.jpg)

- [data.val.values => numpy.array(data.val.values.tolist()) ](./kaggle-screen2.jpg)




