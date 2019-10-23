# 横並びにする方法

## 1. float を使う
### 1.1 float
#### CSS floatプロパティを書いてみよう！
- float による横並び：[コード](./float1.html)

#### CSS floatプロパティによる回り込みを防ぐには？
- 回り込みの発生：[コード](./float2.html)  

- `clear: xx;`を用いて回り込みを解除。`clear: xx`を書いた要素から解除される。
  - 回り込みを解除１：[コード](./float3.html)  
- もう一つの例。解除専用の`<div>`要素を記載する。  
  - 回り込みを解除２：[コード](./float4.html)

#### 参考サイト
- [CSS floatを初心者向けに図で解説　抑えるべき注意点とは？](https://udemy.benesse.co.jp/development/web/css-float.html)
- [CSSで要素を横並びにする方法(floatとdisplayの使い方を解説)](https://creive.me/archives/13552/)

## 2. display を使う
### 2.1 display: flex;
#### 2.1.1 `flex` による横並び
- 箱が縦並びの例：[コード](display=flex1.html)
- 箱に `flex` 指定し、横並び表示：[コード](display=flex2.html)

#### 2.1.2 `flex-direction`：並べる方向を指定
- `flex-direction: row;`：横並び
- `flex-direction: colum;`：縦並び
- `flex-direction: colum-reverse;`：縦並び逆順
  - [コード](display=flex3.html)

#### 2.1.3 `flex-wrap`：折り返しの方法を指定
- `flex-wrap: nowrap;`：折り返さない
- `flex-wrap: wrapj-reverse;`：逆順で折り返す
  - [コード](display=flex4.html)

#### 2.1.4 `flex-flow`：並べる方向と折り返しの方法を同時に指定
- `flex-direction` と `flex-wrap` を同時に指定
- `flex-flow：wrap colum;`：縦方向で折り返し
  - [コード](display=flex5.html)

#### 2.1.5 `justify-content`：main-axis 方向の整列順の指定
- flexbox によって作られた行単位（もしくは flex-direction がカラムの場合は列単位）で、余白ができた時に要素の main-asix 方向の整列順を指定
- `justify-content: flex-start;`：左揃え（横並び指定時）
- `justify-content: flex-end;`：右揃え（横並び指定時）
- `justify-content: center;`：中央揃え（横並び指定時）
- `justify-content: space-between;`：余白を均等割り（左右に余白なし）
- `justify-content: space-around;`：余白を均等割り（左右に余白あり）
  - [コード](display=flex6.html)

#### 2.1.6 `align-items`：cross-axis 方向の整列順の指定
- Flexbox によって作られた行単位（もしくは flex-direction がカラムの場合は列単位）で、余白ができた時に要素の cross-asix 方向の整列順を指定
- `align-items: flex-start;`：左揃え（横並び指定時）
- `align-items: flex-end;`：右揃え（横並び指定時）
- `align-items: center;`：中央揃え（横並び指定時）
- `align-items: space-between;`：余白を均等割り（左右に余白なし）
- `align-items: space-around;`：余白を均等割り（左右に余白あり）
  - [コード](display=flex7.html)

#### 2.1.7 `align-content`：複数行ある際に使える整列
- 複数行をまとめて一つの塊のようにして扱う
- `alig-content: flex-start;`：左揃え（横並び指定時）
- `alig-content: flex-end;`：右揃え（横並び指定時）
- `alig-content: center;`：中央揃え（横並び指定時）
- `alig-content: space-between;`：余白を均等割り（左右に余白なし）
- `alig-content: space-around;`：余白を均等割り（左右に余白あり）
  - [コード](display=flex8.html)

#### 2.1.8 `align-self`：要素単体に対して位置を指定
- 複数行をまとめて一つの塊のようにして扱う
- `alig-self: flex-start;`：左揃え（横並び指定時）
- `alig-self: flex-end;`：右揃え（横並び指定時）
- `alig-self: center;`：中央揃え（横並び指定時）
- `alig-self: base-line;`：ベースラインに合わせる
- `alig-self: stretch;`：余白いっぱいまで伸ばす
  - [コード](display=flex9.html)
- 参考サイト
  - [CSS3 Flexbox 位置の揃え方まとめ](https://qiita.com/junya/items/7762da8052d86462f232)


#### 2.1.9 `order`：要素の並び順を指定
- `order` 指定していないものが先に並ぶ。`order` 指定すると、数字の順番通りに並ぶ。
  - [コード](display=flex10.html)

#### 2.1.10 `flex`：余白ができた場合、はみ出た場合に、要素を広げたり縮めたりする方法を指定
- `flex` は以下の要素を同時に指定する。以下の要素は同時に指定することが推奨されている。
  - `flex: flex-grow flex-shrink flex-basis;`
  - デフォルト値：`flex: 0 1 auto;`
  - `flex-basis` はコンテントの大きさを指定する。
  - `flex-basis: auto;` はコンテントの元の大きさのこと。自動調節ではない。
- `flex-grow` の使い方：複数指定した場合、指定した数値の比になるように、余白を各要素に分配する。
  - [コード](display=flex11.html)
- `flex-shrink` の使い方：複数指定した場合、指定した数値の比になるように、はみ出た要素分を分配して削る。
  - `flex-wrap: wrap` を親要素に指定している場合、折り返しが優先されて、`flex-shrink` が無視され、`flex-basis` で指定した大きさで表示される。
  - [コード](display=flex12.html)

|表記  |`flex-grow`  |`flex-shrink`  |`flex-basis`  |
|---|--:|--:|--:|
|デフォルト  |0  |1  |auto  |
|`flex: 20px;`  |0  |1  |20px  |
|`flex: 2;`  |2  |1  |auto  |
|`flex: 2 3;`  |2  |3  |auto  |

#### 2.1.11 `margin: auto`：余白ができた場合、右詰めする
- 複数の要素があった場合、ある要素意向を右詰めにしたい場合に指定すると便利。
  - [コード](display=flex13.html)

#### 2.1.12 3カラムの作成＆レスポンシブデザイン対応
- 左右の幅は固定、真ん中の要素はブラウザ幅に合わせて伸縮
- レスポンシブデザインにも対応させることができて便利
  - [コード](display=flex14.html)

### 2.2 display: inline-block;
- inline要素と同様に横並びになり、幅や高さも指定できる。
- `virtical-align: middle;` は使えない。
  - 幅や高さを指定した例：[コード](./display=inline-block.html)

### 2.3 display: inline;
- inline要素は横並びになるが、幅や高さは指定できない。  
  - 幅や高さを指定できない例：[コード](./display=inline.html)


### 2.4 display: table-cell;
- ブロック要素(ここでは「liタグ」)をテーブルの「td」として扱う
- tableの「行」と同じように横並びになる
- 幅や高さを指定できる
- `veatical-align: middle;` も利用できる
- `padding` は有効だが、`margin` は使えない
  - table-cell のできること、できないことの例：[コード](./display=table-cell.html)


### 参考サイト
[CSSで要素を横並びにする方法(floatとdisplayの使い方を解説)](https://creive.me/archives/13552/)

## 3. position: absolute;


