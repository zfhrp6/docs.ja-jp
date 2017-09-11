---
title: "方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="0c26e-102">方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加</span><span class="sxs-lookup"><span data-stu-id="0c26e-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="0c26e-103">LINQ クエリを使用する拡張メソッドを追加することでメソッドのセットを拡張する、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="0c26e-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="0c26e-104">たとえば、だけでなく、標準的な平均または操作の最大数は、値のシーケンスから単一の値を計算する場合は、カスタム集計メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="0c26e-105">カスタム フィルターまたは一連の値の変換を特定のデータとして機能し、新しいシーケンスを返すメソッドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="0c26e-106">このようなメソッドの例としては<xref:System.Linq.Enumerable.Distinct%2A>、 <xref:System.Linq.Enumerable.Skip%2A>、 <xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A></span><span class="sxs-lookup"><span data-stu-id="0c26e-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="0c26e-107">拡張すると、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、列挙可能なコレクションにカスタム メソッドを適用することができます</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="0c26e-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="0c26e-108">詳細については、次を参照してください。[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="0c26e-109">集計メソッドの追加</span><span class="sxs-lookup"><span data-stu-id="0c26e-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="0c26e-110">集計メソッドは、一連の値から単一の値を計算します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="0c26e-111">LINQ を含むいくつかの集計メソッドを提供する<xref:System.Linq.Enumerable.Average%2A>、 <xref:System.Linq.Enumerable.Min%2A>、 <xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A></span><span class="sxs-lookup"><span data-stu-id="0c26e-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="0c26e-112">拡張メソッドを追加することで、独自の集計メソッドを作成することができます、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="0c26e-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="0c26e-113">次のコード例は、という拡張メソッドを作成する方法を示しています。`Median`型の数値のシーケンスの中央値を計算する`double`です。</span><span class="sxs-lookup"><span data-stu-id="0c26e-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 <span data-ttu-id="0c26e-114">他の集計メソッドを呼び出すのと同じ方法で、列挙可能なコレクションに対してこの拡張メソッドを呼び出す、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="0c26e-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c26e-115">Visual Basic ではできますか、または使用するメソッドの呼び出しの標準的なクエリ構文、`Aggregate`または`Group By`句。</span><span class="sxs-lookup"><span data-stu-id="0c26e-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="0c26e-116">詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="0c26e-117">次のコード例を使用する方法を示しています、`Median`型の配列をメソッド`double`します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
<span data-ttu-id="0c26e-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-118"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="0c26e-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-119"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="0c26e-120">さまざまな種類をそのまま使用する集計メソッドのオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="0c26e-120">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="0c26e-121">さまざまな種類のシーケンスを受け入れるように、集計メソッドをオーバー ロードできます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-121">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="0c26e-122">標準的なアプローチでは、各種類のオーバー ロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-122">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="0c26e-123">別の方法では、ジェネリック型を受け取るはデリゲートを使用して、特定の種類に変換するオーバー ロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-123">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="0c26e-124">どちらの方法を組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-124">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="0c26e-125">各種類のオーバー ロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="0c26e-125">To create an overload for each type</span></span>  
 <span data-ttu-id="0c26e-126">サポートする各種類の特定のオーバー ロードを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-126">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="0c26e-127">次のコード例のオーバー ロードを示しています、`Median`のメソッド、`integer`型です。</span><span class="sxs-lookup"><span data-stu-id="0c26e-127">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
<span data-ttu-id="0c26e-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-128"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="0c26e-129">呼び出せるように、`Median`両方のオーバー ロード`integer`と`double`型の場合、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="0c26e-129">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
<span data-ttu-id="0c26e-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-130"><CodeContentPlaceHolder>4</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="0c26e-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-131"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
<span data-ttu-id="0c26e-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-132"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="0c26e-133">ジェネリック オーバー ロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="0c26e-133">To create a generic overload</span></span>  
 <span data-ttu-id="0c26e-134">汎用オブジェクトのシーケンスを受け入れるオーバー ロードを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-134">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="0c26e-135">このオーバー ロードは、パラメーターとしてデリゲートを受け取るし、それを使用してジェネリック型のオブジェクトのシーケンスを特定の種類に変換します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-135">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="0c26e-136">次のコードはのオーバー ロード、`Median`を受け取るメソッド、<xref:System.Func%602>をパラメーターとしてデリゲートします</xref:System.Func%602>。</span><span class="sxs-lookup"><span data-stu-id="0c26e-136">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="0c26e-137">このデリゲートがジェネリック型 T のオブジェクトを受け取るし、型のオブジェクトを返します`double`します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-137">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="0c26e-138">呼び出せるように、`Median`任意の型のオブジェクトの順序のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="0c26e-138">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="0c26e-139">型が、独自のメソッド オーバー ロードを持たない場合に、デリゲートのパラメーターを渡す必要あります。</span><span class="sxs-lookup"><span data-stu-id="0c26e-139">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="0c26e-140">Visual basic では、この目的のため、ラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-140">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="0c26e-141">また、使用する場合、`Aggregate`または`Group By`句メソッドの呼び出しではなく、任意の値またはこの句は、スコープ内の式を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-141">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="0c26e-142">次のコード例を呼び出す方法を示します、`Median`方法の整数の配列と文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="0c26e-142">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="0c26e-143">文字列の場合は、配列内の文字列の長さの中央値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-143">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="0c26e-144">渡す方法の例、<xref:System.Func%602>にパラメーターをデリゲート、`Median`各ケースのメソッドです</xref:System.Func%602>。</span><span class="sxs-lookup"><span data-stu-id="0c26e-144">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
<span data-ttu-id="0c26e-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-145"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="0c26e-146">コレクションを返すメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-146">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="0c26e-147">拡張する、<xref:System.Collections.Generic.IEnumerable%601>を一連の値を返すカスタム クエリ メソッドを持つインターフェイスです</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="0c26e-147">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="0c26e-148">この場合、メソッドが型<xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>のコレクションを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c26e-148">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="0c26e-149">値のシーケンスをフィルターまたはデータ変換を適用するのには、このようなメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c26e-149">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="0c26e-150">次の例は、という名前の拡張メソッドを作成する方法を示しています。`AlternateElements`最初の要素を起点として、コレクション内のその他のすべての要素を返します。</span><span class="sxs-lookup"><span data-stu-id="0c26e-150">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
<span data-ttu-id="0c26e-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="0c26e-151"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="0c26e-152">他のメソッドを呼び出すと同様に、列挙可能なコレクションに対してこの拡張メソッドを呼び出すことができます、<xref:System.Collections.Generic.IEnumerable%601>次のコードに示すように、インターフェイス:</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="0c26e-152">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c26e-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c26e-153">See Also</span></span>  
 <span data-ttu-id="0c26e-154"><xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="0c26e-154"><xref:System.Collections.Generic.IEnumerable%601></span></span>   
<span data-ttu-id="0c26e-155"> [拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="0c26e-155"> [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)</span></span>
