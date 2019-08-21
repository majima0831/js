### Basic of JavaScript
---
### JavaScript(JS)
JSとは動的な処理を行うためのプログラミング言語
---
Javaとは違う
---
なぜJavaと名前が似ているか？
---
元々はLiveScriptだったが、Javaがプログラミング言語として隆盛していたのでそれにあやかろう
---
LiveScript => JavaScript
になった！
---
## 基本的な構文
---
### 変数宣言
JSには変数宣言に使用するキーワードが3つ存在する
```
??? test = '変数宣言';
```
- var |
- let(ES6) |
- const(ES6) |
---
### 宣言の使い分け
基本的にconstを使用するのが望ましい

constは再宣言、再代入が不可であるのでコーダーの予期せぬバグを発生させない。

処理の中で値を変えたい変数がある場合はletを使用する
---
varは忘れていい遺物

メリットは左手だけで打てるくらい
---
変数宣言の小技として、複数の宣言をカンマ区切りで行うことができる。
```
const test1 = '1つめ',
      test2 = '2つめ';
```
---

### 配列、オブジェクト
#### 配列
先頭のインデックスが0
上記コードではコンソールに出力されるのはb
```
var test = ['a','b','c'];
console.log(test[1]);
```
---
#### オブジェクト
```
var test = {
      title: 'タイトル名',
      text: '本文',
      num: 1,
};
console.log(test['title']);
```
プロパティと値を紐づけた配列
前述した配列と違いインデックスでの取得はできない。
---
```
× User-Name: 'Majima'
× User Name: 'Majima'
○ 'User Name': 'Majima'
```
オブジェクトのプロパティは"や'で囲うが省略も可能
ただし-(ハイフン)やスペースを含んだプロパティにする場合は省略はできない
---
### DOM操作
DOMとは Document Object Model

DOMを利用する事で、HTMLの探索やスタイルの変更・イベントの設定・HTML要素の取得の他に、振る舞いを変えたり、ユーザー操作時の処理を設定することができます。
---
DOMツリーとノード(ここでDOMツリーの画像)
<img src="assets/DOM.gif">

ノードとはHTMLでいうタグ
---
DOM操作で代表的なもの
`document.getElementById(id)`

対象のIDを持つ要素を取得
---
documentってなに？
- documentとはDocumentオブジェクトを表している |

- DOMツリーの最上位に位置するノードである。 |
---
`document.getElementById(id)`

を無理矢理和訳すると

DOM全体を対象に引数として渡されたidと一致するIDを検索し、該当のノードを取得する

ということになる。
---
### ES6について
ES6とは
- ECMA Script6 の略 |
---
Ecma Internationalという機関のもとで標準化されたJS
---
### ES６で追加された機能
- let,constの変数宣言 |
- アロー関数 |
- モジュール機能 |
---
#### アロー関数
functionを使用していたのを省略した形で記述できる
```
let oldFunc = function(x) {
  console.log(x);
}

let arrowFunc = (x) => {
  console.log(x);
}
oldFunc('古い関数');
arrowFunc('アロー関数');
```
---
ただ省略するためのものではない。

thisの扱いが束縛？される

よってアローはfunctionのまるっきり上位互換というわけではないので、thisの使い方によって使い分けが必要になる
---
#### モジュール機能
モジュール機能前のjsファイルの読み込み
```
<script src="js/vender/jquery.min.js"></script>
<script src="js/common.js"></script>
<script src="js/~~~.js"></script>
<script src="js/~~~.js"></script>
```
---
importの仕方が何通りか存在する
```
import * as myModule from "/common.js";
import { myExport } from "/common.js";
import { foo, bar } from "/common.js";
import { mettyaNagaiNamaeNoExport as shortExport } from "/common.js";
```
---
from先ファイルのexportを全て取得する。

```
import * as myModule from "/common.js";
```

from先のtest()を利用したい場合は

```
myModule.test();
```
で利用可能
---
利用したいexportが1つの場合はfrom先で命名されている名前を指定して取得する

```
import { myExport } from "/common.js";
```
---
1つのファイルから複数importする場合はコンマで分けて取得できる

```
import { foo, bar } from "/common.js";
```
---
インポートする時にインポート先での名前を変更することも可能

```
import { mettyaNagaiNamaeNoExport as shortExport } from "/common.js";
```

{ export元での名前　as import先での名前 } from ~
---
## 小技
オブジェクトにはconsole.dir()が使える
consoleオブジェクトはけっこう種類ある

js.arrayの関数紹介
filter,map,some,findなど

なぜforeachを避けるのか

foreachでは何らかのループ処理であるとしか判別できないが、各関数は知っていればどういった意図で使用するものかが分かるので、
コードリーディングする際に負担になりづらいのが利点となる。
