---
title: "インポート宣言: open キーワード (F#)"
description: "完全修飾名を使用せずに参照できる要素を f# インポート宣言し、モジュールまたは名前空間を指定する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1e98e48c-52e9-4314-8954-85d5583125f0
ms.openlocfilehash: a6d79bed3dd202657d06956edf9499a9b21a5f03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="import-declarations-the-open-keyword"></a>インポート宣言:`open`キーワード

> [!NOTE]
この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

*インポート宣言*モジュールまたは完全修飾名を使用せずに参照できる要素の名前空間を指定します。


## <a name="syntax"></a>構文

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>コメント
名前空間またはモジュールの完全修飾パスを使用してコードを参照するたびには、書き込み、読み取り、および管理することは困難コードを作成できます。 代わりに、使用することができます、`open`キーワードを頻繁に使用されるモジュールと名前空間モジュールまたは名前空間のメンバーを参照するときに、完全修飾名ではなく、名前の短縮形を使用できるようにします。 このキーワードがに似ていますが、 `using` 、C# の場合は、キーワード`using namespace`Visual c、および`Imports`Visual Basic でします。

モジュールまたは名前空間は、同じプロジェクト内、または参照先プロジェクトまたはアセンブリ内にする必要があります。 そうでない場合、プロジェクトへの参照を追加したり、使用、`-reference`コマンド`-`ライン オプション (またはその省略形`-r`)。 詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。

インポート宣言は、その外側の名前空間、モジュール、またはファイルの末尾までの宣言を次のコードで使用できる名前を使用します。

複数のインポート宣言を使用する場合は、別々 の行に表示されます。

次のコードの使用を示しています、`open`コードを簡略化するキーワードです。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F# コンパイラは生成されませんエラーまたは警告が 2 つ以上の開いているモジュールまたは名前空間に出現した場合、同じ名前のあいまいさが発生したとき。 あいまいさが発生すると、f# 優先直前に開かれた複数のモジュールまたは名前空間。 たとえば、次のコードで`empty`意味`Seq.empty`場合でも、`empty`両方にある、`List`と`Seq`モジュール。

```fsharp
open List
open Seq
printfn "%A" empty
```

そのため、注意を開くときのモジュールまたは名前空間など`List`または`Seq`同じ名前です。 代わりに、修飾名を使用するメンバーが含まれています。 コードがインポート宣言の順序に依存しているすべての状況を避ける必要があります。


## <a name="namespaces-that-are-open-by-default"></a>既定で開かれている名前空間
一部の名前空間は、明示的なインポート宣言がなくても暗黙的に開かれたことの f# コードで頻繁に使用されます。 次の表は、既定で開かれている名前空間を示します。

|名前空間|説明|
|---------|-----------|
|`Microsoft.FSharp.Core`|基本的な f# 型の定義を含む組み込み型など`int`と`float`です。|
|`Microsoft.FSharp.Core.Operators`|基本的な算術演算子を含む`+`と`*`です。|
|`Microsoft.FSharp.Collections`|変更できないコレクション クラスを含む`List`と`Array`です。|
|`Microsoft.FSharp.Control`|レイジー評価と非同期ワークフローなどのコントロール構成要素の型が含まれています。|
|`Microsoft.FSharp.Text`|書式設定された IO は、のように関数を含む、`printf`関数。|

## <a name="autoopen-attribute"></a>AutoOpen 属性
適用することができます、`AutoOpen`アセンブリに属性をアセンブリが参照されている場合に、名前空間またはモジュールを自動的に開きたい場合。 適用することも、`AutoOpen`属性の親モジュールまたは名前空間が開かれるときに、そのモジュールを自動的に開くモジュールにします。 詳細については、次を参照してください。 [Core.AutoOpenAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)です。


## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 属性
いくつかのモジュール、レコード、または共用体の型を指定することがあります、`RequireQualifiedAccess`属性。 これらのモジュール、レコード、または共用体の要素を参照する場合は、インポート宣言を含めるかどうかに関係なく、修飾名を使用する必要があります。 この属性を戦略的に使用する場合は、よくを定義する型名が使用されて、おけば名前の衝突を回避し、それによってコード回復力を高めるライブラリの変更にします。 詳細については、次を参照してください。 [Core.RequireQualifiedAccessAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)です。


## <a name="see-also"></a>関連項目
[# 言語リファレンス](index.md)

[名前空間](namespaces.md)

[モジュール](modules.md)

