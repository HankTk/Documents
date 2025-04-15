# JavaScript

## Closure

```
クロージャを一言で表すと「スコープチェーンに存在する変数への参照を保持している関数」
-> A function holding a reference to a variable existing in the scope chain

関数の中の関数のこと、外の関数のスコープである変数にアクセスできる

クロージャは、独立した (自由な)変数を参照する関数です。言い換えるとクロージャ内で定義された関数は、自身が作成された環境を '覚えています'。
https://developer.mozilla.org/ja/docs/Web/JavaScript/Closures

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
