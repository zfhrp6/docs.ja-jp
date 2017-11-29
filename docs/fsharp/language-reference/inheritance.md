---
title: "継承 (F#)"
description: "'Inherit' キーワードを使用して f# 継承関係を指定する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b38ab2f6-7ba7-4839-8eff-e6bd6cfd2b2f
ms.openlocfilehash: 331c8f4e39aacd9d5e55bfbaf584f037e58d36a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance"></a>継承

継承は、"は-a"リレーションシップのモデルを使用または、オブジェクト指向プログラミングのサブタイプ指定します。


## <a name="specifying-inheritance-relationships"></a>継承関係を指定します。
使用して継承関係を指定する、`inherit`クラス宣言でキーワード。 基本的な構文形式は次の例に示します。

```fsharp
type MyDerived(...) =
    inherit MyBase(...)
```

クラスは、最大で 1 つ直接基底クラスを持つことができます。 使用して基底クラスを指定しないかどうか、`inherit`キーワードをクラスから暗黙的に継承`System.Object`です。


## <a name="inherited-members"></a>継承されたメンバー
クラスは、別のクラスから継承している場合、メソッドと基底クラスのメンバー ユーザーが使用できる派生クラスの場合、派生クラスの直接的なメンバーと同様です。

いずれかの let 束縛とコンス トラクターのパラメーターは、クラスにプライベート派生クラスからにアクセスすることはできません。

キーワード`base`は派生クラスで使用でき、基本クラスのインスタンスを参照します。 自己識別子のように使用されます。


## <a name="virtual-methods-and-overrides"></a>仮想メソッドとオーバーライド
仮想メソッドとプロパティ機能はやや異なります f# で他の .NET 言語と比較しています。 使用する新しい仮想メンバーを宣言する、`abstract`キーワード。 この操作は、そのメソッドの既定の実装を提供するかどうかに関係なく行います。 したがって、基底クラスの仮想メソッドの完全な定義では、このパターンを次に示します。

```fsharp
abstract member [method-name] : [type]

default [self-identifier].[method-name] [argument-list] = [method-body]
```

派生クラスでこの仮想メソッドのオーバーライドがこのパターンに従います。

```fsharp
override [self-identifier].[method-name] [argument-list] = [method-body]
```

基本クラスの既定の実装を省略した場合、基本クラスは抽象クラスになります。

次のコード例は、新しい仮想メソッドの宣言を示しています。`function1`で基底クラスと派生クラスでオーバーライドする方法です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2601.fs)]
    
## <a name="constructors-and-inheritance"></a>コンストラクターと継承
派生クラスでは、基本クラスのコンス トラクターを呼び出す必要があります。 基底クラス コンス トラクターの引数、引数のリストに表示、`inherit`句。 使用される値は、派生クラスのコンス トラクターに指定された引数から決定する必要があります。

次のコードは基底クラスと派生クラスでは、継承句で、派生クラスが基底クラス コンス トラクターを呼び出します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2602.fs)]

複数のコンス トラクターの場合は、次のコードを使用できます。 派生クラスのコンス トラクターの最初の行は、`inherit`句、およびフィールドで宣言されている明示的なフィールドとして表示されます、`val`キーワード。 詳細については、次を参照してください。[明示的なフィールド:、`val`キーワード](members/explicit-fields-the-val-keyword.md)です。

```fsharp
type BaseClass =
    val string1 : string
    new (str) = { string1 = str }
    new () = { string1 = "" }

type DerivedClass =
    inherit BaseClass

    val string2 : string
    new (str1, str2) = { inherit BaseClass(str1); string2 = str2 }
    new (str2) = { inherit BaseClass(); string2 = str2 }

let obj1 = DerivedClass("A", "B")
let obj2 = DerivedClass("A")
```

## <a name="alternatives-to-inheritance"></a>継承に代わる方法
型の軽微な変更が必要な場合は、継承する代わりにオブジェクト式の使用を検討してください。 次の例では、新しい派生型を作成する代わりにオブジェクト式の使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2603.fs)]

オブジェクトの式の詳細については、次を参照してください。[オブジェクト式](object-expressions.md)です。

オブジェクト階層を作成するときは、継承の代わりに判別共用体の使用を検討します。 判別共用体は、共通の全体的な型を共有する別のオブジェクトのさまざまなモデルの動作でこともできます。 1 つの判別共用体を多くの場合、不要に互いのわずかな違いは、派生クラスの数。 判別共用体の詳細については、次を参照してください。[判別共用体](discriminated-unions.md)です。


## <a name="see-also"></a>関連項目
[オブジェクト式](object-expressions.md)

[F# 言語リファレンス](index.md)
