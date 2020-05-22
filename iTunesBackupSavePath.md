# How to change iTunes backup folder

1. Start powershell with administrator privileges.
2. Input ```cmd``` to have internal command in command prompt with administrator privileges.
3. Input following command in the terminal.

- mklink /J [src] [dst]

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

Dev folder 
```bash
mklink /j "F:\OneDrive\Documents\Dev" "F:\share\Dev"
mklink /j "F:\OneDrive\Documents\HW" "F:\share\HW"
mklink /j "F:\OneDrive\Documents\homeFiles" "F:\share\homeFiles"
```

## attention

- there is no folder [src]
- jancktion is made at [src]

gitBash を日本語化
https://kekaku.addisteria.com/wp/20190422023230