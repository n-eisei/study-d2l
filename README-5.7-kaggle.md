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
- Jupyterファイルを開き　（chapter_multilayer-perceptrons/kaggle-house-price.ipynb）、すべてのcellsを実行する

