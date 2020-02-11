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
