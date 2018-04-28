---
title: 名前空間 (F#)
description: F# で名前空間を使用できるプログラム要素のグループに名前をアタッチするようにすることによって関連する機能の領域にコードを整理する方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 695de3b58b8567da60c8ef86900f8e78ea563e0e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="namespaces"></a>名前空間

名前空間を使用すると、プログラム要素のグループに名前を割り当てて、関連する機能の区分にコードを編成することができます。


## <a name="syntax"></a>構文

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a>コメント
名前空間にコードを配置する場合は、ファイル内の最初の宣言は名前空間を宣言する必要があります。 ファイル全体の内容は、名前空間の一部になります。

名前空間には、値と関数直接を含めることはできません。 代わりに、モジュール内では、値と関数を含める必要があるし、モジュールの名前空間に含まれます。 名前空間には、型、モジュールを含めることができます。

名前空間を宣言できます明示的に名前空間キーワードを使用して、または暗黙的にモジュールを宣言するとき。 名前空間を明示的に宣言するには、名前空間キーワードの後に名前空間の名前を使用します。 次の例では、型とその名前空間に含まれるモジュールのウィジェットの名前空間を宣言するコード ファイルを示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

ファイルの内容全体が 1 つのモジュールである場合は、宣言することも名前空間に暗黙的を使用して、`module`キーワードとモジュールの完全修飾名で新しい名前空間名を指定します。 次の例は、名前空間を宣言するコード ファイル`Widgets`とモジュール`WidgetsModule`関数が含まれています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

次のコードは同等上記のコードが、モジュールがローカル モジュール宣言します。 その場合は、名前空間は、独自の行に表示する必要があります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

1 つ以上のモジュールが 1 つまたは複数の名前空間の同じファイルに必要な場合は、ローカル モジュール宣言を使用する必要があります。 ローカル モジュール宣言を使用する場合は、モジュールの宣言で修飾名前空間を使用できません。 次のコードでは、名前空間の宣言と 2 つのローカル モジュール宣言を持つファイルを示します。 名前空間で直接、モジュールが含まれるこのケースでは、ファイルと同じ名前を持つ暗黙的に作成されたモジュールはありません。 他のコードで、ファイルなど、`do`モジュール メンバーを修飾する必要があります、内部のモジュールではなく、名前空間には、バインディング、`widgetFunction`モジュール名を使用しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

この例の出力は次のとおりです。

```fsharp
Module1 10 20
Module2 5 6
```

詳細については、次を参照してください。[モジュール](modules.md)です。

## <a name="nested-namespaces"></a>入れ子になった名前空間
入れ子になった名前空間を作成するときに、完全修飾する必要があります。 それ以外の場合、新しい最上位レベルの名前空間を作成します。 インデントは、名前空間の宣言で無視されます。

次の例では、入れ子になった名前空間を宣言する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a>ファイルとアセンブリの名前空間
名前空間は、1 つのプロジェクトまたはコンパイルで複数のファイルにまたがることができます。 用語*名前空間のフラグメント*1 つのファイルに含まれている名前空間の部分について説明します。 名前空間には、複数のアセンブリもまたがることができます。 たとえば、`System`名前空間には、多くのアセンブリに拡張されていて、入れ子になった名前空間多くにはが含まれていますが、全体の .NET Framework が含まれています。


## <a name="global-namespace"></a>グローバル Namespace
定義済みの名前空間を使用する`global`に最上位の .NET 名前空間名を格納します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

使用することできますもグローバル他の名前空間と名前が競合を解決するのには、たとえば、最上位の .NET 名前空間を参照します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a>再帰的な名前空間

F# 4.1 には、再帰的に相互に含まれているすべてのコードでは、名前空間の概念が導入されています。  使用してこれを行う`namespace rec`です。  使用`namespace rec`タイプやモジュール間で相互に参照のコードを記述することはできませんに痛みがあるいくつかを減らすことができます。  この例を次に示します。

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

なお例外`DontSqueezeTheBananaException`とクラス`Banana`両方には、互いを参照してください。  さらに、モジュール`BananaHelpers`とクラス`Banana`も互いを参照してください。  これを削除した場合、f# で表現できないが、`rec`からキーワード、`MutualReferences`名前空間。

この機能は使用できる最上位[モジュール](modules.md)f# 4.1 またはそれ以降。

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[モジュール](modules.md)

[F# RFC FS-1009 - ファイル内でより大きなスコープを相互に参照型とモジュールを許可します。](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
