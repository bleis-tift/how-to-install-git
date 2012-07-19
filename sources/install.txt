=================
Gitのインストール
=================

Windows
=======

Windowsでは、CygwinにGitを導入する方法と、msysgitを導入する方法の2通りの方法があります。

今回はお手軽かつ高速なmsysgitを導入します。

msysgitの場合、msysgit本体だけではうまく日本語が扱えないので、nkfというプログラムの導入も行う必要があります。

msysgitのインストール
---------------------

1. msysgitのサイト_ に移動し、Git-1.7.6-preview201107xx.exeと書かれたリンクを選択します。

   |win-001|

2. ダウンロード用のリンクを選択し、インストーラをダウンロードします。

   |win-002|

3. ダウンロードしてきたファイルを実行します。

   |win-003|

4. ライセンスが表示されます。

   |win-004|

5. インストール場所は、特にこだわりがなければそのままにしておきます。
   32bit版の場合、(x86)は付かないので注意してください。

   |win-005|

6. インストールの設定です。
   デスクトップにショートカットがあっても邪魔なだけなので、外しておきます。

   Git Bash Hereがあった方が何かと便利なので、Windows Explorer integrationは
   「Context menu entries」がいいでしょう。

   Git GUI HereはGit Bash Hereから起動できるので、ここではチェックを入れていません。

   |win-006|

7. スタートメニューに登録する名前です。

   |win-007|

8. PATHにgitの実行ファイルが格納されたbinを使いするかどうかです。
   基本的にはGit Bash Hereを使うことになるので、ここではデフォルトのままにしておきます。

   |win-008|

9. 改行文字の変換の設定です。
   後で変更可能なのでどれでもいいのですが、プアなエディタを使っているのでなければ、
   一番下の「何も変換しない」設定がおすすめです。

   |win-009|

10. しばらくお待ちください。

   |win-010|

11. msysgitのインストールは終了です。

   |win-011|

.. _msysgitのサイト: http://code.google.com/p/msysgit/
.. |win-001| image:: img/win/001.png
.. |win-002| image:: img/win/002.png
.. |win-003| image:: img/win/003.png
.. |win-004| image:: img/win/004.png
.. |win-005| image:: img/win/005.png
.. |win-006| image:: img/win/006.png
.. |win-007| image:: img/win/007.png
.. |win-008| image:: img/win/008.png
.. |win-009| image:: img/win/009.png
.. |win-010| image:: img/win/010.png
.. |win-011| image:: img/win/011.png

nkfのインストール
-----------------------

1. nkf_ をダウンロードし、展開します。
2. binの中にあるnkf.exeを、Gitをインストールしたディレクトリのbinの中にコピーします。

.. _nkf: https://skydrive.live.com/#cid=C562DFDEB23518F0&id=C562DFDEB23518F0%21376

日本語入力と日本語出力の準備
----------------------------

Windowsでは、Gitのインストールディレクトリのetcの中にあるファイルを編集する必要があります。

Windows Vista/7をお使いの方は以下の手順を実行前に、
Usersグループに対してetcディレクトリに書き込み権限を与えておいてください。

1. inputrcを開き、

   ::

     # disable/enable 8bit input
     # set meta-flag on
     # set input-meta on
     # set output-meta off
     # set convert-meta on

   と書かれた場所を探します。おそらく14行目付近にあるはずです。

   これを以下のように書き換えます。

   ::

     # disable/enable 8bit input
     # set meta-flag on
     # set input-meta on
     # set output-meta off
     # set convert-meta on
     set convert-meta off
     set meta-flag on
     set output-meta on
     set kanji-code utf-8

   この修正により、日本語の入力が可能になります。
2. profileを開き、ファイルの最後に

   ::

     export GIT_PAGER="nkf -s | LESSCHARSET=utf-8 less"

   と追記します。

   この修正により、日本語の出力が可能になります。

Mac
===

MacPortsを使う場合
------------------

1. 以下のコマンドを実行します。

   ::

     sudo port install git-core

2. インストール終了です。

Homebrewを使う場合
------------------

1. 以下のコマンドを実行します。

   ::

     brew install git

2. インストール終了です。

初期設定
========

必要最小限の設定を行います。

Windowsの場合、適当なディレクトリを右クリックして、Git Bash Hereを実行します。

その他のOSの場合、bashなりzshなりを開きます。

ユーザ情報を設定
================

以下のコマンドを実行します。

::

  git config --global user.name ユーザ名
  git config --global user.email メールアドレス
  git config --global color.ui auto

エディタを設定
==============

コミットメッセージなどを入力するエディタの設定を行います。

エディタの選定基準としては、

* デフォルトのエンコーディング方式をUTF-8にできる、
  もしくは起動時にエンコーディング方式をUTF-8にできる
* 保存と終了が簡単にできる

を満たすものなら基本的には大丈夫です。

例えば、WindowsでGVimを使用する場合、Gitのインストールディレクトリのetcの中にあるprofileを開き、
ファイルの最後に以下の記述を追加します。

::

  export GIT_EDITOR='/C/Apps/vim/gvim.exe'

パスに空白が入っていると面倒なので、空白が入っていない場所に入れておくといいでしょう。

Windows以外の場合、ホームディレクトリの.bashrcなどのファイルに、上記の記述を追記します。
