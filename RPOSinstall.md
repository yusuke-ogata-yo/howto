# raspi のssh, camer, vnc設定
- 「メニュー」->「Raspberry PI設定」->「カメラ」、「ssh」、「vnc」を有効にする

# bluetoothの接続
- [Bluetooth on the Raspberry Pi](https://pimylifeup.com/raspberry-pi-bluetooth/)
## GUI ツールのインストール
```bash
sudo apt install bluetooth pi-bluetooth bluez blueman
sudo reboot
```
1. 右上の青いbluetooth アイコンをクリック
1. 「Devices」->新規ウィンドウが開く
1. 機器をペアリングモード「Search」を押下
1. 機器を見つけたら「右クリック」->pair, connect, trustを実施
1. preference をして設定すると使用開始

# NPM のインストール
- [Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions](https://github.com/nvm-sh/nvm)
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```
- ```~/.bashrc``` にパスが出力される
```bash
 export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```
- インストールされたことの確認
```bash
command -v nvm
```

## update npm
```bash
nvm install-latest-npm
```
```bash
Attempting to upgrade to the latest working version of npm...
* Installing latest `npm`; if this does not work on your node version, please report a bug!
/home/pi/.nvm/versions/node/v13.11.0/bin/npm -> /home/pi/.nvm/versions/node/v13.11.0/lib/node_modules/npm/bin/npm-cli.js

/home/pi/.nvm/versions/node/v13.11.0/bin/npx -> /home/pi/.nvm/versions/node/v13.11.0/lib/node_modules/npm/bin/npx-cli.js

+ npm@6.14.3
added 2 packages from 2 contributors, removed 1 package and updated 12 packages in 27.233s
* npm upgraded to: v6.14.3
```

## install gulp
```bash
npm install --global gulp-cli
```