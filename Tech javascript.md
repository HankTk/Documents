# JavaScript

## Closure

```
クロージャを一言で表すと「スコープチェーンに存在する変数への参照を保持している関数」
-> A function holding a reference to a variable existing in the scope chain

関数の中の関数のこと、外の関数のスコープである変数にアクセスできる

クロージャは、独立した (自由な)変数を参照する関数です。言い換えるとクロージャ内で定義された関数は、自身が作成された環境を '覚えています'。https://developer.mozilla.org/ja/docs/Web/JavaScript/Closures

メリット/デメリット
関数終了後もローカル変数を参照できることのメリット１、グローバル変数の節減
関数終了後もローカル変数を参照できることのメリット２、クロージャを使うと１のメリットを享受しつつ計算量を増やさないことができる

クロージャは、クロージャが作成された時点でスコープ内にあったすべての変数や関数とともに存在する関数です。
クロージャは、外側（囲む）関数のスコープチェーン内の変数にアクセスできる内部関数です。クロージャは、次の3つのスコープ内の変数にアクセスできます。

scopes; specifically: 
(1) variable in its own scope, 
(2) variables in the enclosing function’s scope, and 
(3) global variables.
```

---

## Hoisting

```
ホイスティングは、宣言をトップに移動するJavaScriptのデフォルトの動作です。
ホイスティングはJavaScriptのドキュメントには見つからない用語です。ホイスティングは、JavaScriptの実行コンテキスト（特に作成フェーズと実行フェーズ）がどのように機能するかについての一般的な考え方として考え出されました。しかし、ホイスティングは誤解を招く可能性があります。例えば、ホイスティングは変数と関数の宣言がコードのトップに物理的に移動されると教えますが、実際にはそうではありません。実際に起こるのは、変数と関数の宣言がコンパイルフェーズ中にメモリに配置されることですが、コード内で入力した場所にそのまま残ります。

https://developer.mozilla.org/en-US/docs/Glossary/Hoisting
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/var
```

---

## this

```
this は、呼び出し時に決定される

thisとは 関数コール時にその関数が所属していたオブジェクト。
関数のコール時にレシーバーが無い時、this はグローバルオブジェクトになります。
ブラウザ実装の場合、これは通常 window オブジェクトです。

thisを操るメソッド
関数オブジェクトには、this をコントロールできる３つのメソッドがあります。（関数オブジェクトだけに存在する）
call, apply, bind
call と apply は 関数を実行する
bindは関数に値を束縛する
```

---

## Strict Mode

```
strictモードでは、最初にvarで宣言されていない変数を使用することはできません。
JavaScriptコードが "strict mode" で実行されるべきであることを定義します。
"use strict" ディレクティブはJavaScript 1.8.5（ECMAScriptバージョン5）で新しく追加されました。
これは文ではなくリテラル式であり、以前のバージョンのJavaScriptでは無視されます。
"use strict" の目的は、コードが "strict mode" で実行されるべきであることを示すことです。
strictモードでは、例えば宣言されていない変数を使用することはできません。

```

---

## データ型

| === プリミティブ型 ===                                   |
| -------------------------------------------------------- |
| Boolean                                                  |
| Number                                                   |
| String                                                   |
| Null —> JavaScript Engin show as object … this incorrect |
| Undefined                                                |

| === 非プリミティブ型 === |
| --------------------------- |
| Object                      |

<u>*null と undefined の違い、および == と === の違い*</u>

| 比較                     | 結果       |
| ----------------------- | ---------- |
| null === null           | # => true  |
| undefined === undefined | # => true  |
| undefined === null      | # => false |
| undefined == null       | # => true  |

---

## Object

### Object Creation

#### 直接｛｝で書く

クラスを定義する時などに用いる。プロトタイプが定義できないので、プロトタイプを指定したい場合は後からプロトタイプを指定する。

```
// 定義した後にプロトタイプ指定。

myObj = { p : "value" };
myObj.prototype = protoObj;

```

#### newで作成する

通常これを用いる。クラス名を付けたコンストラクタメソッドをあらかじめ用意していおいて、それが呼び出される。

```
function MyClass(){
	MyClass.prototype.name = "ProtoTypeMyClass";
    return this;
}    
```

#### Object.create()で作成する

継承させて作りたい時に使用する。継承したいプロパティを持つオブジェクトを引数に渡す。

```
// prototypeを渡すことも可能。
Object.Create(Object.prototype);
    
```

### オブジェクトとプロパティの考え方まとめ

