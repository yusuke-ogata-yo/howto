# How To set SSH

## SSH キーの生成

```bash
ssh-keygen -t ed25519 -P "" -f serial-server.pem
```

- ssh-keygen オプション
  - -t : 鍵のタイプ。ed25519、rsa
  - -P : パスフレーズ。""（空）にするとパスフレーズなし
  - -f : 秘密鍵、公開鍵のファイル名
  - -C : コメント

## 鍵の配置

```bash
ssh-copy-id -i publicKeyName userName@xxx.xxx.xxx.xxx
```

- `~/.ssh/authorized_keys` に鍵がコピーされる

## パーミッションの設定

```bash
chmod 600 authorized_keys
chmod 700 .ssh
# chown root:root my_sshd_confg.conf
```

- `authorized_keys` は `600`
- `~/.ssh` は `700`

## OpenSSH のコンフィグ設定

```bash
sudo vim /etc/ssh/sshd_config
```

```bash
# プロトコルバージョン
Protocol 2
# パスワード認証
PasswordAuthentication no
# チャレンジレスポンス認証
ChallengeResponseAuthentication no
# 空のパスワードの認証
PermitEmptyPasswords no
# ルートのログイン
PermitRootLogin no
# ログレベル
SyslogFacility AUTHPRIV
LogLevel VERBOSE
# ポート
Port 10022
```

## ユーザの追加

```bash
useradd -m username
passwd username
```

- `useradd -m` にて、ユーザフォルダも作成する

```bash
# su - username した状態で
useradd -G wheel
# もしくは
#sudo visudo
```

- `whell` グループに入れてあげると `sudo` ができる



```bash
username ALL=(ALL) ALL
```

## SSH 接続先の登録

```bash
vim ~/.ssh/config
```

```
Host vRaspi001
  HostName 20.0.10.10
  Port 10022
  User username
  IdentityFile ~/.ssh/vRaspi001
```