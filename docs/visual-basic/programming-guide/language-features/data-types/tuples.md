---
title: Visual Basic での組
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b2c8205dd413b1749d181daa8d0e84d62534e28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="tuples-visual-basic"></a>タプル (Visual Basic)

Visual Basic 言語では、組の組み込みサポートを Visual Basic 2017 から始めて、組を作成して、簡単に組の要素へのアクセスします。 組は、特定の数と一連の値を持つ軽量のデータ構造です。 組をインスタンス化するときは、数および各値 (または要素) のデータ型を定義します。 たとえば、2 タプル (またはペア) には、次の 2 つの要素があります。 最初の可能性があります、 `Boolean` 、2 番目の値、`String`です。 組を簡単に 1 つのオブジェクトに複数の値を格納する、ため、メソッドから複数の値を返す軽量な方法としてよく使用されます。

> [!IMPORTANT]
> 組のサポートが必要です、<xref:System.ValueTuple>型です。 .NET Framework 4.7 がインストールされていない場合は、NuGet パッケージを追加する必要があります`System.ValueTuple`、これは NuGet ギャラリーで使用できます。 このパッケージなし可能性がありますエラーが発生したコンパイルと同様、"定義済みの型 'ValueTuple(Of,,,)' は定義されている、またはインポートされていません"

## <a name="instantiating-and-using-a-tuple"></a>インスタンス化して、組を使用します。

組をインスタンス化するには、外側のコンマで区切られた値 im かっこ。 これらの値の各、タプルのフィールドになります。 次のコードが 3 回 (または 3 組) を定義するなど、`Date`その最初の値として、`String`として、2 番目と`Boolean`3 つ目として。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

既定では、タプル内の各フィールドの名前から成る文字列`Item`と共に、組内のフィールドの 1 から始まる位置。 この 3 組の`Date`フィールドは`Item1`、`String`フィールドは`Item2`、および`Boolean`フィールドは`Item3`します。 次の例には、前のコード行でインスタンス化される組のフィールドの値が表示されます。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Visual Basic の組のフィールドには、読み取り/書き込みです。組をインスタンス化した後は、その値を変更できます。 次の例では、前の例で作成される組の 3 つのフィールドの 2 つを変更し、結果を表示します。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>インスタンス化して、名前付きの組を使用します。

組のフィールドの既定の名前を使用することができますをインスタンス化する、*組を名前付き*タプルの要素に独自の名前を割り当てることで。 組のフィールドの割り当てられた名前でアクセスできます*または*によって既定の名前。 次の例の最初のフィールドを明示的に指定する点を除いて前と同じ 3 組がインスタンス化`EventDate`、2 番目`Name`、3 番目の`IsHoliday`します。 フィールド値を表示、それらを変更し、フィールドの値が再び表示されます。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>推論されたタプル要素の名前

Visual Basic 15.3 から始めて、Visual Basic はタプル要素の名前を推論できます。明示的に割り当てる必要はありません。 推論される組の名前は、変数のセットから組を初期化して、タプルの要素名、変数名と同じであるをする場合に便利です。 

次の例を作成、`stateInfo`を明示的に 3 つを含むタプル要素を名前付き`state`、 `stateName`、および`capital`です。 なお、要素の名前付けで、タプルの初期化ステートメントが同じ名前の変数の値だけで名前付きの要素に割り当てられます。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
要素と変数は、同じ名前であるために、Visual Basic コンパイラは、次の例のように、フィールドの名前を推測できます。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Interred タプル要素の名前を有効にするには、Visual Basic プロジェクトで使用する Visual Basic コンパイラのバージョンを定義する必要があります (\*.vbproj) ファイル。 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

バージョン番号は、以降 15.3 で Visual Basic コンパイラの任意のバージョンを指定できます。 特定のコンパイラ バージョンをハードコーディングするのではなく指定することも「最新」の値として`LangVersion`システムにインストールされている Visual Basic コンパイラの最新バージョンでコンパイルしますします。

Visual Basic コンパイラは場合によっては、候補名からタプル要素名を生成することはできませんなどを使用して、既定の名前は、組のフィールドを参照のみ`Item1`、 `Item2`, などです。次の設定があります。

- 候補名は、組のメンバーの名前と同じように`Item3`、 `Rest`、または`ToString`です。

- 名前の候補が、組で重複しています。
 
フィールド名の推定が失敗すると、Visual Basic コンパイラ エラーを生成しませんも実行時にスローされる例外。 代わりに、組フィールド参照が必要、定義済みの名前によってなど`Item1`と`Item2`です。 
  
## <a name="tuples-versus-structures"></a>組構造体との比較

Visual Basic の組が値型の 1 つのインスタンスでは、 **System.ValueTuple**ジェネリック型です。 たとえば、`holiday`前の例で定義される組がのインスタンス、<xref:System.ValueTuple%603>構造体。 軽量のデータ コンテナーに設計されています。 組の目的は、複数のデータ項目を含むオブジェクトを作成するが簡単に、ため、可能性のあるカスタム構造機能の一部が不足しています。 次の設定があります。

- カスタム メンバー。 独自のプロパティ、メソッド、または組のイベントを定義することはできません。

- 検証します。 フィールドに割り当てられているデータを検証することはできません。

- 不変性。 Visual Basic の組は変更可能です。 これに対し、カスタムの構造を制御できますインスタンスには変更可能なと変更できないかどうか。

カスタム メンバー、プロパティとフィールドの検証、または変更不可が重要な場合は、Visual Basic を使用する必要があります[構造](../../../language-reference/statements/structure-statement.md)をカスタム値の型を定義するステートメント。

Visual Basic の組のメンバーを継承してその**ValueTuple**型です。 そのフィールドに加え、次のメソッドが含まれます。

