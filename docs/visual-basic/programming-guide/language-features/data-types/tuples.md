---
title: "Visual Basic での組"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
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

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

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
