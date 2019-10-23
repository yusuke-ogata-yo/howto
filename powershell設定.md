# PowerShell 設定

## 1. viの導入
#### 参考サイト
[Powershellでvimを使う](https://qiita.com/shuhoyo/items/d9966e12976275f20c24)

### 1.1 vim のインストール
リンク：[vim the editor](https://www.vim.org/download.php)

### 1.2 エイリアスコマンドの作成
#### 1.2.1 Powershellスクリプトファイルの実行権限の有無の確認
```bash
PS C:\Users\yusuk> get-executionpolicy
RemoteSigned
```
- `Restricted` ：スクリプトが無効な状態。以下を実施。
- `RemoteSingned`：スクリプトが有効な状態。
```bash
> set-executionpolicy remotesigned
```
#### 1.2.2 Powershellのプロファイルへパスが通っているか確認
```bash
PS C:\Users\yusuk> $profile
C:\Users\yusuk\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
```
存在していない意場合は、上記パスに `Microsoft.PowerShell_profile.ps1` ファイルを作成。

#### 1.2.3 viのエイリアスを設定
```bash
set-alias vi 'C:\Program Files (x86)\Vim\Vim81\vim.exe'
````

### 1.4 行番号の表示
```bash
PS C:\Users\yusuk> vi ~/.vimrc 
```
`.vimrc` に以下を追加
```bash
set number
```

### 1.5 profile
[powershell-profile.txt](./powershell-profile.txt)


## 2. ログを残す設定
### 2.1 ログ収集コマンド
- ログ収集開始：`Start-Transcript <ファイル名> -append`
- ログ収集停止：`Stop-Transcript <ファイル名>`



### 2.2 ログ収集自動化
ターミナルを立ち上げたら自動でログ収集するようにプロファイルに設定。
- プロファイルにパスが通っているか確認
- パスが通っていない場合、プロファイルにパスを通す
```bash
PS C:\WINDOWS\System32> Test-Path $profile
False

PS C:\WINDOWS\System32> New-Item -path $profile -type file -force

    Directory: C:\Users\yusuk\Documents\PowerShell

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2019/09/29    20:11              0 Microsoft.PowerShell_profile.ps1

PS C:\WINDOWS\System32> Test-Path $profile
True
```

powershell起動時に自動でターミナルログを取得するコマンドを記載する。
```bash
PS C:\Users\yusuk> vi $profile
```
以下の内容を記載する。
- 1行目：vi のエイリアス設定
- 3行目～6行目：`yyyy-MM-dd-HHmmss.log` というファイル名でログを出力

```bash
 1 set-alias vi 'C:\Program Files (x86)\Vim\Vim81\vim.exe
 2
 3 $Now = Get-Date
 4 $logPath = "E:\powershellLog\"
 5 $logfileName = $logPath + $Now.ToString("yyyy-MM-dd-HHmmss") + ".log"
 6 Start-Transcript $logfileName
 ```
