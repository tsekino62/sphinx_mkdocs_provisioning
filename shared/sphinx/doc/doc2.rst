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

実際に使ってみる
-------------------------------------------------

**デモ**
