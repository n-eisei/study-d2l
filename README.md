このレポジトリはD2L勉強支援が目的です

# D2LのVM実行環境

## 前提
  - インターネット接続
  - Dockerインストール済み
   
## D2Lソースコードをjupyterで実行する

  [D2L Colab](https://github.com/n-eisei/d2l-pytorch-colab.git)コードを使って作業を進める。  
  ※D2Lのバージョン問題が起きたので、d2l-pytorch-colab　Version 1.0.0-beta0に統一する。

- コードをダウンロードして解凍
  - linux
    - ダウンロード：
     ```
     wget https://github.com/n-eisei/d2l-pytorch-colab/archive/refs/heads/master.zip
     ```
     或いは
     ```
     curl -OL https://github.com/n-eisei/d2l-pytorch-colab/archive/refs/heads/master.zip
     ```

     - 解凍：
     ```
     unzip master.zip -d d2l-pytorch-colab
     ```

      或いはgitコマンドでソースコードを取得する
      ```
      git clone https://github.com/n-eisei/d2l-pytorch-colab.git
      ```
  - windows
    - ダウンロード(cmd)：
      ```
      curl -OL https://github.com/n-eisei/d2l-pytorch-colab/archive/refs/heads/master.zip
      master.zipファイルを自分のPCの適当な場所に解凍（ソースコードフォルダd2l-pytorch-colabが生成される）
      ```

      或いは 
      ```
      https://github.com/n-eisei/d2l-pytorch-colab ページの右上「code」→download zip
      master.zipファイルを自分のPCの適当な場所に解凍（ソースコードフォルダd2l-pytorch-colabが生成される）
      ```

      或いはgitコマンドでソースコードを取得する
      ```
      git clone https://github.com/n-eisei/d2l-pytorch-colab.git
      ```
    
- 生成されたd2l-pytorch-colabフォルダに入る（d2l-pytorch-colab-masterなど生成されたフォルダ名が違うならそのフォルダに合わせて使ってもよい）。

   ```
   cd d2l-pytorch-colab
   ```

- dockerコンテナを起動する
  
   (linux /mac )
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v $(pwd):/root/study sunylab/d2l:1.2
   ```
   (power-shell)
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v ${PWD}:/root/study sunylab/d2l:1.2
   ```
   
   - ”--rm”オプションはコンテナ終了後に自動削除する。毎回クリーンな環境で実行したいならおすすめ。
   - ”-ti”オプションは、実行中のコンテナをcontrol-Cで終了できるようにする。これをつけなければ、コンテナの実行を終了するには[docker stop]コマンドが必要。
   - "--name d2l"は、起動したコンテナを識別するため。
   - "-p 8188:8188"はホストの8188ポートとコンテナの8188ポートにマッピングする。
   - "$(pwd):/root/study" また、“${PWD}:/root/study"　はカレントフォルダをコンテナの中の[/root/study]フォルダにマッピングする。上記の例では、カレントフォルダはd2l-pytorch-colabである。

- ブラウザを開いて http://localhost:8188 ページを開く
  jupyterの画面に【/root/study】フォルダにあるjupyterファイルを開いて実行を試してください。

## 終了時、docker退出
-　ctr-cで退出、dockerを閉じる
-　”Shutdown this Jupyter server (y/[n])?”が出た場合は、yを入れる。

## 毎回の再開

- d2l dockerコンテナを起動する
  
  ※　カレントフォルダはd2l-pytorch-colabである。
  
  - linux /mac
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v `pwd`:/root/study sunylab/d2l:1.2
   ```
   - power-shell
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v ${PWD}:/root/study sunylab/d2l:1.2
   ```
   
 ## d2l dockerコンテナ既に起動中の場合
   - 下記のエラーが出た場合、コンテナがすでに起動中
   ```
   docker: Error response from daemon: Conflict. The container name "/d2l" is already in use by container "7bb7ab7745185c454955f5f73a327804fda3b07d7f79f1581d2fc5a2ca4b385e". You have to remove (or rename) that container to be able to reuse that name.
   ```
   - この場合の対策
      - コンテナが正常に起動中でしたら、ブラウザを開いて http://localhost:8188 ページを開く、
      - 起動しているコンテナを下記のコマンドで終了して、「毎回の再開」の手順でコンテナを再起動する
        ```
        docker stop d2l
        ```
 

### 日本語メニューに切り替える
![image](./images/jp-menu.jpg)
