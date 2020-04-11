# Kubernetes の使い方

kubernetes コマンドを中心に備忘録として残す。

- [Kubernetes の使い方](#kubernetes-%e3%81%ae%e4%bd%bf%e3%81%84%e6%96%b9)
  - [kubectl コマンド](#kubectl-%e3%82%b3%e3%83%9e%e3%83%b3%e3%83%89)
    - [リソースの表示](#%e3%83%aa%e3%82%bd%e3%83%bc%e3%82%b9%e3%81%ae%e8%a1%a8%e7%a4%ba)
    - [ノードの表示](#%e3%83%8e%e3%83%bc%e3%83%89%e3%81%ae%e8%a1%a8%e7%a4%ba)
    - [Pod の表示](#pod-%e3%81%ae%e8%a1%a8%e7%a4%ba)
    - [Pod のリソース使用量を表示](#pod-%e3%81%ae%e3%83%aa%e3%82%bd%e3%83%bc%e3%82%b9%e4%bd%bf%e7%94%a8%e9%87%8f%e3%82%92%e8%a1%a8%e7%a4%ba)
  - [yaml ファイルの書き方](#yaml-%e3%83%95%e3%82%a1%e3%82%a4%e3%83%ab%e3%81%ae%e6%9b%b8%e3%81%8d%e6%96%b9)

## kubectl コマンド

### リソースの表示

```bash
kubectl get all
```

### ノードの表示

```bash
kubectl get nodes
```

### Pod の表示

すべtの Pod を表示

```bash
kubectl get pods
```

Pod のスペックの詳細を表示

```bash
kubectl get pods [metadata.name] --output=yaml
```

### Pod のリソース使用量を表示

``` bash
kubectl top pods [metadata.name] -o
```

## yaml ファイルの書き方

vscode の kubernetes 拡張を入れておくと Pod 保管がかかる。