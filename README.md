# Googleドライブフォルダコピー
## 概要
通常，Googleドライブ内のフォルダをコピーすることはできなく，手作業で１つずつコピーしていくしかない．<br>
このGASのコードはその作業を一括で行うものである．<br>
特に，複数の閲覧用のファイルを共有して自身のドライブにコピーしてもらいたいときに利用すると便利である．

## 使い方
1. コピーしたいフォルダの中に「新規>その他>Google Apps Script」を作成
2. 以下のテキストファイルの中身をコピーして貼り付けて実行

## 注意点
- 通常のファイルをコピーするときはそのまま利用できる<br>
- コピーするフォルダの中に**GASファイル**が含まれる場合は，左のサービスから「Drive API」を追加する必要がある
