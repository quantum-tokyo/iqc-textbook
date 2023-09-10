# 制作方法

現在は Community Internal の活動です。

## ローカルでの作業

### 必要なライブラリのインストール

以下コマンドを実行して必要なライブラリをインストールする。

```
pip install -r requirement.txt
```

### コンテンツファイル編集

コンテンツファイルは過去の Quantum Challenge の GitHub リポジトリから取得する。

- 問題 Jupyter notebook の編集
  - Qiskit ver0.44 で動作確認を行い、廃止済み機能を利用しているものは新機能で作り直す
  - 回答に対する解説をつける
  - notebook のファイル名は目次ファイル`src/_toc.yml`を確認して同じ名前に変更する
  - L1 見出し(`#`)は**notebook 内で 1 つ（最初のタイトルのみ）**とし、複数の L1 見出しがある場合はレベルを下げる
  - （オプション）トピックに対して飛躍のある部分に解説をつける
- 画像ファイルの編集
  - 画像ファイルは`src/resources`配下に`{年度}-{spring/autumn}-{識別ファイル名}`のファイル名で配置する（notebook 側の参照パスが変更されるので注意）

### 目次ファイル編集

目次ファイル`src/_toc.yml`の自身の編集ファイル済みファイルのコメントを外す。  
例えば 2019 年 week1 の問題を追加する場合は`- file: 2019-w1-adder`の行のコメントを外す。

```yaml
# Table of contents
# Learn more at https://jupyterbook.org/customize/toc.html

format: jb-book
root: intro
defaults: # The defaults key will be applied to all chapters and sub-sections
  titlesonly: True
parts:
  - caption: "第２章 量子コンピューターの計算ルール"
    chapters:
  #  - file: 2019-w1-adder
```

## 動作確認

本リポジトリに Pull Request を送る前に正しく Web ページが表示されるか確認する。

```
jupyter-book build ./src/
```

コマンド実行後、`src/_build`にビルド済みファイルが生成されるためブラウザ等で自身が編集したページが正しく反映されているかを確認する。

ブラウザでの確認方法は、上記の`jupyter-book build`コマンドを実行後、以下のようなメッセージが表示されるので表示されるパスを参考に確認する。

```
===============================================================================

Finished generating HTML for book.
Your book's HTML pages are here:
    src/_build/html/
You can look at your book by opening this file in a browser:
    src/_build/html/index.html
Or paste this line directly into your browser bar:
    <!-- ローカルファイルのパス -->

===============================================================================
```
