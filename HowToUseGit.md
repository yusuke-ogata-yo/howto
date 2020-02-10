# vsCodeでのgit設定

拡張機能：Git History を入れるとグラフィカルにできる

ctrl+@ でコマンドでも実施可能

#### 参考サイト

[VSCodeでのGitの基本操作まとめ](https://qiita.com/y-tsutsu/items/2ba96b16b220fb5913be)

[いまさらGit for Windowsのインストール、GitHubに接続してみた。](https://qiita.com/manabu-watanabe/items/ecf1b434baf305adaa00)

# githubのsshでのアクセス先

git@github.com:yusuke-ogata-yo/sample.git



# 公開鍵の生成、登録

#### 参考サイト

[いまさらGit for Windowsのインストール、GitHubに接続してみた。](https://qiita.com/manabu-watanabe/items/ecf1b434baf305adaa00)

## 公開鍵の生成

GitHubへ接続するために公開鍵を作成します。
GitBashをスタートメニューから選択し起動します。
下記のコマンドを実行します。


```bash
$ ssh-keygen -t rsa -b 4096 -C [コメント]
```

実行すると、作成する公開鍵と秘密鍵のディレクトリおよびファイル名の確認されます。
ディレクトリとファイル名がそのままでよければそのままEnterを押してください。


```bash
$ ssh-keygen -t rsa -b 4096 -C [コメント]
Generating public/private rsa key pair.
Enter file in which to save the key (/c/home/.ssh/id_rsa):
```

パスフレーズを設定します。設定しなくてもEnter進めますが、設定しておいたほうが良いでしょう。


```bash
Created directory '/c/home/.ssh'.
Enter passphrase (empty for no passphrase):
```

確認の為にもう一度入力を求められるので、同じパスフレーズを入力します。


```bash
Enter same passphrase again:
Your identification has been saved in /c/home/.ssh/id_rsa.
Your public key has been saved in /c/home/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:A/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx [コメント]
The key's randomart image is:
+---[RSA 4096]----+
|=o*..  o..o.     |
|.+o=     +.      |
|  o.  o.+. .     |
| .o  o o. = .    |
|      ..S. + .   |
| o   o..o.  .    |
|  o    o .       |
|. +.o o .        |
|.o+*.+           |
+----[SHA256]-----+
```

パスフレーズを入力すると、公開鍵と秘密鍵が作成されます。
何も変更しなかった場合は、コマンドを実行した直下に.sshディレクトリが作成され、下記の2ファイルが作成されます。

- id_rsa : 秘密鍵
- id_rsa.pub : 公開鍵

**秘密鍵の名前は"id_rsa"でなければならない**


## githubへの公開鍵の登録

先程作成した公開鍵を登録します。

1. 画面の右上にあるアイコンをクリックします。
2. メニューが表示されるので、「Settings」を選択します。
3. 「Public profile」画面が表示されますので、左側のメニューから「SSH and GPG keys」を選択します。
4. 「SSH keys / Add new」画面が表示されますので、必要な情報を入力し、「Add SSH Key」ボタンを押下します。
   - Title:登録するSSHのPCが特定できる名前が良いと思います。
   - Key:先程作成した公開鍵の中身を貼り付けます。(c:\home.ssh\id_rsa.pub)

# gitの操作

## 簡単操作
```bash
echo "# Javascript-train.omikuji.sample" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:yusuke-ogata-yo/Javascript-train.omikuji.sample.git
git push -u origin master
```

git init は、そのディレクトリに".git"を作成しレポジトリを作る操作。git clone をする場合は不要。

#### 参考サイト

dotinstall.com  
[github](https://github.com/yusuke-ogata-yo/Javascript-train.omikuji.sample)


## #04. gitの設定

- git config --global user.name "(your name)"
- git config --global user.email "(your email)"
- git config --global color.ui true
- git config -l
  - 設定の表示。 git config --list とすると全部表示
- git config --unset color.ui
  - 設定を削除する
- git config --help
- git help config



## #05. gitの初期化、ステージング、コミット

- git init
- git add
- git reset [file name]
  - ステージングの取り消し
- git commit
- git log
- git commit -am"コミット内容"
  - add と commit を同時に実行する



## #06. コミットしたあとの履歴確認

- git log --oneline
- git log -p
- git log --stat

## #07. ファイルの状態表示

- git status

## #08. 変更箇所の確認git diff

- git diff
- git diff --cached
  - ステージングエリアでの確認

## #09. git addする際に使える便利なオプション、ファイルを削除・移動する際のコマンド

- git add .
  - フォルダ配下のファイルをすべてadd する
- git rm / git mv
  - git 配下にあるファイルの削除や移動時



## #10. コミットメッセージをエディタを立ち上げずに書く方法、直前のコミットを変更する方法

- git commit -m "(message)"
- git commit --amend



## #11. コミットのログを見ながら、任意のバージョンに戻す

- git reset --hard HEAD
- git reset --hard HEAD^



## #12. git resetしたあとにそれを取り消し

- git reset --hard ORIG_HEAD



## #13. 複数バージョンの開発を進めていくのに便利なブランチ

- git branch
- git branch (branch name)
- git checkout (branch name)
- git checkout -b (branch name)
  - ブランチを作って移動



## #14. ブランチのマージ、ブランチを削除

- git merge (branch name)
  - マージしたい元ブランチ(masterとか)に移動してから、git margeすること！
- git branch -d (branch name)



### 補足１：git stash

業途中でマージしようとすると、マージによって現在の変更内容が上書きされてしまう場合に、次のようなエラーメッセージが表示されます。

```bash
Please, commit your changes or stash them before you can merge.
```



この場合、先にコミットもしくは「stash」を行なわなければなりません。「git stash」を使うと、一時的に変更内容を退避させることができます。「まだ作業途中なのでコミットしたくない」という場合にこの stash が使えます。

```bash
git stash save
```



わかりやすいコメントをつけて保存することもできます。

```bash
git stash save "コメント"
```



退避した情報は「git stash list」で一覧表示できます。

```bash
git stash list
```

stash するたびに、この一覧の「上」に退避データが積み上がっていきます。

退避した内容は「git stash pop」で取り出すことができます。

```bash
git stash pop
```


引数をつけない場合、list で表示した一番上の内容が取り出されます。



### 補足２：マージ済みのブランチ一覧を確認する方法

masterにマージ済みのbranchの一覧を見るには、masterに切り替えた状態で「git branch --merged」というコマンドを実行します。

```bash
$ git checkout master
$ git branch --merged
```


逆に、まだmasterにマージしていないbranchの一覧を見るには「git branch --no-merged」を使います。

```bash
$ git checkout master
$ git branch --no-merged
```



## #16. コンフリクトの解消
コンフリクトした箇所が下記のように表示されるので、採用したいもののみ残してコミットすればよい。

```bash
>>>>>>>>>>>>>>>HEAD
1番目
===============
1st
<<<<<<<<<<<<<<<foo
```



## #17. 任意のコミットにわかりやすい名前をつけることができるタグ

- git tag
- git tag (tag name)
- git tag (tag name) (commit id)
- git tag -d (tag name)
- git show
  - commit の内容を確認するコマンド



## #18. gitのコマンドに短縮名（エイリアス）をつける

- git config --global alias.co checkout
- git config --global alias.st status
- git config --global alias.br branch
- git config --global alias.ci commit
- git config -l



## #19. 複数人で共同作業をするために、共有リポジトリを設定

- git init --bare
  - 共同開発用には --bare オプションを付けて初期化する



## #20. コミットを共有リポジトリに反映させる方法について説明していきます。

- git remote add origin (repos location)
- git remote rm 
- git push origin master


リモートにあるオリジナルの場所は git config -l で確認できる
```bash
remote.origin.url=git@github.com:yusuke-ogata-yo/sample.git
```



## 共有リポジトリを介して複数ユーザーがその内容を共有していくための流れ

- git clone
- git push
- git pull



## コメントを修正したい場合

#### 直前のコメントの修正

- git commit --amend

#### 1つ以上前のコメントの修正

1. git rebase -i HEAD~3
2. edit マークを付ける
3. git commit --amend
4. エディタでコメントを修正
5. git rebase --continue

これまでのコミットを表示する

```bash
> git log --oneline

fbd8994 (HEAD -> master) finish firstJS #04
fd36125 finish firstJS #03
d197b83 test commit
ae413a9 git pull repository
adca13f Initial commit
```

上かrあ3行目のコミットのコメントを変更
```bash
> git rebase -i HEAD~3
```
エディタが立ち上がるので、編集したいコミットの行の先頭に「edit」を付けて画面を閉じる
```bash
edit d197b83 test commit.
pick fd36125 finish firstJS #03
pick fbd8994 finish firstJS #04

# Rebase ae413a9..fbd8994 onto ae413a9 (3 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

編集を行う。
```bash
> git commit --amend
```

編集が終えると、HEADの位置が、編集したコミットの位置になっているので、最新のコミットまでHEADを戻す。
```bash
> git rebase --continue
```



