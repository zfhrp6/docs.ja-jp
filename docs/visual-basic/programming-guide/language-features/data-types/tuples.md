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
# <a name="tuples-visual-basic"></a><span data-ttu-id="daf8f-102">タプル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daf8f-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="daf8f-103">Visual Basic 言語では、組の組み込みサポートを Visual Basic 2017 から始めて、組を作成して、簡単に組の要素へのアクセスします。</span><span class="sxs-lookup"><span data-stu-id="daf8f-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="daf8f-104">組は、特定の数と一連の値を持つ軽量のデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="daf8f-105">組をインスタンス化するときは、数および各値 (または要素) のデータ型を定義します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="daf8f-106">たとえば、2 タプル (またはペア) には、次の 2 つの要素があります。</span><span class="sxs-lookup"><span data-stu-id="daf8f-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="daf8f-107">最初の可能性があります、 `Boolean` 、2 番目の値、`String`です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="daf8f-108">組を簡単に 1 つのオブジェクトに複数の値を格納する、ため、メソッドから複数の値を返す軽量な方法としてよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="daf8f-109">組のサポートが必要です、<xref:System.ValueTuple>型です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="daf8f-110">.NET Framework 4.7 がインストールされていない場合は、NuGet パッケージを追加する必要があります`System.ValueTuple`、これは NuGet ギャラリーで使用できます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="daf8f-111">このパッケージなし可能性がありますエラーが発生したコンパイルと同様、"定義済みの型 'ValueTuple(Of,,,)' は定義されている、またはインポートされていません"</span><span class="sxs-lookup"><span data-stu-id="daf8f-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="daf8f-112">インスタンス化して、組を使用します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="daf8f-113">組をインスタンス化するには、外側のコンマで区切られた値 im かっこ。</span><span class="sxs-lookup"><span data-stu-id="daf8f-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="daf8f-114">これらの値の各、タプルのフィールドになります。</span><span class="sxs-lookup"><span data-stu-id="daf8f-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="daf8f-115">次のコードが 3 回 (または 3 組) を定義するなど、`Date`その最初の値として、`String`として、2 番目と`Boolean`3 つ目として。</span><span class="sxs-lookup"><span data-stu-id="daf8f-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="daf8f-116">既定では、タプル内の各フィールドの名前から成る文字列`Item`と共に、組内のフィールドの 1 から始まる位置。</span><span class="sxs-lookup"><span data-stu-id="daf8f-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="daf8f-117">この 3 組の`Date`フィールドは`Item1`、`String`フィールドは`Item2`、および`Boolean`フィールドは`Item3`します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="daf8f-118">次の例には、前のコード行でインスタンス化される組のフィールドの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="daf8f-119">Visual Basic の組のフィールドには、読み取り/書き込みです。組をインスタンス化した後は、その値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="daf8f-120">次の例では、前の例で作成される組の 3 つのフィールドの 2 つを変更し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="daf8f-121">インスタンス化して、名前付きの組を使用します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="daf8f-122">組のフィールドの既定の名前を使用することができますをインスタンス化する、*組を名前付き*タプルの要素に独自の名前を割り当てることで。</span><span class="sxs-lookup"><span data-stu-id="daf8f-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="daf8f-123">組のフィールドの割り当てられた名前でアクセスできます*または*によって既定の名前。</span><span class="sxs-lookup"><span data-stu-id="daf8f-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="daf8f-124">次の例の最初のフィールドを明示的に指定する点を除いて前と同じ 3 組がインスタンス化`EventDate`、2 番目`Name`、3 番目の`IsHoliday`します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="daf8f-125">フィールド値を表示、それらを変更し、フィールドの値が再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="daf8f-126">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="daf8f-126">Inferred tuple element names</span></span>

<span data-ttu-id="daf8f-127">Visual Basic 15.3 から始めて、Visual Basic はタプル要素の名前を推論できます。明示的に割り当てる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="daf8f-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="daf8f-128">推論される組の名前は、変数のセットから組を初期化して、タプルの要素名、変数名と同じであるをする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="daf8f-129">次の例を作成、`stateInfo`を明示的に 3 つを含むタプル要素を名前付き`state`、 `stateName`、および`capital`です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="daf8f-130">なお、要素の名前付けで、タプルの初期化ステートメントが同じ名前の変数の値だけで名前付きの要素に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="daf8f-131">要素と変数は、同じ名前であるために、Visual Basic コンパイラは、次の例のように、フィールドの名前を推測できます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="daf8f-132">Interred タプル要素の名前を有効にするには、Visual Basic プロジェクトで使用する Visual Basic コンパイラのバージョンを定義する必要があります (\*.vbproj) ファイル。</span><span class="sxs-lookup"><span data-stu-id="daf8f-132">To enable interred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

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

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="daf8f-133">メソッドの戻り値としてのタプル</span><span class="sxs-lookup"><span data-stu-id="daf8f-133">Tuples as method return values</span></span>

