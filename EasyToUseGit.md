# gitの簡単操作
とりあえずgitを使ってみるための操作集。

# 使い始める時
## リポジトリを新規作成の場合
```bash
echo "# Javascript-train.omikuji.sample" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:yusuke-ogata-yo/Javascript-train.omikuji.sample.git
git push -u origin master
```

git init は、そのディレクトリに".git"を作成しレポジトリを作る操作。git clone をする場合は不要。

## クローンする場合
```bash
git clone git@github.com:yusuke-ogata-yo/Javascript-train.omikuji.sample.git
```
git clone を実施したディレクトリに、「Javascript-train.omikuji.sample」というディレクトリが作成され、ファイルが配置される

# リポジトリへのアップ、ダウン
## リポジトリにアップするとき
```bash
git push origin master
```

## リポジトリを手元にコピーするとき
```bash
git pull origin master
```

# ブランチの利用
## ブランチの確認
```bash
git branch
```
## ブランチの作成
```bash
git branch xxx
```
## ブランチの切り替え
```bash
git checkout xxx
```

ブランチに対して、add や commit を行える

## ブランチのpush
```bash
git push -u origin xxx
```
初めてブランチをpushするときは、-u オプションを使うとよい。
使わないと、リモートリポジトリにブランチがないため以下のエラーが出た。
```bash
error: src refspec xxx does not match any
```

現在のブランチ(HEADの場合)へ簡単にpushする方法
```bash
git push origin HEAD
```

# add の取り消し
```bash
git checkout .
```

# ステージングの取り消し
```bash
git reset [fileName]
```

# 編集内容を破棄してステージングの取り消し
```bash
git reset --hard HEAD
```

コミットのバージョンを戻す
```bash
git reset --hard [commit id]
```

# git のトラブルシューティング

## git commit 時のエラーの対応
### error: xxxx
[事象]コミットメッセージが保存できずに、コミットが失敗
[原因]エディタの内容が保存され閉じられる前に、git commit コマンドが終了してしまうことが原因。
[対処]エディタの指定と共に、--wait オプションを指定し、エディタの応答をコマンドが待つように設定する。
### gitのエディターを指定方法
```bash
git config --global core.editer "vim --wait" // vimを指定
```
```bash
git config --global core.editer "code --wait" // vscodeを指定
```

#### 参考サイト

dotinstall.com  
[github](https://github.com/yusuke-ogata-yo/Javascript-train.omikuji.sample)  
[git を初めて使う時 コミット→プッシュ→マージ　の流れ](https://qiita.com/yukiyoshimura/items/7aa4a8f8db493ab97c2b)

