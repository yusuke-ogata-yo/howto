# How To Set Ubuntu Network

## 複数 NIC 搭載時のネットワーク設定

- デフォルトルートの設定方法がポイント
- Ununtu では、netplan で設定する
- デフォルトルートには、nameservers を記載するといいみたい
- gateway4: xxx.xxx.xxx.xxx を記載してもデフォルトルートとなる模様
  - おそらく、gateway4 を書くほうが良いのでは？nameserver だけだと、DNS を引きにいくルートが指定されていることにより、そのルートがデフォルトルート化されているように思う。

```bash
# ファイルの場所
/etc/netplan/00-installer-config.yaml
```

```bash
# 00-installer-config.yaml
# This is the network config written by 'subiquity'
network:
  ethernets:
    # NAT
    enp0s3:
      dhcp4: true
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
    # ホストオンリーアダプター
    enp0s8:
      addresses:
      - 192.168.56.100/24
      routes:
      - to: 192.168.56.0/24
        via: 192.168.56.1
    # 内部ネットワーク
    enp0s9:
      addresses:
      - 20.0.10.100/24
      routes:
      - to: 20.0.10.0/24
        via: 20.0.10.1
  version: 2
```