```
<script>
  function MyClass(){
    this.member = 0; // これはインスタンス毎に作られる
    MyClass.prototype.name = "ProtoTypeMyClass"; // これはクラス共通
    return this;
  }
  // コンストラクタからオブジェクトを作る.
  var o = new MyClass();
  // プロトタイプからオブジェクトを作る
  var a = Object.create(MyClass.prototype);
  // インスタンスから継承してオブジェクトを作る
  var b = Object.create(o);
  console.log(o.name);
  console.log(o.member);
  console.log(a.name);
  console.log(a.member); // undfined
  console.log(b.name);
  console.log(b.member);
</script>

結果
ProtoTypeMyClass
0
ProtoTypeMyClass
undefined
ProtoTypeMyClass
0
```

---

## Strengths and Weaknesses

Do you know Javascript well; if so, what are it’s strengths and weaknesses?
http://www.jscripters.com/javascript-advantages-and-disadvantages/
https://www.quora.com/What-are-the-strengths-and-weaknesses-of-Go-C++-C-and-JavaScript

## Strengths
* JavaScriptはブラウザにネイティブな唯一の言語です。したがって、フロントエンドのWebアプリを作成したい場合は、少なくともJavaScriptにコンパイルされるものを使用する必要があります。
* JavaScriptは非常に動的な言語です。個人的にはこれは弱点だと感じますが、すぐにいくつかのことを試してみて、後で詳細を修正することができます。
* Webが成長したため、JavaScriptも成長しました。言語の最新バージョンは、以前のバージョンに比べて大幅に改善されました。

## Weaknesses
* JavaScriptは弱い型付けであり、動的型付けと混同しないでください。これは、明示的に指定しなくても、型が相互に変換されることを意味します。その結果、コードは一見正常に動作しているように見えます（実行時例外は発生しません）が、静かに奇妙な動作を引き起こします。
* JavaScriptは大幅に改善されましたが、ブラウザでサポートされているのは古いバージョンです。そしてそのバージョンはかなり悪いです。静かに壊れて混乱を引き起こし、デバッグが難しい問題を引き起こします。また、他の言語にある多くの機能が欠けています。
* Webには大きな注目が集まっており、新しいフレームワークが毎年登場しています。これはJavaScript開発の状態を改善しますが、JavaScript疲れとして知られるものにもつながります。

---

## CORS

---

## XSS

---

## Call, Apply, Bind

---

## CSS

```
position
    static (Default)
    relative
    fixed
    absolute
    sticky

Box Model:
    Margin
    order
    adding
    Content
```

---

## Skills survey - UI Developer

#### Instructions:
回答をこのマークダウンドキュメントで返していただけるとありがたいですが、必須ではありません。
ただし、別のドキュメント形式を作成する場合は、質問の順序や表現を変更しないでください。

#### Questions:

