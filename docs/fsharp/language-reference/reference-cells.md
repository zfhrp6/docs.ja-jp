---
title: 参照セル (F#)
description: F# 参照セルの記憶域の場所を有効にすると、参照セマンティクスを持つ変更可能な値を作成する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 3a632425356a250f07e5babd2751b9923eec6552
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2018
---
# <a name="reference-cells"></a>参照セル

*参照セル*を有効にすると、参照セマンティクスを持つ変更可能な値を作成する記憶域の場所です。

## <a name="syntax"></a>構文

```fsharp
ref expression
```

## <a name="remarks"></a>コメント
値をカプセル化する新しい参照セルを作成するには、値の前に `ref` 演算子を指定します。 基になる値は変更可能なので、後で変更できます。

参照セルは、単なるアドレスではなく、実際の値を保持します。 `ref` 演算子を使用して参照セルを作成すると、基の値のコピーが、カプセル化された変更可能な値として作成されます。

参照セルを逆参照するには、`!` (感嘆符) 演算子を使用します。

次のコード例は、参照セルの宣言と使用方法を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

出力は `50`になります。

参照セルは、次のように宣言される `Ref` ジェネリック レコード型のインスタンスです。

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

`'a ref` 型は、`Ref<'a>` のシノニムです。 コンパイラと IDE の IntelliSense では、この型について前者が表示されますが、基になる定義は後者です。

`ref` 演算子は、新しい参照セルを作成します。 次のコードは、`ref` 演算子の宣言です。

```fsharp
let ref x = { contents = x }
```

次の表に、参照セルで使用できる機能を示します。

|演算子、メンバー、またはフィールド|説明|型|定義|
|--------------------------|-----------|----|----------|
|`!` (逆参照演算子)|基になる値を返します。|`'a ref -> 'a`|`let (!) r = r.contents`|
|`:=` (代入演算子)|基になる値を変更します。|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|`ref` (演算子)|新しい参照セルに値をカプセル化します。|`'a -> 'a ref`|`let ref x = { contents = x }`|
|`Value` (プロパティ)|基になる値を取得または設定します。|`unit -> 'a`|`member x.Value = x.contents`|
|`contents` (レコード フィールド)|基になる値を取得または設定します。|`'a`|`let ref x = { contents = x }`|
基になる値にアクセスする方法はいくつかあります。 逆参照演算子 (`!`) によって返される値は、代入可能な値ではありません。 したがって、基になる値を変更する場合は、代わりに代入演算子 (`:=`) を使用する必要があります。

`Value` プロパティと `contents` フィールドは、いずれも代入可能な値です。 したがって、次のコードに示すように、これらを使用して基になる値にアクセスしたり、基になる値を変更したりできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

出力は次のとおりです。

```
10
10
11
12
```

`contents` フィールドは、他のバージョンの ML との互換性のために用意されており、コンパイル中に警告を生成します。 この警告を無効にするには、`--mlcompatibility` コンパイラ オプションを使用します。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。

次のコードは、パラメーターの引き渡しでの参照セルの使用方法を示しています。 インクリメンタ型には、メソッド パラメーターの型に byref を含むパラメーターを受け取るインクリメントがあります。 Byref パラメーター型で渡すことを示すこと呼び出し元必要があります参照セルまたは指定した型の典型的な変数のアドレスでこのケースの整数です。残りのコードを両方の引数の型とインクリメントを呼び出す方法と参照セル (ref myDelta1) を作成する変数で、ref 演算子の使用を示します。 次に、アドレス演算子 (&amp;) を使用して適切な引数を生成する方法を示しています。 最後に、インクリメント メソッドは、使用すると、バインドを使用して宣言されている参照セルを使用して、もう一度呼び出されます。 コードの最後の行は、の使い方を説明します。 印刷用に参照セルを逆参照演算子。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

参照渡しする方法の詳細については、次を参照してください。[パラメーターと引数](parameters-and-arguments.md)です。

>[!NOTE]
C# プログラマでは、その ref 異なる動作を f# で c# では、知っておく必要があります。 など、ref 引数を渡すときに使用するが、同じ効果 f# と c# ではします。

>[!NOTE]
`mutable` 変数が自動的に昇格する`'a ref`; クロージャでキャプチャされる場合は、次を参照してください。[値](values/index.md)です。

## <a name="consuming-c-ref-returns"></a>使用 (C#)`ref`を返します

使用できる 4.1 以降では f#、 `ref` c# で生成されるを返します。  このような呼び出しの結果は、`byref<_>`ポインター。

次の c# メソッド:

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

透過的にによって呼び出し可能 f# ない特殊な構文を使用します。

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

かかる場合があります関数を宣言することも、`ref`など、入力として返します。

```fsharp
let f (x: byref<int>) = &x
```

現在を生成する方法はありません、 `ref` f# で c# で消費されるを返します。

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[パラメーターと引数](parameters-and-arguments.md)

[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)

[値](values/index.md)
