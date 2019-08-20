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


---
## 小技
オブジェクトにはconsole.dir()が使える
consoleオブジェクトはけっこう種類ある

js.arrayの関数紹介
filter,map,some,findなど

なぜforeachを避けるのか

foreachでは何らかのループ処理であるとしか判別できないが、各関数は知っていればどういった意図で使用するものかが分かるので、
コードリーディングする際に負担になりづらいのが利点となる。
