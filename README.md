# 【Googleドライブフォルダコピー】
## 概要
通常，Googleドライブ内のフォルダをコピーすることはできなく，手作業で１つずつコピーしていくしかない．
このGASのコードはその作業を一括で行うものである．
特に，複数の閲覧用のファイルを共有して自身のドライブにダウンロードしてもらいたいときに利用すると便利である．

## 使い方
コピーしたいフォルダの中に「新規>その他>Google Apps Script」を作成
以下のコードをコピーして貼り付けて実行

## 注意点
通常のファイルをコピーするときはそのまま利用できる
コピーするフォルダの中にGASファイルが含まれる場合は，左のサービスから「Drive API」を追加する必要がある