このレポジトリはD2L勉強支援が目的です

# D2LのVM実行環境

## 前提
  - インターネット接続
  - Dockerインストール済み
   
## D2Lソースコードをjupyterで実行する
  [D2L Colab Classic](https://github.com/d2l-ai/d2l-pytorch-colab.git)を例として、

- コードをダウンロードして解凍
  - linux/mac
    - ダウンロード：
     ```
     wget https://github.com/d2l-ai/d2l-pytorch-colab/archive/refs/heads/master.zip
     ```
     - 解凍：
     ```
     unzip master.zip
     ```
     
  - windows
    - ダウンロード(cmd)：
    ```
    curl -OL https://github.com/d2l-ai/d2l-pytorch-colab/archive/refs/heads/master.zip
    ```
    - 解凍：
    ```
    tar -xf master.zip
    ```
    
    或いは 
    ```
    １．https://github.com/d2l-ai/d2l-pytorch-colab ページの右上「code」→download zip
    ２．自分のPCに解凍
    ```
   
- 生成されたd2l-pytorch-colabフォルダに入る。

   ```
   cd d2l-pytorch-colab

- カレントフォルダの中身をリストアップすると、下記のようになる。

   ```
   d2l-pytorch-colab > ls
   README.md                                        chapter_deep-learning-computation                chapter_notation                                 d2l
   chapter_appendix-mathematics-for-deep-learning   chapter_generative-adversarial-networks          chapter_optimization                             d2l.bib
   chapter_appendix-tools-for-deep-learning         chapter_installation                             chapter_preface                                  img
   chapter_attention-mechanisms                     chapter_introduction                             chapter_preliminaries                            index.ipynb
   chapter_computational-performance                chapter_linear-networks                          chapter_recommender-systems                      setup.py
   chapter_computer-vision                          chapter_multilayer-perceptrons                   chapter_recurrent-modern
   chapter_convolutional-modern                     chapter_natural-language-processing-applications chapter_recurrent-neural-networks
   chapter_convolutional-neural-networks            chapter_natural-language-processing-pretraining  chapter_references
   ```

- dockerコンテナを起動する
  
   (linux /mac )
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v $(pwd):/root/study sunylab/d2l:1.1
   ```
   (power-shell)
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v ${PWD}:/root/study sunylab/d2l:1.1
   ```
   
   - ”--rm”オプションはコンテナ終了後に自動削除する。毎回クリーンな環境で実行したいならおすすめ。
   - ”-ti”オプションは、実行中のコンテナをcontrol-Cで終了できるようにする。これをつけなければ、コンテナの実行を終了するには[docker stop]コマンドが必要。
   - "--name d2l"は、起動したコンテナを識別するため。
   - "-p 8188:8188"はホストの8188ポートとコンテナの8188ポートにマッピングする。
   - "$(pwd):/root/study" また、“${PWD}:/root/study"　はカレントフォルダをコンテナの中の[/root/study]フォルダにマッピングする。上記の例では、カレントフォルダはd2l-pytorch-colab-classic-masterである。

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
   docker run --rm -ti --name d2l -p 8188:8188 -v `pwd`:/root/study sunylab/d2l:1.0
   ```
   - power-shell
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v ${PWD}:/root/study sunylab/d2l:1.0
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
 
