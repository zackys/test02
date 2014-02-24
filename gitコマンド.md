Gitのインストール
=============

http://git-scm.com/

よりインストーラをダウンロードして、実行

Gitの実行（Windows）
================

Git Bash起動

初期設定
```
$ git config --global user.name "<ユーザ名>"
$ git config --global user.email "<メールアドレス>"
```

proxy設定（必要な場合）
```
$ git config --global http.proxy http://tisproxy.tis.co.jp:8080
$ git config --global https.proxy http://tisproxy.tis.co.jp:8080
```

※これらはすべて~/.gitconfigに反映される
```
[user]
	name = zacky-san
	email = miyazaki.toshiro@tis.co.jp
[http]
	proxy = http://tisproxy.tis.co.jp:8080
[https]
	proxy = http://tisproxy.tis.co.jp:8080
[credential]
	helper = cache
```

1. GitHubにインターンシップ用ディレクトリXXXを作成する
2. コンソールで、作業ディレクトリへ移動する
```
mkdir XXX
cd XXX
```
3. 作業ディレクトリを初期化する
```
$ git init
```
4. 実習作業を行う
5. 変更内容を、commitする
```
$ git add <ファイル名>
```
```
$ git add *
```
    * これらのコマンドにより、commitしたい変更がインデックスへ登録される
6. インデックスの内容を、commitする
```
$ git commit -m "コミットメッセージ"
```
7. コミットした内容を、GitHubへpushする
一度だけ
```
$ git remote add origin https://github.com/zacky-san/test02.git
```
```
$ git push origin master
git: 'credential-cache' is not a git command. See 'git --help'.
Username for 'https://github.com': zacky-san
Password for 'https://zacky-san@github.com':
git: 'credential-cache' is not a git command. See 'git --help'.
Counting objects: 11, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (8/8), 636 bytes | 0 bytes/s, done.
Total 8 (delta 0), reused 0 (delta 0)
To https://github.com/zacky-san/test02
   1e41106..75b07ff  master -> master
```

パスワードを保存する
```
$ git config --global credential.helper cache --timeout=3600
$ git config --global credential.helper cache
```
