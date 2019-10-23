# Vagrantによるローカル環境設定

## 1. 基本的な操作
### 1.1 簡単な使い方
1. 仮想マシンを動作させるフォルダを作成する
2. `vagrant init [box name]` にて、`Vagrantfile` を生成
3. `Vagrantfile` を編集
4. `vagrant up` にて、仮想マシン立ち上げ
5. `vagrat status` にてvmの起動状態確認
6. `vagrant ssh` にてssh接続
7. `vagratnt resum` にてmv再起動
8. `vagrant halt` にてvm停止
9. `vagrant destroy` にてvm削除

### 1.2 box ファイルのDL、登録
コマンド
```bash
vagrant box add [box name] [url]
```
登録されたか確認
```bash
vagrant box list
```
box の削除
```bash
vagrant box remove [box name]
```
box が配置されている場所  
`C:\Users\yusuk\.vagrant.d\boxes`

## 2. Vagrantfile の編集
vagrantfile


## 3. box を作る
### 3.1 box 作成準
1. vmがあるディレクトリに移動
2. boxの作成：`vagrant package`
3. boxの登録：`vagrant box add [box name] package.box`
4. package.boxの削除：`rm package.box`

### 3.2 新たなboxを使ったvmの起動
1. ディレクトリ作成
2. 初期化：`vagrant init [box name]`
3. 起動：`vagrant up`

### 3.3 virtualbox ファイルを vagrantfile に変換
コマンド
```bash
vagrant package --base [virtulabox file name] --output [vagrant box name]
```
例
```bash
vagrant package --base "CentOS 6.6" --output "CentOS 6.6.box"
```
`--base`：VirtualBox上に表示されている登録名  
`--output`：出力ファイル名

実行例
```bash
PS E:\VMImages\VirtualBox VMs\開発環境> ls                                                                              

    Directory: E:\VMImages\VirtualBox VMs\開発環境

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2019/01/24     6:54                centos-7 dokuwiki
d-----        2018/09/02    21:42                centos-7-GNOME dev
d-----        2018/09/02    21:24                centos-7-GNOME redmine

PS E:\VMImages\VirtualBox VMs\開発環境> vagrant package --base "centos-7 dokuwiki" --output "centos-7-dokuwiki.box"     ==> centos-7 dokuwiki: Clearing any previously set forwarded ports...
==> centos-7 dokuwiki: Exporting VM...
==> centos-7 dokuwiki: Compressing package to: E:/VMImages/VirtualBox VMs/開発環境/centos-7-dokuwiki.box
PS E:\VMImages\VirtualBox VMs\開発環境> ls                                                                              

    Directory: E:\VMImages\VirtualBox VMs\開発環境

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2019/10/03    11:47                centos-7 dokuwiki
d-----        2018/09/02    21:42                centos-7-GNOME dev
d-----        2018/09/02    21:24                centos-7-GNOME redmine
-a----        2019/10/03    12:45     2825390995 centos-7-dokuwiki.box
```
