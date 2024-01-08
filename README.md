# PDFファイルからのテキスト抽出と統計解析
### 21RS001 青見俊
## 1.序論
　本章では、研究背景、研究目的、研究方法について述べる。
### 1-1.研究背景
　理工学部情報科学科では複数の研究室が存在しており、3年次の学生は卒業研究のために研究室に配属され教員の指導を受け、4年次に卒業研究を行う。  
　研究室配属では、配属調査を3年次の前期に行ない、その調査結果を基に決定している。
### 1-2.研究目的
　本研究の目的は、卒業論文のPDFファイルをテキスト抽出し、形態素解析を行なうことである。これにより、研究室ごとの特色を明確にすることができ、3年次の研究室配属や4年次の卒業研究テーマ選択において、参考材料になると考える。
### 1-3.研究方法
　Pythonのライブラリを用いてPDFファイルからテキスト抽出を行い、同じくPythonで形態素解析を行い、統計解析をする。
## 2.テキスト抽出と形態素解析
　本章では、本研究で使用する技術の概要を述べる。まず、2.1節ではテキスト抽出の基本事項について説明する。次に2.2節ではPDFファイルからのテキスト抽出について説明する。最後に、2.3節では形態素解析について説明する。
### 2-1.テキスト抽出の基本事項
　テキスト抽出とは、主に組版加工済の印刷用データから、再利用を目的としてプレーンなテキストデータを抽出すること。DTPアプリケーションや文書作成ソフトによっては、指定形式でのデータ出力機能を利用することもできる。基本的には、抽出データに対して、形式調整やクリーニングなどの後処理が必要になる。以下に主なテキスト抽出の手法を説明する。
* **DTPデータからのテキスト抽出**  
　主要なDTPアプリケーションは、タグ付テキストやXHTMLなどの形式を指定してテキストデータを出力する機能を備えており、「テキスト書き出し」と呼ぶこともある。EPUB形式で直接、電子書籍を出力できるものも多い。ただし、そのDTPアプリケーションでの組版加工時において後のテキスト書き出しを想定してレイアウトなどに十分な配慮を行った場合を除き、期待通りの二次利用に適した形でのテキストデータ取得は難しい。  
　一括でのテキスト書き出しは、その後のチェックと調整を考慮すると現実的とは言えず、ここはページ単位またはページ内のテキストブロック単位でコツコツとテキストをコピー＆ペーストしていくのが、遠回りのように見えて、結局、一番効率が良い。コピー＆ペーストの単位で書籍レイアウトと比較確認しながら、チェックと必要な調整を施しておくことも重要である。

* **PDFファイルからのテキスト抽出**  
　PDFファイルからのテキスト取り出しについても、上記同様、コツコツとコピー＆ペーストするのが一番安全ではある。一方、PDFを対象にしたテキスト抽出ツールも無料・有料合わせて多数存在するので、組版レイアウトの複雑さやコンテンツのボリュームなども勘案し、適切なものを選ぶ必要がある。

いずれの方法によるとしても、抽出・取得したテキストデータを原本と比較チェックし、調整を施すことは必須の作業である。
### 2-2.PDFファイルからのテキスト抽出
　現在PDFファイルからテキストを抽出する方法は多岐にわたる。本研究では、Pythonのライブラリを利用したPDFファイルからのテキスト抽出を行なう。そこでテキスト抽出の主なライブラリとその特徴についてまとめたものを記述する。

### 3-1.研究の流れ
①各研究室の卒業論文のPDFファイルを収集し、フォルダにまとめる。PDFファイルは理工学部情報科学科学生用Webサーバから収集する。各研究室ごとにフォルダを作成し、PDFファイルをまとめる。ファイル名は[研究室名_元号]とする。例えば、令和4年度の成研究室の場合`sei_r04`となる。

②PDFファイルからのテキスト抽出を行なう。フォルダにあるすべてのファイルを読み込み、テキスト抽出を行なう。

