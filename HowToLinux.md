# ユーザの追加
``` bash
useradd -m <user_name>  
usermod -aG wheel <user_name>
passwd <user_name>
```
-m : ホームディレクトリを作成する

# ユーザの削除
``` bash
userdel -r <user_name>  
```
ホームディレクトリや /etc/passwd から削除される

# job について
```bash
ctrl+z でjobの停止
jobs -l
bg %<job_number>
fg %<job_number>
kill %<job_number>
kill <PID>
ps -a (-a: 実行中プロセスの表示)
```
