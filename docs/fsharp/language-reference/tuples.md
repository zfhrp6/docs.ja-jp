---
title: タプル (F#)
description: F# タプル、名前のないが、順序付けられた、可能性のある異なる型の値のグループ化について説明します。
keywords: visual f#, f#, 関数型プログラミング
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 35069073-9a82-410f-8dea-912e2a152e6d
ms.openlocfilehash: e0a5e5eb08e13bd5cbe9f88a47d4cf4bba19ea22
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="tuples"></a>タプル

A*組*名前のないが、順序付けられた、可能性のある異なる型の値のグループです。  参照型または構造体の組はできますか。

## <a name="syntax"></a>構文

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a>コメント
各*要素*前の構文では有効な f# 式を指定できます。

## <a name="examples"></a>使用例
組には、ペア 3 要素、やなど、同じまたは異なる型のなどがあります。 いくつかの例は、次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a>個々 の値を取得します。
使えばパターン マッチにアクセスしたり、タプル要素の名前を割り当てる、次のコードに示すようにできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

外部のパターン マッチを使用して、組を分解することができますも、`match`を介して式`let`バインド。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

パターンを作成できますまたは関数への入力としての組が一致します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

タプルの 1 つだけの要素を必要がある場合、必要としない値の新しい名前を作成しないようにする、ワイルドカード文字 (アンダー スコア) を使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

構造体の組に参照組内の要素のコピーも簡単です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

関数は、`fst`と`snd`(組のみを参照)、最初を返し、2 番目のタプル要素のそれぞれします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

3 つの 3 番目の要素を返す組み込み関数はありませんが、次のように簡単に記述いずれか。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

一般に、パターン マッチを使用して個々 のタプル要素にアクセスすることをお勧めします。

## <a name="using-tuples"></a>組の使用
組は、次の例で示すように、関数から複数の値を返す便利な手段を提供します。 この例では、整数の除算を実行し、結果を丸め、タプルのペアの最初のメンバーとして操作と、ペアの 2 番目のメンバーとして残りの部分を返します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

暗黙的なカリー化関数の引数は、通常の関数の構文で指定されるを避けたい場合に、組を関数の引数として使用もできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

関数を定義するには、通常の構文`let sum a b = a + b`次のコードに示すように、関数の最初の引数の部分的なアプリケーションである関数を定義することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

パラメーターとしての組を使用するには、カリー化と無効になります。 詳細についてを参照してください「部分的なアプリケーションの引数」[関数](functions/index.md)です。

## <a name="names-of-tuple-types"></a>タプルの型の名前
使用する組のある型の名前を記述するときに、`*`要素を区切る記号。 構成される組の`int`、 `float`、および`string`など`(10, 10.0, "ten")`型が次のように書き込まれます。

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>C# の組との相互運用

C# 7.0 では、組を言語で導入されました。  C# 内の組構造体と f# の構造体のタプルに同じです。  C# と相互運用する必要がある場合は、構造体の組を使用する必要があります。

これは簡単に行えます。  たとえば、c# のクラスに組を渡すし、これは、組でも、その結果を使用する必要があるとします。

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

F# コードで、パラメーターとして構造体の組を渡すし、構造体タプルとして結果を使用できます。

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>参照の組と構造体の組の間で変換します。

参照の組と構造体の組は、完全に別の基になる表現であるために、暗黙的に変換できることはできません。  つまり、次のようなコードはコンパイルされません。

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

パターンを作成する必要があります 1 つの組が一致し、他の構成要素を構築します。  例えば:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>参照の組をコンパイルした形式
コンパイル時に、タプルの形式を説明します。  ここにある情報は、.NET Framework 3.5 を対象としている場合を除き、読み取りに必要なまたは下限はありません。

組はすべての名前付き、いくつかのジェネリック型の 1 つのオブジェクトにコンパイル`System.Tuple`アリティ、または型パラメーターの数のオーバー ロードです。 タプル型は、c# または Visual Basic などの他の言語から表示するときに、またはを f# の構成要素に対応していないツールを使用しているときに、このフォームに表示されます。 `Tuple`型は .NET Framework 4 で導入されました。 コンパイラのバージョンを使用して、.NET Framework の以前のバージョンを対象とする場合[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) 2.0 のバージョンの f# コア ライブラリからです。 このライブラリ内の型は、2.0、3.0、および 3.5、.NET Framework のバージョンを対象とするアプリケーションでのみ使用されます。 型の転送は .NET Framework 2.0 と .NET Framework 4 の F# でのコンポーネント間でのバイナリの互換性を確保するために使用します。

### <a name="compiled-form-of-struct-tuples"></a>構造体の組をコンパイルした形式

構造体の組 (たとえば、 `struct (x, y)`)、参照の組から基本的に異なります。  コンパイル、<xref:System.ValueTuple>アリティ、または型パラメーターの数によってオーバー ロードされた型。  これらと同じ[c# 7.0 組](../../csharp/tuples.md)と[Visual Basic 2017 組](../../visual-basic/programming-guide/language-features/data-types/tuples.md)、双方向の相互運用とします。

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[F# の型](fsharp-types.md)
