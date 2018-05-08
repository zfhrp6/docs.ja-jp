---
title: 属性 (F#)
description: F# の属性がプログラミング構成要素に適用するメタデータを有効にする方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 107f5d9cbcce28c97fc5b738759ef27649fc45a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="attributes"></a>属性

属性は、プログラミング構成要素に適用するメタデータを有効にします。

## <a name="syntax"></a>構文

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>コメント

前の構文では、*ターゲット*を省略して、存在する場合は、属性が適用されるプログラム エンティティの種類を指定します。 有効な値*ターゲット*このドキュメントの後半に示す表に示します。

*属性名*またはサフィックスがない場合、有効な属性型の名前 (場合によっては名前空間を持つ修飾名) を指す`Attribute`属性の型名で通常使用されます。 たとえば、型`ObsoleteAttribute`だけに簡略化`Obsolete`このコンテキストでします。

*引数*属性の型のコンス トラクターの引数します。 属性に既定のコンス トラクターがある場合、引数リストとかっこを省略できます。 属性は、位置指定引数と名前付き引数の両方をサポートします。 *位置指定引数*が出現する順序で使用される引数。 属性にパブリック プロパティが設定されている場合、名前付き引数を使用できます。 引数リストで、次の構文を使用して、これらを設定することができます。

```
*property-name* = *property-value*
```

このようなプロパティの初期化は、任意の順序で指定できますが、任意の位置指定引数に従う必要があります。 位置指定引数とプロパティの初期化を使用する属性の使用例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

属性は、この例では`DllImportAttribute`、ここで短縮形で使用します。 最初の引数が位置指定パラメーターで、2 番目はプロパティです。

属性は、.NET プログラミング構成要素と呼ばれるオブジェクトをできるようにする、*属性*型またはその他のプログラム要素に関連付ける。 属性が適用されるプログラム要素と呼ばれる、*属性ターゲット*です。 通常、属性には、そのターゲットに関するメタデータが含まれます。 このコンテキストでのメタデータにそのフィールドとメンバー以外の型に関するデータが可能性があります。

F# の属性は、次のプログラミング構成要素に適用できます: 関数、メソッド、アセンブリ、モジュール、型 (クラス、レコード、構造体、インターフェイス、デリゲート、列挙体、共用体、およびなど)、コンス トラクター、プロパティ、フィールド、パラメーター、パラメーターを入力し、値を返します。 属性が許可されていない`let`クラス、式、またはワークフローの式内のバインド。

通常、属性の宣言には、属性のターゲットの宣言の直前が表示されます。 同時に、次のように、複数の属性の宣言を使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

.NET リフレクションを使用して、実行時に属性を照会できます。

前のコード例では、個別に、複数の属性を宣言することができます。 またはでも宣言できます角かっこの 1 つのセットに次のように、個々 の属性と、コンス トラクターを分離する、セミコロンを使用する場合。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

属性によく発生、`Obsolete`属性、セキュリティに関する考慮事項については、属性の COM サポート、コードの所有権に関連する属性および属性の型をシリアル化できるかどうかを示す属性です。 次の例での使用、`Obsolete`属性。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

属性の対象の`assembly`と`module`、最上位に属性を適用する`do`アセンブリにバインドします。 単語を含めることができます`assembly`または`module`属性宣言で、次のようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

適用する属性の属性のターゲットを省略したかどうか、`do`バインド、その属性の意味のある属性ターゲットを特定しようと試みます、f# コンパイラです。 多くの属性クラスは、型の属性を持つ`System.AttributeUsageAttribute`その属性のサポート可能なターゲットに関する情報を含むです。 場合、`System.AttributeUsageAttribute`属性には、ターゲットとしての関数がサポートされています、プログラムのメイン エントリ ポイントに適用する属性が作成されたことを示します。 場合、`System.AttributeUsageAttribute`ことを示す属性がアセンブリをターゲットとしてをサポートしている、コンパイラはアセンブリに適用する属性を取得します。 関数と、アセンブリの両方にほとんどの属性は適用されませんが、プログラムの main 関数に適用する場合で属性が実行されます。 属性ターゲットが明示的に指定されている場合は、属性が、指定したターゲットに適用されます。

属性がターゲットの有効な値で明示的に、通常を指定する必要はありませんが*ターゲット*属性での使用例と、次の表で表示されます。

<table>
  <tr>
    <th>属性ターゲット</td>
    <th>例</td> 
  </tr>
  <tr>
    <td>アセンブリ</td>
    <td>`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</td> 
  </tr>
  <tr>
    <td>return</td>
    <td>' function1 を x: [<return: Obsolete>] int = x + 1'</td> 
  </tr>
  <tr>
    <td>フィールド</td>
    <td>' [<field: DefaultValue>] val mutable x: int'</td> 
  </tr>
  <tr>
    <td>property</td>
    <td>' [<property: Obsolete>] このです。MyProperty = x'</td> 
  </tr>
  <tr>
    <td>Param</td>
    <td>' メンバーこれです。MyMethod ([<param: Out>] x: ref<int>) = x: = 10'</td> 
  </tr>
  <tr>
    <td>型</td>
    <td>
        ```
        [<type: StructLayout(Sequential)>入力は構造体を = x: バイト y: int 終了 ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>関連項目

[F# 言語リファレンス](index.md)
