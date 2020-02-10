# CSSについて



複数指定はカンマ

絞り込みはスペース

## 絞り込み方

- E.class　要素Eに指定してあるclass
- E[attribute]　要素Eで使われている属性
- E:not(F)　要素Eの中で、Fについいては除外する
- E > F　子要素
- E + F　次の要素
- E ~ F　以降の要素
- E:first-letter　最初の文字だけ

## 表やリストで使われる絞り込み方

- E:first-child　はじめの要素だけ
- E:lat-child　最後の要素だけ
- E:nth-child(odd)　奇数の項目だけ
- E:nth-child(3n)　3の倍数の項目だけ

## リンクでよく使うセレクタ

- a:hover　カーソルを載せたとき
- a:visited　訪問済み
- a:link　未訪問
- a:active　クリックした瞬間



## 参考リンク

- [CSSのセレクタとは？覚えておきたい25種類と書き方](https://saruwakakun.com/html-css/reference/selector)  
  サルワカのサイト。指定の仕方等かんたんにまとめてある。
- [意外と知らない!?CSSセレクタ20個のおさらい](http://weboook.blog22.fc2.com/blog-entry-268.html)
- [CSSの勉強を始める前に。初心者はこの30個だけ覚えればWEBサイトは作れる](http://designersnavi.com/css-begin/)  
  よく使うセレクタが一覧化されている。

