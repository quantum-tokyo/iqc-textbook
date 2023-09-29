# 制作方法

現在は Community Internal の活動です。

## ローカルでの作業

### 必要なライブラリのインストール

以下コマンドを実行して必要なライブラリをインストールする。

```
pip install -r requirements.txt
```

### Jupyter notebook の編集

コンテンツファイルは過去の Quantum Challenge の GitHub リポジトリから取得する。

以下TODO
- Qiskit ver0.44 で動作確認を行う
  - 廃止済み機能を利用しているものは新機能で作り直す
  - コードの改変がある場合はnotebookのタイトル下に以下のような注意書きブロックを加える

````
  ```{note}
  このNotebookはQiskit v0.44の仕様に合わせてコードを改変しています。
  ```
````

- 各Excersiseに対して解答・解説をつける
  - Excersiseのブロックはそのままで、以下のような解答ブロックと解説ブロックを追加する([サンプルファイル参照](https://github.com/quantum-tokyo/iqc-textbook/blob/main/src/sample-2023-spring-lab1-ja.ipynb))
  - （オプション）トピックに対して飛躍のある部分に解説をつける

解答ブロック
`````
  ````{dropdown} 解答
    ```python
    <ここに解答Qiskitコードを書きます>
    ```
  ````
`````

解説ブロック
````
  ```{admonition} 解説
  :class: tip
  <ここに解説を書きます>
  ```
````


- notebook のファイル名を変更する
  - ファイル名は目次ファイル`src/_toc.yml`を参照
- notebookの見出し構成を編集する
  - L1 見出し(`#`)はnotebook内で 1 つのみ（最初のタイトルのみ）
  - 複数の L1 見出しがある場合はレベルを1つずつ下げる
  - 見出し調整をしないと[サンプル](https://quantum-tokyo.github.io/iqc-textbook/intro.html)の様に1つのノートブックに複数のリンクが表れてしまう

### 画像ファイルの編集
- 画像ファイルがある場合は`src/resources`配下に`{年度}-{spring/autumn}-{識別ファイル名}`のファイル名で配置する（notebook 側の参照パスが変更されるので注意）

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
