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
### 繰り返し
for,forEachを使用した繰り返しの処理が代表的
---
### for
```
let test = [1,2,3,4,5];
for(let i=0; i < test.length; i++) {
      console.log(test[i]);
}
```
---
### Array.forEach
```
let test = [1,2,3,4,5];
test.forEach(x => {
      console.log(x);
});
```
---
### map
```
const num = 3
const test = [1, 2, 3, 4, 5]

// 配列のすべての値をaの値だけ足します。
const result = test.map(item => item + num)
// result = [4, 5, 6, 7, 8]
```
配列の各要素を加工する場合

---
### filter
```
var words = [
      'spray',
      'limit',
      'elite',
      'exuberant',
      'destruction',
      'present'
];

// 文字列の長さが6より大きいものを取得
const result = words.filter(word => word.length > 6);

// result = ["exuberant", "destruction", "present"]
```
条件にあった要素のみを取得
---
### find
```
var array1 = [5, 12, 8, 130, 44];

// 10より大きい値を取得
var found = array1.find(element =>
  return element > 10;
);
// found = 12
```
条件にあった最初の要素を取得
条件にあう要素がなかった場合undfinedを返す
---
### some
```
const ary = [1, 2, 3, 4, 5]
// 配列の中に偶数が含まれているかどうかをチェックします
const isBool = ary.some(item => item % 2 === 0)
// isBool = true
```
条件にあった要素を検索

ある時はtrue

ない時はfalseを返す
---
なぜforeachを避けるのか

foreachでは何らかのループ処理であるとしか判別できないが、各関数は知っていればどういった意図で使用するものかが分かるので、
コードリーディングする際に負担になりづらいのが利点となる。
---
### DOM操作
DOMとは Document Object Model

DOMを利用する事で、HTMLの探索やスタイルの変更・イベントの設定・HTML要素の取得の他に、振る舞いを変えたり、ユーザー操作時の処理を設定することができます。
---
DOMツリーとノード (ここでDOMツリーの画像)
<img src="assets/DOM.gif">

- DOMツリーとはHTMLドキュメントやXMLをツリー構造として表現したもの
- ノードとはHTMLでいうタグ
---
DOM操作で代表的なもの
`document.getElementById(id)`

対象のIDを持つ要素を取得
取得する要素を指定しているダイレクトアクセス
---
documentってなに？
- documentとはDocumentオブジェクトを表している |

- DOMツリーの最上位に位置するノードである。 |
---
`document.getElementById(id)`

DOM全体を対象に引数として渡されたidと一致するIDを検索し、該当のノードを取得する


ということになる。
---
### ノードウォーキング
あるノードを基準に、その親や子のノード取得する方法
---
- 親要素の取得

`element.parentNode`

- 最初,最後の子要素

`element.firstElementChild`

`element.lastElementChild`

- 子要素のリスト

`element.children`

- 一つ前の要素

`element.previousElementSibling`

- 一つ後の要素

`element.nextElementSibling`
---
### ES6について
ES6とは
- ECMA Script6 の略 |
---
ES = ECMA Script

Ecma Internationalという機関のもとで標準化されたJS
---
### ES2015って？
元々は1,2,3...

と続いていたが、web業界の発展がめざましく、今後は毎年標準化していこう

→じゃあ名前にはその年度をつけよう

ということでES6からはES2015と呼ばれるようになった
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
### Hoisting(巻き上げ)
```
test('巻き上がります');

function test(x) {
      console.log(x);
};
```
関数を定義する前に関数を呼び出す

他プログラミングならエラーになるがJSは巻き上げが起こって問題なく動作する
---
#### ただし関数の定義の仕方で巻き上げを起こさないことも出来る
```
test('巻き上がります');

let test = function(x) {
      console.log(x);
};
```
関数式での関数なら巻き上げは起きない
---
### 変数の巻き上げ
```
var test = 321;
function hoist() {
      console.log(test);
      var test = 123;
      console.log(test);
};

hoist();
console.log(test);
```

letやconstでは巻き上げは起こらない
---
### Hoistingについて作者から
---
In other words, what happened was that JavaScript implemented hoisting of function declarations so that programmers would not be forced to place the inner-most functions at the top of the script block, and the outer-most (top-level) functions at the bottom.

This order, which is forced in ML languages (such as LISP) is painful because programmers prefer reading code top-to-bottom, rather than bottom-to-top.

Languages like C/C++ get around this issue by using header files, and standalone declarations, which JavaScript doesn’t have.

Also, hoisting was required for implementing mutual recursion.
---
参考

https://qiita.com/Stranger_31/items/20baef019c117c3180d9

ちなみにletやconstが生まれたのは巻き上げ防止の為だそうです。
---
### Event Bubbling
---
### Scope Prototype
---
### strict
---
### shadow DOM
