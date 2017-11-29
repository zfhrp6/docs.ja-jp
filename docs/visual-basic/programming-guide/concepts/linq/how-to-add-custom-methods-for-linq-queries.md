---
title: "方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c94973bf9eae0feb2f7690dcc10e839b6b7c060c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="42c14-102">方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加</span><span class="sxs-lookup"><span data-stu-id="42c14-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="42c14-103"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで、LINQ クエリに使用できるメソッド セットを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="42c14-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="42c14-104">たとえば一連の値から単一の値を求めるために、平均値や最大値を求める標準的な演算に加えて、独自の集計メソッドを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="42c14-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="42c14-105">また、一連の値を受け取って別の一連の値を返す特定のデータ変換やカスタム フィルターの働きを持ったメソッドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="42c14-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="42c14-106">このようなメソッドには、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A>、<xref:System.Linq.Enumerable.Reverse%2A> があります。</span><span class="sxs-lookup"><span data-stu-id="42c14-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="42c14-107"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスを拡張すると、列挙可能なコレクションにカスタム メソッドを適用できます。</span><span class="sxs-lookup"><span data-stu-id="42c14-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="42c14-108">詳細については、「[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42c14-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="42c14-109">集計メソッドの追加</span><span class="sxs-lookup"><span data-stu-id="42c14-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="42c14-110">集計メソッドは、一連の値から単一の値を計算するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="42c14-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="42c14-111">LINQ は、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Max%2A> などの集計メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="42c14-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="42c14-112"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで、独自の集計メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="42c14-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="42c14-113">次のコード例は、`double` 型の一連の数値から中央値を求める `Median` という拡張メソッドの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="42c14-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="42c14-114">この拡張メソッドは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他の集計メソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="42c14-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42c14-115">Visual basic でことができますか、またはを使用するメソッドを呼び出すのための標準的なクエリ構文、`Aggregate`または`Group By`句。</span><span class="sxs-lookup"><span data-stu-id="42c14-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="42c14-116">詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="42c14-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="42c14-117">`double` 型の配列に対して `Median` メソッドを使用する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="42c14-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
```  
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="42c14-118">さまざまな型を受け取るために集計メソッドをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="42c14-118">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="42c14-119">集計メソッドでさまざまな型を受け取るように、集計メソッドをオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="42c14-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="42c14-120">その標準的な方法として、型ごとにオーバーロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="42c14-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="42c14-121">または、ジェネリック型を受け取り、デリゲートを使って特定の型に変換するオーバーロードを作成する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="42c14-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="42c14-122">その両方の方法を組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="42c14-122">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="42c14-123">型ごとにオーバーロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="42c14-123">To create an overload for each type</span></span>  
 <span data-ttu-id="42c14-124">サポート予定の型ごとに固有のオーバーロードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="42c14-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="42c14-125">次のコード例では、`integer` 型の `Median` メソッドのオーバーロードを示します。</span><span class="sxs-lookup"><span data-stu-id="42c14-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 <span data-ttu-id="42c14-126">これで、次のコードに示すように、`integer` 型と `double` 型の両方に対して、`Median` のオーバーロードを呼び出すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="42c14-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
Dim numbers2() As Integer = {1, 2, 3, 4, 5}  
  
Dim query2 = Aggregate num In numbers2 Into Median()  
  
Console.WriteLine("Integer: Median = " & query2)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
' Integer: Median = 3  
```  
  
 
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="42c14-127">ジェネリック オーバーロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="42c14-127">To create a generic overload</span></span>  
 <span data-ttu-id="42c14-128">一連のジェネリック オブジェクトを受け取るオーバーロードを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="42c14-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="42c14-129">このオーバーロードは、デリゲートをパラメーターとして受け取り、ジェネリック型の一連のオブジェクトを特定の型に変換します。</span><span class="sxs-lookup"><span data-stu-id="42c14-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="42c14-130">次のコードは、<xref:System.Func%602> デリゲートをパラメーターとして受け取る `Median` メソッドのオーバーロードを示しています。</span><span class="sxs-lookup"><span data-stu-id="42c14-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="42c14-131">このデリゲートは、ジェネリック型 T のオブジェクトを受け取り、`double` 型のオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="42c14-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="42c14-132">これで、任意の型の一連のオブジェクトに対して `Median` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="42c14-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="42c14-133">型に固有のメソッド オーバーロードがない場合は、デリゲート パラメーターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="42c14-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="42c14-134">Visual basic では、この目的のため、ラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="42c14-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="42c14-135">また、使用する場合、`Aggregate`または`Group By`メソッドの呼び出しではなく句は、任意の値またはスコープ内にあるこの句の式を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="42c14-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="42c14-136">次のコード例では、整数の配列と文字列の配列に対して `Median` メソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="42c14-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="42c14-137">文字列の場合は、配列に格納されている文字列の長さの中央値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="42c14-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="42c14-138">この例は、それぞれのケースについて、`Median` メソッドに <xref:System.Func%602> デリゲート パラメーターを渡す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="42c14-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
```vb  
Dim numbers3() As Integer = {1, 2, 3, 4, 5}  
  
' You can use num as a parameter for the Median method   
' so that the compiler will implicitly convert its value to double.  
' If there is no implicit conversion, the compiler will  
' display an error message.  
  
Dim query3 = Aggregate num In numbers3 Into Median(num)  
  
Console.WriteLine("Integer: Median = " & query3)  
  
Dim numbers4() As String = {"one", "two", "three", "four", "five"}  
  
' With the generic overload, you can also use numeric properties of objects.  
  
Dim query4 = Aggregate str In numbers4 Into Median(str.Length)  
  
Console.WriteLine("String: Median = " & query4)  
  
' This code produces the following output:  
'  
' Integer: Median = 3  
' String: Median = 4  
```  
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="42c14-139">コレクションを返すメソッドを追加する</span><span class="sxs-lookup"><span data-stu-id="42c14-139">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="42c14-140"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスは、一連の値を返すカスタム クエリ メソッドを追加することで拡張できます。</span><span class="sxs-lookup"><span data-stu-id="42c14-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="42c14-141">その場合、メソッドで型 <xref:System.Collections.Generic.IEnumerable%601> のコレクションを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="42c14-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="42c14-142">このようなメソッドを使用すると、一連の値にフィルターまたはデータ変換を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="42c14-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="42c14-143">次の例では、コレクション内の最初の要素から 1 つおきに要素を返す `AlternateElements` という名前の拡張メソッドを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="42c14-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
```vb  
' Extension method for the IEnumerable(of T) interface.   
' The method returns every other element of a sequence.  
  
<Extension()>   
Function AlternateElements(Of T)(  
    ByVal source As IEnumerable(Of T)  
    ) As IEnumerable(Of T)  
  
    Dim list As New List(Of T)  
    Dim i = 0  
    For Each element In source  
        If (i Mod 2 = 0) Then  
            list.Add(element)  
        End If  
        i = i + 1  
    Next  
    Return list  
End Function  
```  
 <span data-ttu-id="42c14-144">この拡張メソッドは、次のコードに示すとおり、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他のメソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="42c14-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42c14-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="42c14-145">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="42c14-146">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="42c14-146">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