| メンバー | 説明 |
| ---|---|
| CompareTo | 同じ数の要素を持つ別のタプルに現在の組を比較します。 |
| 次の値に等しい | 現在の組が別の組またはオブジェクトに等しいかどうかを判断します。 |
| GetHashCode | 現在のインスタンスのハッシュ コードを計算します。 |
| ToString | この組は、の形式の文字列表現を返します`(Item1, Item2...)`ここで、`Item1`と`Item2`組のフィールドの値を表します。 |

さらに、 **ValueTuple**型実装<xref:System.Collections.IStructuralComparable>と<xref:System.Collections.IStructuralEquatable>インターフェイスで、顧客の比較子を定義することです。

## <a name="assignment-and-tuples"></a>割り当てとタプル

Visual Basic では、同じ数のフィールドを持つタプル型間での割り当てをサポートします。 次のいずれかが true の場合、フィールドの型を変換できます。

- ソースとターゲットのフィールドでは、同じ型です。

- 対象の型に、元の型の拡大 (または暗黙的な) 変換が定義されます。 

- `Option Strict` `On`対象の型に、元の型の縮小 (または明示的な) 変換が定義されているとします。 この変換は、元の値がターゲット型の範囲外の場合、例外をスローできます。

他の変換は、割り当てでは考慮されません。 タプル型間で許可されている割り当ての種類を見てみましょう。

以降の例で使用されている変数について考えます。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

最初の 2 つの変数では、`unnamed`と`anonymous`フィールドのセマンティックの名がありません。 フィールド名は、既定`Item1`と`Item2`です。 最後の 2 つの変数では、`named`と`differentName`セマンティック フィールド名があります。 この 2 つのタプルでは、フィールド名が異なっていることに注意してください。

これらの組の 4 つすべては同じ数のフィールド (呼ば 'アリティ') を持ち、これらのフィールドの型が同一です。 このため、これらの割り当てはすべて機能します。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

タプルの名前が割り当てられていないことに注意してください。 フィールドの値は、タプルのフィールドの順序に従って割り当てられます。

最後は割り当てることができますに注意してください、`named`タプル、`conversion`タプル、にもかかわらずの最初のフィールド`named`は、`Integer`との最初のフィールド`conversion`は、`Long`です。 変換するため、この割り当てが成功、`Integer`を`Long`拡大変換は、します。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

フィールドの数が異なるとの組に割り当てることはできません。

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>メソッドの戻り値としてのタプル

メソッドは、単一の値のみを返すことができます。 多くの場合、ただし、たいメソッドの呼び出しを複数の値を返します。 これにはこの制限を回避するいくつかの方法があります。

- または作成できますカスタム クラスまたは構造体プロパティを持つフィールドは、メソッドによって返される値を表します。 したがって、重いソリューションです。メソッドの呼び出しから値を取得するが唯一の目的は、カスタムの型を定義することが必要です。

- メソッドから単一の値を返すし、メソッドへの参照で渡すことによって、残りの値を返すことができます。 これには、変数と参照渡しで渡された変数の値を上書きしてしまうリスクをインスタンス化のオーバーヘッドが含まれます。

- 複数の戻り値を取得する簡易ソリューションを提供する組を使用できます。

たとえば、 **TryParse** .NET の戻り値のメソッド、`Boolean`解析操作が成功したかどうかを示す値。 メソッドへの参照によって渡された変数には、解析操作の結果が返されます。 呼び出しでは通常などの解析方法<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>次のようになります。

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

呼び出しをラップしている場合、解析操作から組を返すおことができます、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>独自のメソッドのメソッドです。 次の例では、`NumericLibrary.ParseInteger`呼び出し、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>メソッドを 2 つの要素と名前付きの組を返します。 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

次のようにコードを持つメソッドを呼び出すことができます。

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic の組と、.NET Framework 内の組

Visual Basic 組の 1 つのインスタンスとは、 **System.ValueTuple** 、.NET Framework 4.7 で導入されたジェネリック型です。 .NET Framework は、汎用のセットも含まれています。 **System.Tuple**クラスです。 ただし、これらのクラスが Visual Basic の組から異なると、 **System.ValueTuple**さまざまな方法でジェネリック型。

- 要素、**組**クラスという名前のプロパティは、 `Item1`、`Item2`のようにします。 Visual Basic の組にし、 **ValueTuple**型、タプル要素はフィールドです。

- 要素にはわかりやすい名前を割り当てることはできません、**組**インスタンスであるかの**ValueTuple**インスタンス。 Visual Basic を使用すると、フィールドの意味を通信する名前を割り当てることができます。

- プロパティ、**組**インスタンスは読み取り専用です。 組は変更できません。 Visual Basic の組にし、 **ValueTuple**型、タプルのフィールドは読み取り/書き込み以外の場合は、組は変更可能です。

- ジェネリック**組**型は、参照型です。 これらを使用して**組**型のオブジェクトを割り当てることを意味します。 ホット パスでは、これがアプリケーションのパフォーマンスに大きな影響を及ぼすことがあります。 Visual Basic の組と**ValueTuple**型は値型です。

拡張メソッドにおいて、<xref:System.TupleExtensions>クラスしやすいように Visual Basic の組と .NET の間で変換**組**オブジェクト。 **ToTuple**メソッドは、Visual Basic の組を .NET に変換します**組**オブジェクト、および**ToValueTuple**メソッドは、.NET、変換**組**Visual Basic 組オブジェクト。

次の例は、タプルを作成、.NET に変換します**組**オブジェクト、および Visual Basic の組に戻します。 例は、それらが等しいことを確認するのには、元の名前を持つこのタプルを比較します。

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>関連項目

[Visual Basic の言語リファレンス](index.md)  
