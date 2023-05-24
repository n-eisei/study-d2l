このレポジトリはD2L勉強支援が目的です

# D2LのVM実行環境

## 前提
  - インターネット接続
  - Dockerインストール済み

## dockerイメージをダウンロード
   ```
    docker pull sunylab/d2l:1.0
   ```
## D2Lソースコードをjupyterで実行する
  [D2L Colab Classic](https://github.com/d2l-ai/d2l-pytorch-colab-classic.git)を例として、

- コードをダウンロード
   ```
   wget https://github.com/d2l-ai/d2l-pytorch-colab-classic/archive/refs/heads/master.zip
   ```
   windowsで,下記実施によるダウンロード
    ```
   １．https://github.com/d2l-ai/d2l-pytorch-colab-classic ページの右上「code」→download zip
   ２．自分のPCに解凍
   例：C:\Users\syq\d2l-pytorch-colab-classic-master
   ```
   
- 生成されたd2l-pytorch-colab-classicフォルダに入る。

   ```
   cd d2l-pytorch-colab-classic

- カレントフォルダの中身をリストアップすると、下記のようになる。

   ```
   d2l-pytorch-colab-classic > ls
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
  `pwd`はカレントフォルダのパスを表す。下記の例では、カレントフォルダはd2l-pytorch-colab-classicである。
  
   (linux /mac )
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v `pwd`:/root/study sunylab/d2l:1.0
   ```
   (power-shell)
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v ${PWD}:/root/study sunylab/d2l:1.0
   ```
   
   - ”--rm”オプションはコンテナ終了後に自動削除する。毎回クリーンな環境で実行したいならおすすめ。
   - ”-ti”オプションは、実行中のコンテナをcontrol-Cで終了できるようにする。これをつけなければ、コンテナの実行を終了するには[docker stop]コマンドが必要。
   - "--name d2l"は、起動したコンテナを識別するため。
   - "-p 8188:8188"はホストの8188ポートとコンテナの8188ポートにマッピングする。
   - “-v `pwd`:/root/study”はカレントフォルダをコンテナの中の[/root/study]フォルダにマッピングする。

- ブラウザを開いて http://localhost:8188 ページを開く
  jupyterの画面に【/root/study】フォルダにあるjupyterファイルを開いて実行を試してください。

## 終了時、docker退出
-　ctr-cで退出、dockerを閉じる

## 毎回の再開
- dockerコンテナを起動する
  `pwd`はカレントフォルダのパスを表す。下記の例では、カレントフォルダはd2l-pytorch-colab-classicである。
  
   (linux /mac )
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v `pwd`:/root/study sunylab/d2l:1.0
   ```
   (power-shell)
   ```
   docker run --rm -ti --name d2l -p 8188:8188 -v ${PWD}:/root/study sunylab/d2l:1.0
   ```

