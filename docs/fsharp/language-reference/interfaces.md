---
title: インターフェイス (F#)
description: F# でインターフェイスが他のクラスを実装する関連するメンバーのセットを指定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 54ae8a2840ce26814be25f08c3ed02e12df6b7c0
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="interfaces"></a>インターフェイス

*インターフェイス*他のクラスを実装する関連するメンバーのセットを指定します。

## <a name="syntax"></a>構文

```fsharp
// Interface declaration:
[ attributes ]
type [accessibility-modifier] interface-name =
    [ interface ]     [ inherit base-interface-name ...]
    abstract member1 : [ argument-types1 -> ] return-type1
    abstract member2 : [ argument-types2 -> ] return-type2
    ...
[ end ]

// Implementing, inside a class type definition:
interface interface-name with
    member self-identifier.member1argument-list = method-body1
    member self-identifier.member2argument-list = method-body2

// Implementing, by using an object expression:
[ attributes ]
let class-name (argument-list) =
    { new interface-name with
        member self-identifier.member1argument-list = method-body1
        member self-identifier.member2argument-list = method-body2
        [ base-interface-definitions ]
    }
    member-list
```

## <a name="remarks"></a>コメント
インターフェイスの宣言では、メンバーを実装していないする点を除いて、クラス宣言が似ています。 代わりに、すべてのメンバーが、抽象キーワードによって示される`abstract`です。 抽象メソッドのメソッド本体を指定しません。 ただしもと共にメソッドとして、メンバーの個別の定義を含めることで、既定の実装を用意することができます、`default`キーワード。 これは、他の .NET 言語の基本クラスでの仮想メソッドの作成と同じです。 このような仮想メソッドは、インターフェイスを実装するクラスでオーバーライドできます。

インターフェイスの既定のアクセシビリティが`public`です。

各メソッドのパラメーターに f# の通常の構文を使用して名前を付けることができます必要に応じて。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24032.fs)]

上記で`ISprintable`など、`Print`メソッドに型のパラメーターが 1 つ`string`名前を持つ`format`。

インターフェイスを実装する 2 つの方法: オブジェクト式を使用して、クラスの型を使用します。 どちらの場合は、クラス型またはオブジェクトの式は、メソッド本体をインターフェイスの抽象メソッドを提供します。 実装は、インターフェイスを実装する種類ごとに固有です。 そのため、さまざまな種類のインターフェイス メソッドは、互いに異なる可能性があります。

キーワード`interface`と`end`、軽量構文を使用するときに開始し、定義の最後をマークするは省略可能です。 これらのキーワードを使用しない場合、コンパイラはかどうかの型がクラスまたはインターフェイスを使用する構成要素を分析して、推定しようとします。 メンバーを定義または他のクラスの構文を使用する場合は、型がクラスとして解釈されます。

.NET のコーディング スタイルは、大文字のすべてのインターフェイスを開始する`I`です。


## <a name="implementing-interfaces-by-using-class-types"></a>クラスの型を使用してインターフェイスを実装します。
使用して、クラス型の 1 つまたは複数のインターフェイスを実装することができます、`interface`キーワード、インターフェイスの名前と`with`キーワード、インターフェイス メンバーの定義後に、次のコードに示すようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2801.fs)]

インターフェイスの実装が継承、ので、すべての派生クラスは、それらを再実装する必要はありません。


## <a name="calling-interface-methods"></a>インターフェイス メソッドの呼び出し
インターフェイス メソッドは、インターフェイスを実装する型のオブジェクトではなく、インターフェイスを介してのみ呼び出すことができます。 したがってを使用して、インターフェイス型にキャストする必要があります、`:>`演算子または`upcast`これらのメソッドを呼び出すために演算子。

型のオブジェクトがあるときに、インターフェイス メソッドを呼び出す`SomeClass`、次のコードに示すようにアップ キャスト オブジェクトをインターフェイス型必要があります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2802.fs)]

代わりには、キャスト、オブジェクトでメソッドを宣言する、次の例のように、インターフェイス メソッドを呼び出します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2803.fs)]
    
## <a name="implementing-interfaces-by-using-object-expressions"></a>オブジェクト式を使用してインターフェイスを実装します。
オブジェクトの式は、短いインターフェイスを実装する方法を提供します。 これらは、名前付きの型を作成する必要はありませんし、メソッドを追加せず、インターフェイス メソッドをサポートするオブジェクトを希望する場合に便利です。 オブジェクト式は、次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2804.fs)]
    
## <a name="interface-inheritance"></a>インターフェイスの継承
インターフェイスは、1 つまたは複数の基底インターフェイスから継承できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2805.fs)]
    
## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[オブジェクト式](object-expressions.md)

[クラス](classes.md)
