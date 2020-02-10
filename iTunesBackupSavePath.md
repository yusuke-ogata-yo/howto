管理権限付きで、PowerShellを起動
cmd で

```
mklink /J “%APPDATA%\Apple Computer\MobileSync\Backup” “E:\Backup”
```

AWSの鍵置き場へのリンクをはりたい
```
mklink /J “E:\privateKey” “\\ASBCREATE_NAS01\home\Drive\yusuke\web\privateKey”
```

gitBash を日本語化
https://kekaku.addisteria.com/wp/20190422023230