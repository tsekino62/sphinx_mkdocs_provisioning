=================================================
Sphinxという選択肢
=================================================

Sphinxとは
=================================================

| もともとPythonのドキュメントを作るために開発されたツール。
| 出力形式はHTML,PDFなどが扱える。
|

reStructuredText（reSt）
=================================================

| Sphinxで利用されるマークアップ言語。
| Markdownのように段落や表を作るのが簡単にできる。
| 基本的な例を示す。
|

表の作成
-------------------------------------------------

| 表の作成方法がいくつかあるので、
| それぞれ紹介。
|

表の作り方１
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    ======= ====== ======
    col1    col2   col3
    ======= ====== ======
    row1    a      b
    row2    a      b
    row3    a      b
    ======= ====== ======

======= ====== ======
col1    col2   col3
======= ====== ======
row1    a      b
row2    a      b
row3    a      b
======= ====== ======

.. warning::

    日本語で作る時、=の数に注意。どうやらbyte数の分だけ必要

表の作り方2
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    +--------+-------+-------+
    | col1   | col2  | col3  |
    +========+=======+=======+
    | row1   | a     | b     |
    +--------+-------+-------+
    | row2   | a     | b     |
    +--------+-------+-------+
    | row3   | a     | b     |
    +--------+-------+-------+

+--------+-------+-------+
| col1   | col2  | col3  |
+========+=======+=======+
| row1   | a     | b     |
+--------+-------+-------+
| row2   | a     | b     |
+--------+-------+-------+
| row3   | a     | b     |
+--------+-------+-------+

.. warning::

    日本語で作る時、-,=の数に注意。どうやらbyte数の分だけ必要


表の作り方3 (CSV-table)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. csv-table:: TABLE
        :header: "col1", "col2", "col3"
        :widths: 15, 10, 30

        "row1", 1, "b"
        "row2", 2, "b"
        "row3", 3, "b"

.. csv-table:: TABLE
    :header: "col1", "col2", "col3"
    :widths: 15, 10, 30

    "row1", 1, "b"
    "row2", 2, "b"
    "row3", 3, "b"

|

.. code-block:: rst

    .. csv-table:: 外部ファイル読み込みサンプル
       :file: ../data/sample.csv
       :encoding: utf-8
       :header-rows: 1
       :widths: 15, 10, 30

.. csv-table:: 外部ファイル読み込みサンプル
   :file: ../data/sample.csv
   :encoding: utf-8
   :header-rows: 1
   :widths: 15, 10, 30

表の作り方4 (list-table)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: rst

    .. list-table:: TABLE
        :header-rows: 1

        * - col1
          - col2
          - col3
        * - row1
          - 1
          - b
        * - row2
          - 2
          - b
        * - row3
          - 3
          - b

.. list-table:: TABLE
    :header-rows: 1

    * - col1
      - col2
      - col3
    * - row1
      - 1
      - b
    * - row2
      - 2
      - b
    * - row3
      - 3
      - b

.. note::

    日本語でも問題ない。けど、正直見づらい

画像を挿入する
-------------------------------------------------

.. code-block:: rst

    .. figure:: ../img/ham.png
       :alt: ham

       キャプション：フリー素材


.. figure:: ../img/ham.png
   :alt: ham

   キャプション：フリー素材


.. code-block:: rst

    .. |emoji| image:: ../img/ham.png
              :scale: 20%

    ロゴとか絵文字化することも出来る |emoji| どや

.. |emoji| image:: ../img/ham.png
          :scale: 20%

ロゴとか絵文字化することも出来る |emoji| どや


ラベルと参照
-------------------------------------------------

.. code-block:: none

      .. _label:

      タイトル
      -------------------------------------------------
      文章

      :ref:`label` を参照


.. _label:

タイトル
-------------------------------------------------

文章

:ref:`label` を参照


他のドキュメントへの参照
-------------------------------------------------

.. code-block:: rst

    :doc:`include`

:doc:`include`


定義の参照
-------------------------------------------------

.. code-block:: rst

      .. include:: definition.txt

      てすと |hoge| ほげ

.. include:: definition.txt

てすと |hoge| ほげ


インストールしてみよう
=================================================

| Pythonさえあればインストール可能。
| CentOS7.x上にSphinxを入れる手順を示す。
|

Python2.7
-------------------------------------------------

| CentOS7なら基本的にはPythonが入っているはず。
| `virtualenvwrapper` を入れておくと、環境の切り替えが楽になるので入れる。
|

