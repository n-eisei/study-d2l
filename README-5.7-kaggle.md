### D2Lソースコードダウンロード　（d2l-pytorch フォルダが自動作成される）

```
git clone  https://github.com/dsgiitr/d2l-pytorch.git
```
### d2l-pytorch フォルダの下にdockerコンテナ実行

```
docker run --rm -ti --name jupyter -p 8188:8188 -v `pwd`:/root/study -ti  sunylab/d2l:1.1
```

### localhost:8188にアクセス

### terminalを開き、必要なライブラリを追加インストールする

```
bash
pip install tqdm
pip install opencv-python
apt-get update && apt-get upgrade -y
apt-get install -y libgl1-mesa-dev
```

### Jupyter実行する
- Jupyterファイルを開き　（Ch06_Multilayer_Perceptrons/Predicting_House_Prices_on_Kaggle.ipynb）、すべてのcellsを実行する

