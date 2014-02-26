Git簡易マニュアル
==============

Gitのインストール
---------------------

以下の記事を参考にインストールして下さい。（Windows、UNIX/Linux、Mac OS それぞれのインストール方法があります。）

https://github.com/masaru-b-cl/niigata-scm/wiki/Gitのインストール方法

Gitの初期設定
-----------------

※Windowsの場合は、Git Bashを起動してください

### 初期設定
コミットログに残す<ユーザ名>と<メールアドレス>を設定します。
```
$ git config --global user.name "<ユーザ名>"
$ git config --global user.email "<メールアドレス>"
```

#### ※[今回の実習では、設定不要です] paroxy設定（必要な場合）
```
$ git config --global http.proxy http://proxyname:8080
$ git config --global https.proxy http://proxyname:8080
```

※なお、これらはすべて~/.gitconfigに以下のように反映されます。
```
[user]
	name = <ユーザ名>
	email = <メールアドレス>
[http]
	proxy = http://proxyname:8080
[https]
	proxy = http://proxyname:8080
```

---

Gitの操作
------------

#### 1. GitHubにインターンシップ用ディレクトリXXXを作成する
#### 2. コンソールで、ディレクトリXXXへ移動する
```
mkdir XXX
cd XXX
```
#### 3. [一度だけ実施] 作業ディレクトリを初期化する。
* 以下のコマンドを実行すると、カレントディレクトリ（今の場合、XXX）が、Gitの`作業ディレクトリ`として初期化されます。同時に、Gitの`ローカルリポジトリ`も作成されます。
```
$ git init
```
#### 4. 実習作業を行う（ファイルの追加・更新etc）

#### 5. 変更内容を、Gitの`ローカルリポジトリ`へコミットする
* (1).コミット準備として、以下の操作を行う
```
$ git add .
```
※この操作により、Gitの`インデックス`領域に、コミットすべきファイルが追加されます。
* (2).以下の操作により、`ローカルリポジトリ`へコミットを行う
```
$ git commit -m "コミットメッセージ"
```
※この操作で、インデックスの内容が`ローカルリポジトリ`へコミットされる
#### 6. コミットした内容を、GitHubへpushする
* [一度だけ実施]GitHubに、管理用リポジトリを作成しておく
* [一度だけ実施]GitHubのリポジトリに、ローカルでの別名をつけておく（originという別名をつけておく）。
```
$ git remote add origin https://github.com/<GitHubのアカウント名>/<作成した管理用リポジトリ名>.git
```
* コミットした内容を、GitHubへpushする。以下のコマンドを実行する。その際、GitHubのアカウント名とパスワードを尋ねられるので、入力する。
```
$ git push origin master
```
以下、その時のログ
```
git: 'credential-cache' is not a git command. See 'git --help'.
Username for 'https://github.com': <GitHubのアカウント名>
Password for 'https://<GitHubのアカウント名>@github.com':<パスワード>
git: 'credential-cache' is not a git command. See 'git --help'.
Counting objects: 11, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (8/8), 636 bytes | 0 bytes/s, done.
Total 8 (delta 0), reused 0 (delta 0)
To https://github.com/<GitHubのアカウント名>/<作成した管理用リポジトリ名>
   1e41106..75b07ff  master -> master
```
* [push時のパスワード入力を省略したい場合] 以下のコマンドを実行すると、指定した時間（秒）の間、一度入力したアカウント名/パスワードがメモリ中に保存されるので便利。
```
$ git config --global credential.helper cache --timeout=3600
```

以上、4～5を繰り返して開発を進め、タイミングをみて6を実施してださい。

ご参考
------

* [git - 簡単ガイド](http://rogerdudler.github.io/git-guide/index.ja.html) - http://rogerdudler.github.io/git-guide/index.ja.html
* [Gitを使いこなすための20のコマンド](http://sourceforge.jp/magazine/09/03/16/0831212) - http://sourceforge.jp/magazine/09/03/16/0831212