<span data-ttu-id="daf8f-134">メソッドは、単一の値のみを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-134">A method can return only a single value.</span></span> <span data-ttu-id="daf8f-135">多くの場合、ただし、たいメソッドの呼び出しを複数の値を返します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-135">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="daf8f-136">これにはこの制限を回避するいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="daf8f-136">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="daf8f-137">または作成できますカスタム クラスまたは構造体プロパティを持つフィールドは、メソッドによって返される値を表します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-137">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="daf8f-138">したがって、重いソリューションです。メソッドの呼び出しから値を取得するが唯一の目的は、カスタムの型を定義することが必要です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-138">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="daf8f-139">メソッドから単一の値を返すし、メソッドへの参照で渡すことによって、残りの値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-139">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="daf8f-140">これには、変数と参照渡しで渡された変数の値を上書きしてしまうリスクをインスタンス化のオーバーヘッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-140">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="daf8f-141">複数の戻り値を取得する簡易ソリューションを提供する組を使用できます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-141">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="daf8f-142">たとえば、 **TryParse** .NET の戻り値のメソッド、`Boolean`解析操作が成功したかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="daf8f-142">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="daf8f-143">メソッドへの参照によって渡された変数には、解析操作の結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-143">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="daf8f-144">呼び出しでは通常などの解析方法<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>次のようになります。</span><span class="sxs-lookup"><span data-stu-id="daf8f-144">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="daf8f-145">呼び出しをラップしている場合、解析操作から組を返すおことができます、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>独自のメソッドのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="daf8f-145">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="daf8f-146">次の例では、`NumericLibrary.ParseInteger`呼び出し、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>メソッドを 2 つの要素と名前付きの組を返します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-146">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="daf8f-147">次のようにコードを持つメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-147">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="daf8f-148">Visual Basic の組と、.NET Framework 内の組</span><span class="sxs-lookup"><span data-stu-id="daf8f-148">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="daf8f-149">Visual Basic 組の 1 つのインスタンスとは、 **System.ValueTuple** 、.NET Framework 4.7 で導入されたジェネリック型です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-149">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="daf8f-150">.NET Framework は、汎用のセットも含まれています。 **System.Tuple**クラスです。</span><span class="sxs-lookup"><span data-stu-id="daf8f-150">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="daf8f-151">ただし、これらのクラスが Visual Basic の組から異なると、 **System.ValueTuple**さまざまな方法でジェネリック型。</span><span class="sxs-lookup"><span data-stu-id="daf8f-151">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="daf8f-152">要素、**組**クラスという名前のプロパティは、 `Item1`、`Item2`のようにします。</span><span class="sxs-lookup"><span data-stu-id="daf8f-152">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="daf8f-153">Visual Basic の組にし、 **ValueTuple**型、タプル要素はフィールドです。</span><span class="sxs-lookup"><span data-stu-id="daf8f-153">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="daf8f-154">要素にはわかりやすい名前を割り当てることはできません、**組**インスタンスであるかの**ValueTuple**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="daf8f-154">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="daf8f-155">Visual Basic を使用すると、フィールドの意味を通信する名前を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="daf8f-155">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="daf8f-156">プロパティ、**組**インスタンスは読み取り専用です。 組は変更できません。</span><span class="sxs-lookup"><span data-stu-id="daf8f-156">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="daf8f-157">Visual Basic の組にし、 **ValueTuple**型、タプルのフィールドは読み取り/書き込み以外の場合は、組は変更可能です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-157">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="daf8f-158">ジェネリック**組**型は、参照型です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-158">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="daf8f-159">これらを使用して**組**型のオブジェクトを割り当てることを意味します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-159">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="daf8f-160">ホット パスでは、これがアプリケーションのパフォーマンスに大きな影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="daf8f-160">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="daf8f-161">Visual Basic の組と**ValueTuple**型は値型です。</span><span class="sxs-lookup"><span data-stu-id="daf8f-161">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="daf8f-162">拡張メソッドにおいて、<xref:System.TupleExtensions>クラスしやすいように Visual Basic の組と .NET の間で変換**組**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="daf8f-162">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="daf8f-163">**ToTuple**メソッドは、Visual Basic の組を .NET に変換します**組**オブジェクト、および**ToValueTuple**メソッドは、.NET、変換**組**Visual Basic 組オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="daf8f-163">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="daf8f-164">次の例は、タプルを作成、.NET に変換します**組**オブジェクト、および Visual Basic の組に戻します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-164">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="daf8f-165">例は、それらが等しいことを確認するのには、元の名前を持つこのタプルを比較します。</span><span class="sxs-lookup"><span data-stu-id="daf8f-165">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="daf8f-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="daf8f-166">See also</span></span>

[<span data-ttu-id="daf8f-167">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="daf8f-167">Visual Basic Language Reference</span></span>](index.md)  