- Easy: (you shouldn't need Google for these)
- js:
- What's the difference between a variable that is: `null`, `undefined` or undeclared? How would you go about checking for any of these states?

```
Answer:
1, null means, variable defined, value with null
2, undefined means, variable defined but the value has not been initialized.
3, typeof myVar === 'undefined'
4, myVar === null
5,
if (this['test'] == undefined) {
    console.log('Undeclared');
}
if (!this.hasOwnProperty('test')) {
    console.log('Undeclared');
}
```

- What is a closure, and how and why would you use one?

```
Answer:
1, Closure is to create a scope or context, encapslate the state.
2, To avoid scoping problem in JavaScript. You maight see this in callbacks or Asyncronus code.
```

- What is `this`? How is `this` used? Discuss at least 2 ways that you can change `this` (in either ES5 or ES6)?

```
Answer:
1, `this` relate to scope or context in JavaScrit
2, `this` is to control accessing context
3, In ES5, can use call, apply or bind
4, In ES6, can use let or arrow function
```

- css:
- What is the order of greatest to least specificity?
- classes
- ids
- inline style attributes
- elements

```
Answer:
From greatest to least specificity,
-> inline style attributes, ids, classes, elements
```

- What's the difference between:

```
.shopping-list.list-item {
// ...
}

.shopping-list .list-item {
// ...
}

.shopping-list > .list-item {
// ...
}
```

```
Answer:
.shopping-list.list-item    -> element must have both classes
.shopping-list .list-item -> it can be any list-item that is a descendent of shopping-list
.shopping-list > .list-item -> list-item element must be a direct child of shopping-list element
```

- What's the difference between `display: none` and `visibility: hidden`, and when would choose one over the other?

```
Answer:
1, none means does not exist in DOM, hidden means in DOM but can not see it.
2, To avoid areas of the UI jupping aroud when you adjust these properties.
```

- What are other ways to visually hide content?

```
Answer:
1, move it off screen
2, Set hight or width as zero
3, change the color (dangerous for clickable items)
4, change transparent
5, use JavaScript to remove a node (harsh technique)
```

- Medium: (feel free to use what online resources you need, ...awesome if you can do this w/o though)
- js:
- Just for kicks, let's implement our own util library, create a 'util' module with the following util functions:
- `unique()`

```javascript
uniqueList = util.unique(['a', 'b', 'c', 'b', 'd', 'a', 'd', 'e']);

// ['a', 'b', 'c', 'd', 'e']
```

```
Answer:
var util = (function() {
    return {
        unique: function (arr) {
            const result = [];
            for (let i = 0; i < arr.length; i++) {
                let item = arr[i];
                if (result.indexOf(item) < 0) {
                    result.push(item);
                }
            }
            return result;
        }
    }
})();

let result = util.unique(['a', 'b', 'c', 'b', 'd', 'a', 'd', 'e']);

//console.log(result);

```

- `extend()`

```javascript
homer = util.extend({name: 'Homer'}, {occupation: 'Nuclear Safety Inspector'});
/*
{
	name: 'Homer', 
	occupation: 'Nuclear Safety Inspector'
}
*/


homer = util.extend(homer, {kids: [{name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'}]});
/*
{ name: 'Homer',
  occupation: 'Nuclear Safety Inspector',
  kids: [
  	{ name: 'Bart' },
  	{ name: 'Lisa' },
  	{ name: 'Maggie' }
  ]
}
*/
```

```
Answer:
var util = (function() {
    return {
        extend: function (obj1, obj2) {
            //return Object.assign(obj1, obj2);
            return {...obj1, ...obj2}
        }
    }
})();

var homer = util.extend({name: 'Homer'}, {occupation: 'Nuclear Safety Inspector'});
console.log(JSON.stringify(homer));

homer = util.extend(homer, {kids: [{name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'}]});
console.log(JSON.stringify(homer));
```

- Using the testing framework of your choice write the spec to test your implementation of the above functions

```
Answer:

var assert = require('assert');
var util = require('./util');

describe("Test util", function(){

	it ("Test unique", function() {
		let result = util.unique(['a', 'b', 'c', 'b', 'd', 'a', 'd', 'e']);
		assert.deepEqual(['a', 'b', 'c', 'd', 'e'], result)
	});

	it ("Test extend", function() {
		let homer = util.extend({name: 'Homer'}, {occupation: 'Nuclear Safety Inspector'});
		assert.deepEqual({"name":"Homer","occupation":"Nuclear Safety Inspector"}, homer)

		homer = util.extend(homer, {kids: [{name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'}]});
		assert.deepEqual({"name":"Homer","occupation":"Nuclear Safety Inspector","kids":[{"name":"Bart"},{"name":"Lisa"},{"name":"Maggie"}]}, homer)

	});

});
```

- css:
- Have a look at the following jsfiddle: http://jsfiddle.net/mipark2csco/o9v5rdpa/2/
- fork this guy (hit 'Fork')
- make the following changes, and save a new jsfiddle for each task (hit 'Update'), and paste your saved links back here:
- horizontally center the box
```

Answer:
http://jsfiddle.net/a4pa63Ld/2/
```

- right-align the box

```
Answer:
http://jsfiddle.net/a4pa63Ld/3/
```

- align the box in the bottom-right corner

```
Answer:
http://jsfiddle.net/a4pa63Ld/4/
```

- horizontally and vertically center the box

```
Answer:
http://jsfiddle.net/a4pa63Ld/5/
```

- Have a look at the following jsfiddle: https://jsfiddle.net/mipark2csco/v4k5rjag/
- fork this guy (hit 'Fork')
- make the following changes, and save a new jsfiddle for each task (hit 'Update'), and paste your saved links back here:
- vertically center the three boxes

```
Answer:
https://jsfiddle.net/5kzu3bje/1/
```

- horizontally center the three boxes

```
Answer:
https://jsfiddle.net/5kzu3bje/2/
```

- space the three boxes evenly horizontally, and center them vertically

```
Answer:
https://jsfiddle.net/5kzu3bje/3/
```

---

## タイマー処理

### 2種類の タイマー処理

* setInterval…一定時間ごとに特定の処理を繰り返す
* setTimeout…一定時間後に特定の処理をおこなう（繰り返さずに一度だけ）

```
setInterval(関数function, 一定時間の指定[, 引数1, 引数2, …])
```

```
setTimeout(関数function, 一定時間の指定[, 引数1, 引数2, …])
```

finctionは関数の定義、コンマで区切って一定時間の指定（ミリ秒）、functionが引数をとる場合には[  ]のなかで指定します。

※注意：setIntervalの「I」、setTimeoutの「T」は大文字で記述しましょう。
小文字で書くとプログラムが実行されません

### setTimeoutでタイマー処理をおこなう

```
<!DOCTYPE html>
<html lang = "ja">
  <head>
    <meta charset = "utf-8">
    <title>JavaScriptの練習</title>
  </head>
  <body>
    <script>
      var count = 0;
      var countup = function(){
        console.log(count++);
      }
    </script>
  </body>
</html>
```

countという変数を用意し、0を基準に1ずつカウントを足して（count++）いったものをconsole.logで出力します。そして、この一連の処理をさらにcountupという変数に入れています。
この変数countupの処理を1000ミリ秒後に呼び出したいとします。次のようにsetTimeoutを追加します。

```
<script>
  var count = 0;
  var countup = function(){
    console.log(count++);
  }
  setTimeout(countup, 1000);
</script>
```

setTimeoutでは一度きりしか呼び出されないので、0が1000ミリ秒後に出力されて終わりました。

### setTimeoutでsetIntervalのような繰り返しの処理をする方法

やり方は非常に単純です。繰り返し処理の関数のなか、つまり{  }内にsetTimeoutを記述し、countup();で呼び出し実行します。

```
<script>
  var count = 0;
  var countup = function(){
    console.log(count++);
    setTimeout(countup, 1000);
  }
  countup();
</script>
```

こうすることで、**一度処理が終わった地点から1000ミリ秒後にまた同じ処理を繰り返す**ようになります。
しかし、このままでは繰り返し処理がとまらず、カウントは半永久的に続いてしまいます。
では、繰り返し処理を指定した箇所でストップさせるにはどうしたら良いでしょう。
そのためには、clearTimeoutを追加します。

### clearTimeoutでsetTimeoutの処理を停止する
まずは、idを使ってさきほどのsetTimeout(countup, 1000);をまとめましょう。

```
var id = setTimeoutl(countup, 1000);
```

このidをclearTimeoutで指定することで、setTimeoutの処理を好きなタイミングでストップさせることができます（処理を止めるからclearですね）。

```
<script>
  var count = 0;
  var countup = function(){
    console.log(count++);
    var id = setTimeout(countup, 1000);
    if(count > 5){
      clearTimeout(id);　//idをclearTimeoutで指定している
    }
  }
  countup();
</script>
```

上のプログラムでは、setTimeoutの繰り返し処理が実行されcountupが5より多くなったとき（if(count > 5)）、clearTimeoutが実行されます。
よってブラウザでは、5まででカウントでストップします。
これで、setTimeoutを使って繰り返しのタイマー処理をしたり、clearTimeoutを合わせて実行を止めるといったことができるようになりました。

### setIntervalでの繰り返し処理とsetTimeoutでの繰り返し処理の違い
え？ ちょっと待って！ 同じ繰り返し処理なら、わざわざsetTimeoutを使わずsetIntervalを使ってプログラムを書けばいいんじゃないの？？ と思ったかた。実は、両者には微妙な違いがあります。


```
setIntervalで繰り返し処理をおこなった場合：処理開始時点から一定時間後に同じ処理を繰り返す
setTimeoutで繰り返し処理をおこなった場合：処理終了時点から一定時間後に同じ処理を繰り返す
```

よって、同じ1000ミリ秒後で時間を指定したとしても、次の処理がはじまるまでに要する時間がずれるのです。
また、処理1回分に要する時間がインターバルの時間を超えてしまうと、挙動に不具合が生じてしまいます。処理と処理のあいだに確実に一定の余裕を保ちたいなら、setTimeoutを使うようにしましょう。

---

## [スプレッド演算子の便利な使い方まとめ](https://qiita.com/Nossa/items/e6f503cbb95c8e6967f8#nodelist-%E3%82%84-htmlcollection-%E3%82%92%E9%85%8D%E5%88%97%E3%81%AE%E3%82%88%E3%81%86%E3%81%AB%E6%93%8D%E4%BD%9C%E3%81%99%E3%82%8B)

### スプレッド演算子

...（ピリオド３つ） と書きます。

配列ライクなオブジェクト（正確には for of で展開できるオブジェクト）を個々の値に展開することができます。

[スプレッド演算子](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

### 個々の値に展開する

```
const data = [15, -3, 78, 1];
console.log(Math.max(...data));    // 78

// もう以下のように書く必要はありません
console.log(Math.max.apply(null, data));
```

### 配列を複製する

配列をコピー（新しく参照）する場合は Array.from()、[].slice.call() などを使いますがスプレッド演算子を使うと以下のようにコーディングできます。

```
const ary = ['Pen', 'Pineapple', 'apple'];
const myAry = [...ary];

console.log(ary === myAry);    // false
console.log(myAry);            // ["Pen","Pineapple","apple"]
```

### 要素の参照は保たれます。

```
const fruits = [
  { 'banana': 100 },
  { 'cherry': 200 }
];
const myFruits = [...fruits];

fruits["0"].banana = 300;
console.log(myFruits);    // [{"banana":300},{"cherry":200}] ← myFruits[0].bananaも変わる
```

### 強力な配列操作

以下のような配列があるとします。

```
const data1 = [1, 2, 3];
const data2 = ['d', 'e', 'f'];
```

### より強力な.push()

```
data1.push(...data2);
console.log(data1);    // [1,2,3,"d","e","f"]

// もう以下のように書く必要はありません
Array.prototype.push.apply(data1, data2);
[].push.apply(data1, datat2);
```

### より強力な .unshift()

```
data1.unshift(...data2);
console.log(data1);    // ["d", "e", "f", 1, 2, 3]
```

### 配列をマージする

```
const merged = ['あ', ...data1, 'い', ...data2, 'う'];
console.log(merged);    // ["あ",1,2,3,"い","d","e","f","う"]
```

### 配列を分割する

```
let [a, b, ...other] = [1, 2, 3, 4, 5];

console.log(a);        // 1
console.log(b);        // 2
console.log(other);    // [3, 4, 5]
```

### 分割代入と組み合わせると配列の分割も簡単です。

分割代入 - MDN web docs
文字列を配列にする

```
const word = 'JavaScriptプログラミング';
const converted = [...word];
console.log(converted);    // ["J","a","v","a","S","c","r","i","p","t","プ","ロ","グ","ラ","ミ","ン","グ"]
```

### もう空文字で分割する（ .split('')）する必要はありません。

Array.from(word) と書くよりシンプルです。

```
example.js
const word = 'プログラミングJavaScript';

// 一文字づつ操作する。
[...word].forEach(c => console.log(c));    // ここでは一文字ずつ列挙してみました。

// - 文字列を反転する
const reversed = [...word].reduceRight((p, c) => p + c);    // 配列に変換し右から左へたたみ込む。
console.log(reversed);    // tpircSavaJグンミラグロプ
```

### 配列から重複を取り除く

```
const data = ['a', 'b', 'c', 'a', 'b', 'd'];
const dist = [...(new Set(data))];
```

Set オブジェクトは重複しない値の集合を管理するためのオブジェクトです。
重複する値が追加された場合には、それを無視します。

### 可変長引数を定義する

```
const sum = (...nums) => nums.reduce((p, c) => p + c);
console.log(sum(1, 2, 3, 4, 5));     // 15
```

引数が可変長であることを明示できます。
IDEで表示され関数の利用者は引数が可変長であることがわかります。

![image-20190222144812641](/Users/hidenori/Library/Application Support/typora-user-images/image-20190222144812641.png)

**arguments** オブジェクトと違い、スプレッド演算子で宣言された引数は **Array** です。
そのまま .reduce()、 .filter()、 .map() といった配列操作が行えます。

### NodeList や HtmlCollection を配列のように操作する
#### NodeList や HtmlCollction に .filter() を掛ける

```
const elems = document.getElementByClassName('checkboxClassName');

// 取得した **NodeList** から、**checked** プロパティが **true** かつ **class** プロパティに **'foo'** が含まれているものを抽出します。
const filtered = [...elems].filter(el => el.checked && el.classList.contains('foo'));
```

#### チェックボックスをチェック、リストボックスをセレクトする

```
const setCheckBox = (name, ...values) => {
  const elems = document.getElementsByName(name);
  elems.forEach(el => el.checked = values.includes(el.value));
}

setCheckBox('fruits', 'apple', 'banana');    // value が 'apple' 、'banana' のチェックボックスをチェックします。
```
