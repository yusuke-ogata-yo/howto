# powershell にエイリアス追加

```cmd
set-alias vi 'C:\Program Files (x86)\Vim\Vim81\vim.exe'
```

# powershell のログを自動で出力
```cmd
$Now = Get-Date
$logPath = "E:\powershellLog\"
$logfileName = $logPath + $Now.ToString("yyyy-MM-dd-HHmmss") + ".log"
Start-Transcript $logfileName
```