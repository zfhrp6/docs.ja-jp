---
title: モジュール (F#)
description: F# モジュールは、f# コード、値、型、および f# プログラムでは、関数の値などのグループ化方法について説明します。
ms.date: 04/24/2017
ms.openlocfilehash: ddb6a0762171f8acc94f0ba0cf29c4b6b3e4990e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="modules"></a>モジュール

F# 言語のコンテキストで、*モジュール*f# コード、値、型、および f# プログラムでは、関数の値などのグループです。 モジュールのコードをグループ化すると、関連するコードをまとめることができ、プログラム内で名前の競合を回避するのに役立ちます

## <a name="syntax"></a>構文

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a>コメント
F# モジュールは、f# コードの構成要素の種類、値、関数の値、および内のコードなどのグループ化`do`バインドします。 静的メンバーのみを持つ共通言語ランタイム (CLR) クラスとして実装されます。 モジュールにファイル全体が含まれているかどうかによって、モジュール宣言の 2 種類があります: 最上位レベルのモジュールの宣言とローカル モジュール宣言します。 最上位レベルのモジュールの宣言には、モジュールには中にファイル全体が含まれます。 最上位レベルのモジュールの宣言は、ファイル内の最初の宣言としてのみ使用できます。

省略可能な最上位モジュール宣言の構文で*修飾名前空間*モジュールを含む入れ子になった名前空間の名前のシーケンスです。 修飾名前空間を事前に宣言する必要はありません。

最上位のモジュールの宣言をインデントする必要はありません。 ローカル モジュールのすべての宣言にインデントを設定する必要は。 ローカル モジュール宣言では、そのモジュール宣言の下にインデント宣言だけは、モジュールの一部です。

すべてのローカル モジュールを含むファイルの内容全体を拡張子を付けずにファイルと同じ名前を持つ暗黙的に作成された最上位モジュールの一部となるコード ファイルが最上位レベルのモジュールの宣言または名前空間の宣言で始まっていない場合最初の文字を大文字に変換します。 たとえば、次のファイルがあるとします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

このファイルは、この方法で記述されている場合、コンパイルは。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

をファイルに複数のモジュールがある場合は、モジュールごとにローカル モジュールの宣言を使用する必要があります。 外側の名前空間が宣言されている場合、これらのモジュールは、外側の名前空間の一部になります。 外側の名前空間が宣言されていない場合、モジュールは、暗黙的に作成された最上位モジュールの一部になります。 次のコード例では、複数のモジュールを含むコード ファイルを示します。 コンパイラが暗黙的にという名前の最上位モジュールを作成`Multiplemodules`、および`MyModule1`と`MyModule2`その最上位レベルのモジュールで入れ子にします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

プロジェクトまたは 1 つのコンパイルで複数のファイルが存在する場合、またはライブラリを構築する場合は、名前空間の宣言またはファイルの上部にあるモジュールを宣言する必要があります。 のみ、f# コンパイラは暗黙的にモジュール名を決定し、プロジェクトまたはコンパイルのコマンド ラインでは、1 つのファイルが存在し、アプリケーションを作成するときにします。

*アクセシビリティ修飾子*、次のいずれかになります: `public`、 `private`、`internal`です。 詳細については、「[Access Control](access-control.md)」(アクセス制御) を参照してください。 既定値はパブリックです。


## <a name="referencing-code-in-modules"></a>モジュール内のコードを参照します。
別のモジュールから関数、型、および値を参照するときにする必要がありますを使用する修飾名かモジュールを開きます。 修飾名を使用する場合は、名前空間、モジュール、および対象のプログラム要素の識別子を指定する必要があります。 次のようには、ピリオド (.)、修飾パスの各部分を分離します。

`Namespace1.Namespace2.ModuleName.Identifier`

モジュールまたは 1 つ以上のコードを簡略化する名前空間を開くことができます。 開く名前空間とモジュールの詳細については、次を参照してください。[インポート宣言:、`open`キーワード](import-declarations-the-open-keyword.md)です。

次のコード例では、ファイルの末尾までのすべてのコードを含む最上位レベルのモジュールを示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

同じプロジェクト内の別のファイルからこのコードを使用するには、修飾名を使用するか、または開く、モジュール、関数を使用する前に、次の例に示すようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a>入れ子になったモジュール
モジュールは、入れ子にすることができます。 内部のモジュールは、いない新しいモジュール、内側のモジュールがあることを示すために外部モジュール宣言枝葉と同じインデントする必要があります。 たとえば、次の 2 つの例を比較します。 モジュール`Z`次のコードの内部のモジュールです。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

モジュールが、`Z`モジュールに兄弟`Y`次のコードにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
モジュール`Z`モジュールで他の宣言枝葉と同じインデントしないために、次のコードでは、兄弟モジュールも`Y`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
最後に、外側のモジュールの宣言を持たず、その直後に別のモジュール宣言によって、新しいモジュール宣言は、内部のモジュールと見なされますが、コンパイラが警告が表示するかどうかは、2 番目のモジュールの定義は遠くよりインデントされません、まずは。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
警告を回避するのには、内部のモジュールをインデントします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
1 つの外部モジュール内にあるファイル内のすべてのコードが必要な内部モジュールをする場合は、外側のモジュールには、等号 (=) は不要し、インデントを設定するのには、外側のモジュールである任意の内部モジュールを宣言を含む、宣言することはありません。 内部モジュール宣言内の宣言は、インデントする必要はします。 次のコードでは、この例を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a>再帰的なモジュール

F# 4.1 には、再帰的に相互に含まれているすべてのコードでは、モジュールの概念が導入されています。  使用してこれを行う`module rec`です。  使用`module rec`タイプやモジュール間で相互に参照のコードを記述することはできませんに痛みがあるいくつかを減らすことができます。  この例を次に示します。

```fsharp
module rec RecursiveModule =
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
        let peel (b: Banana) =
            let flip (banana: Banana) =
                match banana.Orientation with
                | Up -> 
                    banana.Orientation <- Down
                    banana
                | Down -> banana

            let peelSides (banana: Banana) =
                banana.Sides
                |> List.map (function
                             | Unpeeled -> Peeled
                             | Peeled -> Peeled)

            match b.Orientation with
            | Up ->   b |> flip |> peelSides
            | Down -> b |> peelSides
```

なお例外`DontSqueezeTheBananaException`とクラス`Banana`両方には、互いを参照してください。  さらに、モジュール`BananaHelpers`とクラス`Banana`も互いを参照してください。  これを削除した場合、f# で表現できないが、`rec`からキーワード、`RecursiveModule`モジュール。

この機能ではも使用[名前空間](namespaces.md)f# 4.1 にします。

## <a name="see-also"></a>関連項目

[F# 言語リファレンス](index.md)
[名前空間](namespaces.md)
[f# RFC FS 1009 - ファイル内でより大きなスコープを相互に参照型とモジュールを許可します。](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
