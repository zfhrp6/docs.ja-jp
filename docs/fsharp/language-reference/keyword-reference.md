---
title: キーワード リファレンス (F#)
description: F# 言語のキーワードのすべてについての情報へのリンクを検索します。
ms.date: 05/16/2016
ms.openlocfilehash: 7d8a2bf667f5303cc19e8d4279e433efca25c294
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
ms.locfileid: "33840890"
---
# <a name="keyword-reference"></a>キーワード リファレンス

このトピックには、f# 言語のすべてのキーワードについての情報へのリンクが含まれています。

## <a name="f-keyword-table"></a>F# キーワード テーブル

次の表は、簡単な説明と詳細情報を格納する関連するトピックへのリンクのアルファベット順に f# のすべてのキーワードを示します。

|キーワード|リンク|説明|
|-------|----|-----------|
|`abstract`|[メンバー](members/index.md)<br /><br />[抽象クラス](abstract-classes.md)|か、実装を持たない型で宣言されているかを仮想が既定の実装方法を示します。|
|`and`|[`let` バインド](functions/let-bindings.md)<br /><br />[メンバー](members/index.md)<br /><br />[制約](generics/constraints.md)|相互再帰のバインディングで、ジェネリック パラメーターで複数の制約を使用して、プロパティ宣言で使用されます。|
|`as`|[クラス](classes.md)<br /><br />[パターン一致](Pattern-Matching.md)|現在のクラス オブジェクトのオブジェクト名を提供するために使用します。 名前を付けるパターン一致内のパターン全体にも使用されます。|
|`assert`|[アサーション](assertions.md)|デバッグ中にコードを検証するために使用します。|
|`base`|[クラス](classes.md)<br /><br />[継承](inheritance.md)|基底クラスのオブジェクトの名前として使用されます。|
|`begin`|[冗語構文](verbose-syntax.md)|冗語構文は、コード ブロックの先頭を示します。|
|`class`|[クラス](classes.md)|冗語構文は、クラス定義の開始を示します。|
|`default`|[メンバー](members/index.md)|抽象メソッドの実装を示します抽象メソッドの宣言と共に使用すると、仮想メソッドを作成します。|
|`delegate`|[デリゲート](delegates.md)|デリゲートを宣言するために使用します。|
|`do`|[do バインド](functions/do-bindings.md)<br /><br />[ループ: `for...to` 式](loops-for-to-expression.md)<br /><br />[ループ: `for...in` 式](loops-for-in-expression.md)<br /><br />[ループ: `while...do` 式](loops-while-do-expression.md)|ループ構造または命令型コードを実行するために使用します。|
|`done`|[冗語構文](verbose-syntax.md)|冗語構文は、ループの式のコードのブロックの末尾を示します。|
|`downcast`|[キャストと変換](casting-and-conversions.md)|継承チェーンで下位にある型に変換するために使用します。|
|`downto`|[ループ: `for...to` 式](loops-for-to-expression.md)|`for`式、カウントを逆にするときに使用します。|
|`elif`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)|条件付き分岐のために使用します。 短い形式`else if`です。|
|`else`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)|条件付き分岐のために使用します。|
|`end`|[構造体](structures.md)<br /><br />[判別共用体](discriminated-unions.md)<br /><br />[レコード](records.md)<br /><br />[型拡張](type-extensions.md)<br /><br />[冗語構文](verbose-syntax.md)|型の定義と型の拡張機能では、メンバーの定義のセクションの末尾を示します。<br /><br />冗語構文を使用して開始されるコード ブロックの末尾を指定するために、`begin`キーワード。|
|`exception`|[例外処理](exception-handling/index.md)<br /><br />[例外の種類](exception-handling/exception-types.md)|例外の種類を宣言するために使用します。|
|`extern`|[外部関数](functions/external-functions.md)|宣言されたプログラム要素が別のバイナリまたはアセンブリで定義されていることを示します。|
|`false`|[プリミティブ型](primitive-types.md)|ブール型リテラルとして使用します。|
|`finally`|[例外: `try...finally` 式](exception-handling/the-try-finally-expression.md)|組み合わせて使用`try`例外が発生したかどうかに関係なく実行されるコードのブロックを導入します。|
|`fixed`|[固定](fixed.md)|「ピン留め」ポインターをガベージ コレクションの対象を防ぐためにスタックにするために使用します。|
|`for`|[ループ: `for...to` 式](loops-for-to-expression.md)<br /><br />[ループ: for...in 式](loops-for-in-expression.md)|ループ構造で使用されます。|
|`fun`|[ラムダ式:`fun`キーワード](functions/lambda-expressions-the-fun-keyword.md)|ラムダ式とも呼ばれる匿名関数で使用します。|
|`function`|[match 式](match-expressions.md)<br /><br />[ラムダ式: fun キーワード](functions/lambda-expressions-the-fun-keyword.md)|短いの代わりに使用される、`fun`キーワードと`match`引数を 1 つに一致するパターンを持つラムダ式の式。|
|`global`|[名前空間](namespaces.md)|最上位の .NET 名前空間を参照するために使用します。|
|`if`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)|条件付き分岐構造で使用されます。|
|`in`|[ループ: for...in 式](loops-for-in-expression.md)<br /><br />[冗語構文](verbose-syntax.md)|バインディングから式を区切るためには、シーケンス式と冗語構文を使用します。|
|`inherit`|[継承](inheritance.md)|基底クラスまたは基本インターフェイスを指定するために使用します。|
|`inline`|[関数](functions/index.md)<br /><br />[インライン関数](functions/inline-functions.md)|呼び出し元のコードに直接統合する必要があります関数を示すために使用します。|
|`interface`|[インターフェイス](interfaces.md)|宣言し、のインターフェイスを実装するために使用します。|
|`internal`|[アクセス制御](access-control.md)|メンバーが表示されているを指定するため、アセンブリ内では、外側にします。|
|`lazy`|[遅延計算](lazy-computations.md)|結果が必要な場合にのみ実行する計算を指定するために使用します。|
|`let`|[`let` バインド](functions/let-bindings.md)|関連付けるには、またはバインドして、値または関数名に使用します。|
|`let!`|[非同期ワークフロー](asynchronous-workflows.md)<br /><br />[コンピュテーション式](computation-expressions.md)|非同期ワークフローする非同期計算の結果に名前をバインドするにまたは、結果は、計算の種類の名前にバインドするために使用、その他の計算式を使用します。|
|`match`|[match 式](match-expressions.md)|パターンに値を比較することで分岐を使用します。|
|`member`|[メンバー](members/index.md)|プロパティまたはオブジェクト型のメソッドを宣言するために使用します。|
|`module`|[モジュール](modules.md)|他のコードから論理的に分離するには、関連する型、値、および関数のグループの名前を関連付けるために使用します。|
|`mutable`|[let バインド](functions/let-bindings.md)|変更可能な値は、変数を宣言するために使用します。|
|`namespace`|[名前空間](namespaces.md)|他のコードから論理的に分離するには、関連する型とモジュールの名前を関連付けるために使用します。|
|`new`|[コンストラクター](members/constructors.md)<br /><br />[制約](generics/constraints.md)|宣言、定義、またはを作成するか、オブジェクトを作成するには、コンス トラクターの呼び出しに使用されます。<br /><br />型が特定のコンス トラクターを持つ必要がありますを示すにジェネリック パラメーターの制約にも使用されます。|
|`not`|[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)<br /><br />[制約](generics/constraints.md)|実際にはキーワードです。 ただし、`not struct`組み合わせでは、ジェネリック パラメーターの制約として使用します。|
|`null`|[null 値](values/null-values.md)<br /><br />[制約](generics/constraints.md)|オブジェクトがないことを示します。<br /><br />ジェネリック パラメーターの制約にも使用されます。|
|`of`|[判別共用体](discriminated-unions.md)<br /><br />[デリゲート](delegates.md)<br /><br />[例外の種類](exception-handling/exception-types.md)|デリゲートと例外の宣言とカテゴリの値の型を示すために判別共用体でを使用します。|
|`open`|[インポート宣言: `open` キーワード](import-declarations-the-open-keyword.md)|名前空間またはモジュールの内容を修飾しないで使用できるようにするために使用します。|
|`or`|[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)<br /><br />[制約](generics/constraints.md)|ブール値としてブール条件で使用される`or`演算子。 等価 '||`.<br /><br />メンバー制約でも使用されます。|
|`override`|[メンバー](members/index.md)|基本のバージョンとは異なる、abstract または仮想メソッドのバージョンを実装するために使用します。|
|`private`|[アクセス制御](access-control.md)|同じ型またはモジュール内のコードにメンバーへのアクセスを制限します。|
|`public`|[アクセス制御](access-control.md)|型の外部からのメンバーにアクセスをできます。|
|`rec`|[関数](functions/index.md)|関数が再帰的であることを示すために使用します。|
|`return`|[非同期ワークフロー](Asynchronous-Workflows.md)<br /><br />[コンピュテーション式](computation-expressions.md)|コンピュテーション式の結果として提供する値を示すために使用します。|
|`return!`|[コンピュテーション式](computation-expressions.md)<br /><br />[非同期ワークフロー](asynchronous-workflows.md)|コンピュテーション式を示すために使用するには、評価すると、そのを含むコンピュテーション式の結果によって提供されます。|
|`select`|[クエリ式](query-expressions.md)|クエリ式で使用すると、どのようなフィールドまたは抽出する列を指定します。 コンテキスト キーワード、つまり実際に予約語ではありませんし、適切なコンテキストでキーワードに似た動作だけあることに注意してください。|
|`static`|[メンバー](members/index.md)|メソッドや型のインスタンスなしで呼び出されるプロパティまたは型のすべてのインスタンス間で共有されている値のメンバーを示すために使用します。|
|`struct`|[構造体](structures.md)<br /><br />[制約](generics/constraints.md)|構造体の型を宣言するために使用します。<br /><br />ジェネリック パラメーターの制約にも使用されます。<br /><br />モジュールの定義で OCaml 互換性のために使用します。|
|`then`|[条件式: `if...then...else`](conditional-expressions-if-then-else.md)<br /><br />[コンストラクター](members/constructors.md)|条件式で使用されます。<br /><br />またオブジェクトの構築後に副作用を実行するために使用します。|
|`to`|[ループ: `for...to` 式](loops-for-to-expression.md)|使用される`for`ループ範囲を示します。|
|`true`|[プリミティブ型](primitive-types.md)|ブール型リテラルとして使用します。|
|`try`|[例外: try...with 式](exception-handling/the-try-with-expression.md)<br /><br />[: 例外最後に式](exception-handling/the-try-finally-expression.md)|例外が生成されるコードのブロックを導入するために使用します。 組み合わせて使用`with`または`finally`です。|
|`type`|[F# の型](fsharp-types.md)<br /><br />[クラス](classes.md)<br /><br />[レコード](records.md)<br /><br />[構造体](structures.md)<br /><br />[列挙型](enumerations.md)<br /><br />[判別共用体](discriminated-unions.md)<br /><br />[型略称](type-abbreviations.md)<br /><br />[測定単位](units-of-measure.md)|クラス、レコード、構造体、判別共用体、列挙型、長さの単位を宣言するか、省略名を入力するために使用します。|
|`upcast`|[キャストと変換](casting-and-conversions.md)|継承チェーン内の上位である型に変換するために使用します。|
|`use`|[リソースの管理: `use` キーワード](resource-management-the-use-keyword.md)|代わりに使用`let`を必要とする値の`Dispose`を呼び出してリソースを解放します。|
|`use!`|[コンピュテーション式](computation-expressions.md)<br /><br />[非同期ワークフロー](asynchronous-workflows.md)|代わりに使用`let!`非同期ワークフローやその他の計算式の値を必要とする`Dispose`を呼び出してリソースを解放します。|
|`val`|[明示的なフィールド: `val` キーワード](members/explicit-fields-the-val-keyword.md)<br /><br />[シグネチャ](signatures.md)<br /><br />[メンバー](members/index.md)|値を示すために署名または限られた状況で、メンバーを宣言する型を使用します。|
|`void`|[プリミティブ型](primitive-types.md)|.NET を示す`void`型です。 他の .NET 言語と相互運用するときに使用します。|
|`when`|[制約](generics/constraints.md)|ブール条件の使用 (*ときにガード*) パターン一致とジェネリック型パラメーターの制約句を紹介します。|
|`while`|[ループ: `while...do` 式](loops-while-do-expression.md)|ループ構造が導入されています。|
|`with`|[match 式](match-expressions.md)<br /><br />[オブジェクト式](object-expressions.md)<br /><br />[レコード式のコピーと更新](copy-and-update-record-expressions.md)<br /><br />[型拡張](type-extensions.md)<br /><br />[例外: `try...with` 式](exception-handling/the-try-with-expression.md)|と共に使用される、`match`パターン マッチ式でのキーワードです。 メンバーの定義を紹介し、例外ハンドラーの導入にオブジェクト式、レコードのコピー式や型の拡張機能にも使用されます。|
|`yield`|[シーケンス](sequences.md)|シーケンスの値を生成するために、シーケンス式で使用されます。|
|`yield!`|[コンピュテーション式](computation-expressions.md)<br /><br />[非同期ワークフロー](asynchronous-workflows.md)|コンピュテーション式で指定計算式の結果を含むコンピュテーション式の結果のコレクションに追加するために使用します。|

次のトークンでは、OCaml 言語のキーワードであるために、f# で予約されています。

* `asr`
* `land`
* `lor`
* `lsl`
* `lsr`
* `lxor`
* `mod`
* `sig`

使用する場合、`--mlcompatibility`コンパイラ オプションは、上記のキーワードが使用可能な識別子として。

次のトークンは、f# 言語の将来の拡張のキーワードとして予約されています。

* `atomic`
* `break`
* `checked`
* `component`
* `const`
* `constraint`
* `constructor`
* `continue`
* `eager`
* `event`
* `external`
* `functor`
* `include`
* `method`
* `mixin`
* `object`
* `parallel`
* `process`
* `protected`
* `pure`
* `sealed`
* `tailcall`
* `trait`
* `virtual`
* `volatile`

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)

[コンパイラ オプション](compiler-options.md)
