============
Githubの利用
============

アカウントの作成
================

1. https://github.com にアクセスします。

  |github-001|

2. 画面中央にある"Plans, Pricing and Signup"をクリックします。

  |github-002|

3. 画面右上にある"Create a free account"をクリックします。

  |github-003|

4. 入力フォームに必要な情報を入力します。

5. 以上でGithubのアカウンの作成は完了です。

.. |github-001| image:: img/github/001.png
.. |github-002| image:: img/github/002.png
.. |github-003| image:: img/github/003.png

Githubアカウントの設定
======================

先ほど作成したアカウント情報をgitに設定します。

ユーザ名
--------

  ::

    git config --global user.name "ユーザネーム"

メールアドレス
--------------

  ::

    git config --global user.email "メールアドレス"

.. note::

  ここで指定するメールアドレスは正しいメールアドレスである必要はありません。
  もし公開したくない場合は"someone@gmail"のように設定すると良いでしょう。

以上でGithubアカウントのGitに対する設定は完了です。

パスワードのキャッシュ
----------------------

.. warning::

  この設定はgitのバージョンが1.7.10以降の場合のみ利用可能です。
  Gitのバージョンを確認するには以下のコマンドを実行します。

  ::

    git --version

パスワードのキャッシュ機能を利用するには以下のコマンドを実行します。

::

  git config --global credential.helper cache

デフォルトでは15分の間1度入力したパスワードをキャッシュしてくれます。
この設定を変更したい場合は以下のコマンドを実行します。

::

  git config --global credential.helper 'cache --timeout=3600'

時間の単位は秒で指定するので上記の例では1時間パスワードをキャッシュしてくれるようになります。

.. note::

  パスワードのキャッシュ機能については Githubのヘルプ_ にプラットフォーム毎の
  設定が詳しく書かれています。英語で書かれていますが、興味ある方はそちらも合わせて
  確認してみると良いでしょう。

以上でGithubアカウントの設定は完了です。

.. _Githubのヘルプ: https://help.github.com/articles/set-up-git
