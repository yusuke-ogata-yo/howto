# How to change iTunes backup folder

1. Start powershell with administrator privileges.
2. Input ```cmd``` to have internal command in command prompt with administrator privileges.
3. Input following command in the terminal.

- iTunes backup folder path
  - C:\Users\yusuk\AppData\Roaming\Apple Computer\MobileSync

```bash
cmd

mklink /J “C:\Users\yusuk\AppData\Roaming\Apple Computer\MobileSync\Backup” “F:\iTunes\MobileSync\Backup”
```

AWSの鍵置き場へのリンクをはりたい
```bash
mklink /J “E:\privateKey” “\\ASBCREATE_NAS01\home\Drive\yusuke\web\privateKey”
```

gitBash を日本語化
https://kekaku.addisteria.com/wp/20190422023230