1. pipを入れる

    .. code-block:: bash

      wget https://bootstrap.pypa.io/get-pip.py
      sudo python get-pip.py

#. `virtualenvwrapper` を入れる

    .. code-block:: bash

      sudo pip install virtualenvwrapper

#. PATHを通す

    .. code-block:: bash

      vi ~/.bash_profile

    .. code-block:: bash

      ### add s
      ### Virtualenvwrapper
      if [ -f /usr/bin/virtualenvwrapper.sh ]; then
          export WORKON_HOME=$HOME/.virtualenvs
          source /usr/bin/virtualenvwrapper.sh
      fi
      ### add e

    .. code-block:: bash

      source ~/.bash_profile

Sphinxを入れる
-------------------------------------------------

| virtualenvで用意した環境にSphinxを入れる
|

1. `sphinx` という名前でvirtualenvを作成

    .. code-block:: bash

      mkvirtualenv --python=/usr/bin/python2.7 sphinx

#. pipでSphinxのインストール

    .. code-block:: bash

      pip install sphinx

PDF出力用の環境を作る
------------------------------------------------

1. Tex liveのインストール

    .. code-block:: bash

      wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
      tar xzvf install-tl-unx.tar.gz
      cd install-tl-20171005/
      sudo ./install-tl
      Loading http://ftp.jaist.ac.jp/pub/CTAN/systems/texlive/tlnet/tlpkg/texlive.tlpdb
      Installing TeX Live 2017 from: http://ftp.jaist.ac.jp/pub/CTAN/systems/texlive/tlnet (verified)
      Platform: x86_64-linux => 'GNU/Linux on x86_64'
      Distribution: net  (downloading)
      Using URL: http://ftp.jaist.ac.jp/pub/CTAN/systems/texlive/tlnet
      Directory for temporary files: /tmp/2xZStj58ZI

      ======================> TeX Live installation procedure <=====================

      ======>   Letters/digits in <angle brackets> indicate   <=======
      ======>   menu items for actions or customizations      <=======

       Detected platform: GNU/Linux on x86_64

       <B> set binary platforms: 1 out of 19

       <S> set installation scheme: scheme-full

       <C> set installation collections:
           40 collections out of 41, disk space required: 5068 MB

       <D> set directories:
         TEXDIR (the main TeX directory):
           /usr/local/texlive/2017
         TEXMFLOCAL (directory for site-wide local files):
           /usr/local/texlive/texmf-local
         TEXMFSYSVAR (directory for variable and automatically generated data):
           /usr/local/texlive/2017/texmf-var
         TEXMFSYSCONFIG (directory for local config):
           /usr/local/texlive/2017/texmf-config
         TEXMFVAR (personal directory for variable and automatically generated data):
           ~/.texlive2017/texmf-var
         TEXMFCONFIG (personal directory for local config):
           ~/.texlive2017/texmf-config
         TEXMFHOME (directory for user-specific files):
           ~/texmf

       <O> options:
         [ ] use letter size instead of A4 by default
         [X] allow execution of restricted list of programs via \write18
         [X] create all format files
         [X] install macro/font doc tree
         [X] install macro/font source tree
         [ ] create symlinks to standard directories

       <V> set up for portable installation

      Actions:
       <I> start installation to hard disk
       <P> save installation profile to 'texlive.profile' and exit
       <H> help
       <Q> quit

      Enter command: I <---Iを入力してEnter

      ＜略 3501のパッケージが入る＞


#. PATHの追加

    | latexを入れた時に以下のようなメッセージが出るので、
    | `.bashrc` などに追記する

    .. code-block:: bash

      Add /usr/local/texlive/2017/texmf-dist/doc/man to MANPATH.
      Add /usr/local/texlive/2017/texmf-dist/doc/info to INFOPATH.
      Most importantly, add /usr/local/texlive/2017/bin/x86_64-linux
      to your PATH for current and future sessions.

    .. code-block:: bash

      MANPATH=$MANPATH:/usr/local/texlive/2017/texmf-dist/doc/man
      INFOPATH=$INFOPATH:/usr/local/texlive/2017/texmf-dist/doc/info
      PATH=$PATH:/usr/local/texlive/2017/bin/x86_64-linux

#. 追記後、 `source` コマンドで読み込み

    .. code-block:: bash

      source ~/.bashrc

#. PDF出力する

    .. code-block:: bash

      make latexpdf

実際に使ってみる
-------------------------------------------------

**デモ**
