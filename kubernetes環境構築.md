# docker インストール
## ホストからVMへ資材を転送
```bash
scp "E:\VMImages\VirtualBox VMs\devenv\dockerInstall.sh" yskogt@192.168.33.10:~
```
## sshでvmへログイン
```bash
ssh yskogt@192.168.33.10
```
## シェルの実行
```bash
chmod 755 dockerInstall.sh
./dockerInstall.sh
```
## 動作確認
```bash
docker --version
sudo docker run hello-world
```
## シェルの内容
```bash
#!/usr/bin/bash
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install -y docker-ce --nobest
sudo systemctl enable docker
sudo systemctl start docker
```

# kubectl のインストール
## ホストからVMへ資材を転送
```bash
scp "E:\VMImages\VirtualBox VMs\devenv\kubernetes.repo" yskogt@192.168.33.10:/etc/yum.repos.d/kubernetes.repo
```
## sshでvmへログイン
```bash
ssh yskogt@192.168.33.10
```
## インストールの実行
```bash
sudo yum install -y kubectl
```

# minikube のインストール
## ホストからVMへ資材を転送
```bash
scp "E:\VMImages\VirtualBox VMs\devenv\minkubeInstall.sh" yskogt@192.168.33.10:~
```
## sshでvmへログイン
```bash
ssh yskogt@192.168.33.10
```
## シェルの実行
```bash
chmod 755 minkubeInstall.sh
./minkubeInstall.sh
```

## パスを通す
```bash
vi visudo
:/usr/local/bin
```

## minikube の実行
```bash
# パスが通っているとき
sudo minikube start --vm-driver=none

# パスが通っていないとき
sudo /usr/local/bin/minikube start --vm-driver=none
```

## config を設定
```bash

# version 1.2.0 の場合
sudo minikube config set vm-driver none

# version 1.8.2 の場合 
sudo minikube config set driver none
```

## シェルの内容
```bash
#!/usr/bin/bash

# add repo
sudo tee /etc/yum.repos.d/kubernetes.repo <<EOF > /dev/null
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF

# install "docker"
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install -y docker-ce --nobest
sudo systemctl enable docker
sudo systemctl start docker

# Install "kubectl"
sudo yum install -y kubectl

# Install "minikube"
#curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
# curl -Lo minikube https://github.com/kubernetes/minikube/releases/tag/v1.8.2
curl -Lo minikube https://github.com/kubernetes/minikube/releases/tag/v1.7.3
chmod +x minikube
sudo install minikube /usr/local/bin
rm -f minikube

# stop firewall
sudo systemctl disable firewalld
sudo systemctl stop firewalld

# Add addons
sudo /usr/local/bin/minikube start --vm-driver=none
# sudo minikube addons enable heapster
sudo minikube addons enable ingress
```

## addons の参照
```bash
minikube addons list
```

## minikube のアンインストール
```bash
sudo minikube delete
sudo rm /usr/local/bin/minikube
```

## sudo で実行できないとき
/usr/local/bin にパスを通す
```bash
sudo visudo
Defaults    secure_path = /sbin:/bin:/usr/sbin:/usr/local/bin:/usr/bin
```


# kubeadm のインストール
## ホストからVMへ資材を転送
```bash
scp "E:\VMImages\VirtualBox VMs\devenv\kubernetes.repo" yskogt@192.168.33.10:/etc/yum.repos.d/kubernetes.repo
scp "E:\VMImages\VirtualBox VMs\devenv\kubeadmInstall.sh" yskogt@192.168.33.10:~
```
## sshでvmへログイン
```bash
ssh yskogt@192.168.33.10
```
## シェルの実行
```bash
chmod 755 kubeadmInstall.sh
./kubeadmInstall.sh
```

## kubeadm インストールシェル
```bash
#!/usr/bin/bash

update-alternatives --set iptables /usr/sbin/iptables-legacy
sudo vi /etc/yum.repos.d/kubernetes.repo

# SELinux off
sudo setenforce 0
sudo sed -i --follow-symlinks 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/sysconfig/selinux

# opne internal port
sudo firewall-cmd --permanent --add-port=6443/tcp
sudo firewall-cmd --permanent --add-port=2379-2380/tcp
sudo firewall-cmd --permanent --add-port=10250/tcp
sudo firewall-cmd --permanent --add-port=10251/tcp
sudo firewall-cmd --permanent --add-port=10252/tcp
sudo firewall-cmd --permanent --add-port=10255/tcp
sudo firewall-cmd --reload
sudo modprobe br_netfilter
# sudo echo '1' > /proc/sys/net/bridge/bridge-nf-call-iptables

# install kubeadm
sudo yum install -y kubeadm

# init kubeadm
sudo swapoff -a
sudo kubeadm init
```

## kubeadm 用 yum レポジトリ
```bash
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
```

# ネットワークの設定
## ホストからVMへコピー
```bash
scp "E:\VMImages\VirtualBox VMs\devenv\initNetwork.sh" yskogt@192.168.33.10:~
```
## sshでvmへログイン
```bash
ssh yskogt@192.168.33.10
```
## シェルの実行
```bash
chmod 755 initNetwork.sh
./initNetwork.sh dockube001 100
```
※ リモートから実行するとipが変わるため接続が切れるため、ターミナルを閉じて、再度sshでログインする。
## シェルの内容
initNetwork.sh
```bash
#!/usr/bin/bash
sudo nmcli general hostname $1
sudo nmcli c mod enp0s8 connection.autoconnect yes
sudo nmcli c mod enp0s8 ipv4.method manual
sudo nmcli c mod enp0s8 ipv4.addresses 192.168.33.$2/24
sudo nmcli c mod enp0s8 ipv4.gateway 192.168.33.1
sudo nmcli device disconnect enp0s8
sudo nmcli device connect enp0s8
sudo systemctl restart NetworkManager
```

# ssh config
```bash
Host docukube001
  HostName dockube001
  User yskogt
  Port 22
  IdentityFile ~/.ssh/hoge.key
  ServerAliveInterval 60
```
