---
title: "コレクション (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b3c8de3e22075d576f86bcd4eb599946740ebe16
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="collections-visual-basic"></a><span data-ttu-id="45265-102">コレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45265-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="45265-103">多くのアプリケーションで、関連するオブジェクトのグループの作成および管理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="45265-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="45265-104">オブジェクトをグループ化するには、オブジェクトの配列を作成する方法と、オブジェクトのコレクションを作成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="45265-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="45265-105">配列は、数が固定されている厳密に型指定されたオブジェクトの作成および処理に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="45265-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="45265-106">配列の概要については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="45265-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="45265-107">コレクションは、オブジェクトのグループをより柔軟に処理できます。</span><span class="sxs-lookup"><span data-stu-id="45265-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="45265-108">配列の場合とは違って、コレクションで扱うオブジェクトのグループは、アプリケーションの変更に伴う必要に応じて動的に拡大および縮小できます。</span><span class="sxs-lookup"><span data-stu-id="45265-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="45265-109">コレクションによっては、コレクションに含まれるオブジェクトのキーを割り当てると、そのキーを使用してオブジェクトを迅速に取り出すことができます。</span><span class="sxs-lookup"><span data-stu-id="45265-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="45265-110">コレクションはクラスであるため、そのコレクションに要素を追加するには、事前にそのクラスのインスタンスを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45265-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="45265-111">コレクションに&1; つのデータ型の要素が含まれている場合は、クラスでは、いずれかを使用、<xref:System.Collections.Generic?displayProperty=fullName>名前空間</xref:System.Collections.Generic?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="45265-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="45265-112">ジェネリック コレクションでは、タイプ セーフが強制されるため、他のデータ型を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="45265-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="45265-113">ジェネリック コレクションから要素を取得する場合は、データ型を判断したり、変換したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="45265-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45265-114">このトピックの例に、 [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントを`System.Collections.Generic`と`System.Linq`名前空間。</span><span class="sxs-lookup"><span data-stu-id="45265-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="45265-115">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="45265-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="45265-116">単純なコレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="45265-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="45265-117">コレクションの種類</span><span class="sxs-lookup"><span data-stu-id="45265-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="45265-118">System.Collections.Generic のクラス</span><span class="sxs-lookup"><span data-stu-id="45265-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="45265-119">System.Collections.Concurrent のクラス</span><span class="sxs-lookup"><span data-stu-id="45265-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="45265-120">System.Collections のクラス</span><span class="sxs-lookup"><span data-stu-id="45265-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="45265-121">Visual Basic のコレクション クラス</span><span class="sxs-lookup"><span data-stu-id="45265-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="45265-122">キー/値ペアのコレクションを実装します。</span><span class="sxs-lookup"><span data-stu-id="45265-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="45265-123">LINQ を使用して、コレクションにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="45265-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="45265-124">コレクションを並べ替える</span><span class="sxs-lookup"><span data-stu-id="45265-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="45265-125">カスタム コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="45265-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="45265-126">反復子</span><span class="sxs-lookup"><span data-stu-id="45265-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="45265-127">単純なコレクションを使用する</span><span class="sxs-lookup"><span data-stu-id="45265-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="45265-128">このセクションの例では、ジェネリックを使用して<xref:System.Collections.Generic.List%601>クラスで、この厳密に型指定されたオブジェクトの一覧を使用することができます</xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="45265-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="45265-129">次の例は、文字列のリストを作成しを使用して、文字列を使用して反復処理し、[ごとにしています.次](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="45265-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="45265-130">使用することができます、コレクションの内容が事前にわかっている場合、*コレクション初期化子*コレクションを初期化します。</span><span class="sxs-lookup"><span data-stu-id="45265-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="45265-131">詳細については、次を参照してください。[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="45265-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="45265-132">次の例は、コレクションへの要素の追加にコレクション初期化子を使用する以外、前の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="45265-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="45265-133">使用することができます、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ステートメントの代わりに、`For Each`コレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="45265-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="45265-134">インデックス位置によってコレクションの要素にアクセスすることで、これを実現します。</span><span class="sxs-lookup"><span data-stu-id="45265-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="45265-135">要素のインデックスは、0 から開始し、要素の数から 1 少ない値で終了します。</span><span class="sxs-lookup"><span data-stu-id="45265-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="45265-136">次の例は、`For…Next` の代わりに `For Each` を使用して、コレクションの要素を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="45265-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="45265-137">次の例は、削除するオブジェクトを指定して、コレクションから要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="45265-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="45265-138">次の例では、ジェネリック リストからすべての要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="45265-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="45265-139">代わりに、`For Each`ステートメント、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)降順に反復処理するステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="45265-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="45265-140">これは、<xref:System.Collections.Generic.List%601.RemoveAt%2A>メソッドが低いインデックス値を持つ削除された要素の後に要素をにより</xref:System.Collections.Generic.List%601.RemoveAt%2A>。</span><span class="sxs-lookup"><span data-stu-id="45265-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="45265-141">で<xref:System.Collections.Generic.List%601>、独自のクラスを定義することも、</xref:System.Collections.Generic.List%601>要素の型の</span><span class="sxs-lookup"><span data-stu-id="45265-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="45265-142">次の例で、`Galaxy`クラスによって使用される、 <xref:System.Collections.Generic.List%601>、コードで定義されています</xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="45265-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="45265-143">コレクションの種類</span><span class="sxs-lookup"><span data-stu-id="45265-143">Kinds of Collections</span></span>   
 <span data-ttu-id="45265-144">.NET Framework は、多くの共通のコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="45265-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="45265-145">各コレクションの型は、固有の目的に合わせてデザインされています。</span><span class="sxs-lookup"><span data-stu-id="45265-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="45265-146">このセクションでは、次の共通のコレクション クラスをいつくか説明します:</span><span class="sxs-lookup"><span data-stu-id="45265-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="45265-147">@System.Collections.Generic クラス</span><span class="sxs-lookup"><span data-stu-id="45265-147">@System.Collections.Generic classes</span></span>  
  
-   <span data-ttu-id="45265-148">@System.Collections.Concurrent クラス</span><span class="sxs-lookup"><span data-stu-id="45265-148">@System.Collections.Concurrent classes</span></span>  
  
-   <span data-ttu-id="45265-149">@System.Collections クラス</span><span class="sxs-lookup"><span data-stu-id="45265-149">@System.Collections classes</span></span>  
  
-   <span data-ttu-id="45265-150">Visual Basic の `Collection` クラス</span><span class="sxs-lookup"><span data-stu-id="45265-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="45265-151">System.Collections.Generic のクラス</span><span class="sxs-lookup"><span data-stu-id="45265-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="45265-152">ジェネリック コレクションを作成するにはクラスでは、いずれかを使用して、<xref:System.Collections.Generic>名前空間</xref:System.Collections.Generic>。</span><span class="sxs-lookup"><span data-stu-id="45265-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="45265-153">ジェネリック コレクションは、コレクション内のすべての項目が同じデータ型である場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="45265-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="45265-154">ジェネリック コレクションには該当するデータ型しか追加できないため、厳密な型指定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="45265-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="45265-155">次の表の頻繁に使用されるクラスの一覧、<xref:System.Collections.Generic?displayProperty=fullName>名前空間:</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="45265-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="45265-156">クラス</span><span class="sxs-lookup"><span data-stu-id="45265-156">Class</span></span>|<span data-ttu-id="45265-157">説明</span><span class="sxs-lookup"><span data-stu-id="45265-157">Description</span></span>|  
|---|---|  
|<span data-ttu-id="45265-158"><xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="45265-158"><xref:System.Collections.Generic.Dictionary%602></span></span>|<span data-ttu-id="45265-159">キーに基づいて編成された、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="45265-159">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<span data-ttu-id="45265-160"><xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="45265-160"><xref:System.Collections.Generic.List%601></span></span>|<span data-ttu-id="45265-161">インデックスを使用してアクセスできる、オブジェクトの一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="45265-161">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="45265-162">リストの検索、並べ替え、および変更のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="45265-162">Provides methods to search, sort, and modify lists.</span></span>|  
|<span data-ttu-id="45265-163"><xref:System.Collections.Generic.Queue%601></xref:System.Collections.Generic.Queue%601></span><span class="sxs-lookup"><span data-stu-id="45265-163"><xref:System.Collections.Generic.Queue%601></span></span>|<span data-ttu-id="45265-164">先入れ先出し (FIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="45265-164">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="45265-165"><xref:System.Collections.Generic.SortedList%602></xref:System.Collections.Generic.SortedList%602></span><span class="sxs-lookup"><span data-stu-id="45265-165"><xref:System.Collections.Generic.SortedList%602></span></span>|<span data-ttu-id="45265-166">関連付けられたに基づいてキーにより並べ替えられたキー/値ペアのコレクションを表す<xref:System.Collections.Generic.IComparer%601>実装</xref:System.Collections.Generic.IComparer%601>。</span><span class="sxs-lookup"><span data-stu-id="45265-166">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<span data-ttu-id="45265-167"><xref:System.Collections.Generic.Stack%601></xref:System.Collections.Generic.Stack%601></span><span class="sxs-lookup"><span data-stu-id="45265-167"><xref:System.Collections.Generic.Stack%601></span></span>|<span data-ttu-id="45265-168">後入れ先出し (LIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="45265-168">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="45265-169">詳細については、次を参照してください[よく使用されるコレクション型](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55)、[コレクション クラスの選択](../../../standard/collections/selecting-a-collection-class.md)、 <xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="45265-169">For additional information, see [Commonly Used Collection Types](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=fullName>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="45265-170">System.Collections.Concurrent のクラス</span><span class="sxs-lookup"><span data-stu-id="45265-170">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="45265-171">.NET Framework 4 またはそれ以降のコレクションで、<xref:System.Collections.Concurrent>名前空間は、複数のスレッドからコレクション項目にアクセスするための効率的なスレッド セーフな操作を提供します</xref:System.Collections.Concurrent>。</span><span class="sxs-lookup"><span data-stu-id="45265-171">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="45265-172">内のクラス、<xref:System.Collections.Concurrent>名前空間は、対応する型の代わりに使用する必要があります、<xref:System.Collections.Generic?displayProperty=fullName>と<xref:System.Collections?displayProperty=fullName>に、複数のスレッドがコレクションを同時にアクセスするたびに、名前空間</xref:System.Collections?displayProperty=fullName></xref:System.Collections.Generic?displayProperty=fullName></xref:System.Collections.Concurrent>。</span><span class="sxs-lookup"><span data-stu-id="45265-172">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=fullName> and <xref:System.Collections?displayProperty=fullName> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="45265-173">詳細については、次を参照してください[スレッド セーフなコレクション](../../../standard/collections/threadsafe/index.md) <xref:System.Collections.Concurrent>.</xref:System.Collections.Concurrent> 。</span><span class="sxs-lookup"><span data-stu-id="45265-173">For more information, see [Thread-Safe Collections](../../../standard/collections/threadsafe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="45265-174">含まれるいくつかのクラス、<xref:System.Collections.Concurrent>名前空間は<xref:System.Collections.Concurrent.BlockingCollection%601>、 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>、 <xref:System.Collections.Concurrent.ConcurrentQueue%601>、 <xref:System.Collections.Concurrent.ConcurrentStack%601>.</xref:System.Collections.Concurrent.ConcurrentStack%601> </xref:System.Collections.Concurrent.ConcurrentQueue%601> </xref:System.Collections.Concurrent.ConcurrentDictionary%602> </xref:System.Collections.Concurrent.BlockingCollection%601> </xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="45265-174">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="45265-175">System.Collections のクラス</span><span class="sxs-lookup"><span data-stu-id="45265-175">System.Collections Classes</span></span>    
 <span data-ttu-id="45265-176">内のクラス、<xref:System.Collections?displayProperty=fullName>型のオブジェクトが、具体的には型指定されたオブジェクトと名前空間が要素を格納しないで`Object`</xref:System.Collections?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="45265-176">The classes in the <xref:System.Collections?displayProperty=fullName> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="45265-177">可能であれば、ジェネリック コレクションを使用する必要があります、<xref:System.Collections.Generic?displayProperty=fullName>名前空間または<xref:System.Collections.Concurrent>従来型の代わりに名前空間、`System.Collections`名前空間</xref:System.Collections.Concurrent></xref:System.Collections.Generic?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="45265-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="45265-178">次のテーブルは `System.Collections` 名前空間でよく使用されるクラスの一覧です:</span><span class="sxs-lookup"><span data-stu-id="45265-178">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="45265-179">クラス</span><span class="sxs-lookup"><span data-stu-id="45265-179">Class</span></span>|<span data-ttu-id="45265-180">説明</span><span class="sxs-lookup"><span data-stu-id="45265-180">Description</span></span>|  
|---|---|  
|<span data-ttu-id="45265-181"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="45265-181"><xref:System.Collections.ArrayList></span></span>|<span data-ttu-id="45265-182">必要に応じてサイズが動的に拡大されるオブジェクトの配列を表します。</span><span class="sxs-lookup"><span data-stu-id="45265-182">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<span data-ttu-id="45265-183"><xref:System.Collections.Hashtable></xref:System.Collections.Hashtable></span><span class="sxs-lookup"><span data-stu-id="45265-183"><xref:System.Collections.Hashtable></span></span>|<span data-ttu-id="45265-184">キーのハッシュ コードに基づいて編成された、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="45265-184">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<span data-ttu-id="45265-185"><xref:System.Collections.Queue></xref:System.Collections.Queue></span><span class="sxs-lookup"><span data-stu-id="45265-185"><xref:System.Collections.Queue></span></span>|<span data-ttu-id="45265-186">先入れ先出し (FIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="45265-186">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<span data-ttu-id="45265-187"><xref:System.Collections.Stack></xref:System.Collections.Stack></span><span class="sxs-lookup"><span data-stu-id="45265-187"><xref:System.Collections.Stack></span></span>|<span data-ttu-id="45265-188">後入れ先出し (LIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="45265-188">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="45265-189"><xref:System.Collections.Specialized>名前空間には、文字列専用のコレクションやリンク リスト、ハイブリッド ディクショナリなどの厳密に型指定された専用のコレクション クラスが用意されています</xref:System.Collections.Specialized>。</span><span class="sxs-lookup"><span data-stu-id="45265-189">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="45265-190">Visual Basic のコレクション クラス</span><span class="sxs-lookup"><span data-stu-id="45265-190">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="45265-191">Visual Basic を使用する<xref:Microsoft.VisualBasic.Collection>クラスや数値インデックスを使用して、項目コレクションのアクセスを`String`キー</xref:Microsoft.VisualBasic.Collection> 。</span><span class="sxs-lookup"><span data-stu-id="45265-191">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="45265-192">キーを指定してもしなくても、項目をコレクション オブジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="45265-192">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="45265-193">キーを使わずに項目を追加した場合は、その項目にアクセスするときに数値インデックスを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="45265-193">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="45265-194">Visual Basic の `Collection` クラスは、そのすべての要素を `Object` 型として保存するため、任意のデータ型の項目を追加できます。</span><span class="sxs-lookup"><span data-stu-id="45265-194">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="45265-195">不適切なデータ型が追加されないようにする保護機能はありません。</span><span class="sxs-lookup"><span data-stu-id="45265-195">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="45265-196">Visual Basic の `Collection` クラスを使用すると、コレクション内の最初の項目はインデックス 1 となります。</span><span class="sxs-lookup"><span data-stu-id="45265-196">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="45265-197">これは、インデックスが 0 から開始される .NET Framework のコレクション クラスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="45265-197">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="45265-198">可能であれば、ジェネリック コレクションを使用する必要があります、<xref:System.Collections.Generic?displayProperty=fullName>名前空間または<xref:System.Collections.Concurrent>Visual Basic ではなく名前空間`Collection`クラス</xref:System.Collections.Concurrent></xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="45265-198">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=fullName> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="45265-199">詳細については、 <xref:Microsoft.VisualBasic.Collection>。</xref:Microsoft.VisualBasic.Collection>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45265-199">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="45265-200">キーと値のペアのコレクションを実装する</span><span class="sxs-lookup"><span data-stu-id="45265-200">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="45265-201"><xref:System.Collections.Generic.Dictionary%602>ジェネリック コレクションでは、各要素のキーを使用して、コレクション内の要素にアクセスすることができます</xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="45265-201">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="45265-202">ディクショナリに追加される各エントリは、値とその値に関連付けられたキーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="45265-202">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="45265-203">`Dictionary` クラスはハッシュ テーブルとして実装されているため、キーを使用した値の取得は非常に高速になります。</span><span class="sxs-lookup"><span data-stu-id="45265-203">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="45265-204">次の例では `Dictionary` のコレクションを作成し、`For Each` ステートメントを使用してディクショナリを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="45265-204">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <span data-ttu-id="45265-205">コレクション初期化子を使用して `Dictionary` コレクションをビルドする代わりに、`BuildDictionary` および `AddToDictionary` メソッドを次のメソッドに置換できます。</span><span class="sxs-lookup"><span data-stu-id="45265-205">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 <span data-ttu-id="45265-206">次の例では、<xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>メソッドおよび<xref:System.Collections.Generic.Dictionary%602.Item%2A>のプロパティ`Dictionary`キーによって項目をすばやく検索します</xref:System.Collections.Generic.Dictionary%602.Item%2A></xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="45265-206">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="45265-207">`Item`プロパティでは、項目にアクセスすることができます、`elements`を使用してコレクション、 `elements(symbol)` Visual basic コードです。</span><span class="sxs-lookup"><span data-stu-id="45265-207">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="45265-208">代わりに次の例を使用して、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>メソッドがキーによって項目をすばやく検索します</xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="45265-208">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="45265-209">LINQ を使用してコレクションにアクセスする</span><span class="sxs-lookup"><span data-stu-id="45265-209">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="45265-210">統合言語クエリ (LINQ) を使用してコレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="45265-210">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="45265-211">LINQ クエリは、フィルター処理、並べ替え、およびグループ化の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="45265-211">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="45265-212">詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)します。</span><span class="sxs-lookup"><span data-stu-id="45265-212">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="45265-213">次の例では、ジェネリック `List` に対して LINQ クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="45265-213">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="45265-214">LINQ クエリは、結果が格納されている別のコレクションを戻します。</span><span class="sxs-lookup"><span data-stu-id="45265-214">The LINQ query returns a different collection that contains the results.</span></span>  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a><span data-ttu-id="45265-215">コレクションを並べ替える</span><span class="sxs-lookup"><span data-stu-id="45265-215">Sorting a Collection</span></span>  
 <span data-ttu-id="45265-216">次の例では、コレクションを並べ替えるための手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="45265-216">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="45265-217">この例のインスタンスの並べ替え、 `Car` <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601>に格納されているクラス</span><span class="sxs-lookup"><span data-stu-id="45265-217">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="45265-218">`Car`クラスが実装する、<xref:System.IComparable%601>を必要とするインターフェイス、<xref:System.IComparable%601.CompareTo%2A>メソッドを実装する</xref:System.IComparable%601.CompareTo%2A></xref:System.IComparable%601>。</span><span class="sxs-lookup"><span data-stu-id="45265-218">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="45265-219">呼び出すたび、<xref:System.IComparable%601.CompareTo%2A>メソッドは、並べ替えに使用される単一の比較</xref:System.IComparable%601.CompareTo%2A>。</span><span class="sxs-lookup"><span data-stu-id="45265-219">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="45265-220">`CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。</span><span class="sxs-lookup"><span data-stu-id="45265-220">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="45265-221">現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。</span><span class="sxs-lookup"><span data-stu-id="45265-221">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="45265-222">これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。</span><span class="sxs-lookup"><span data-stu-id="45265-222">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="45265-223">`ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="45265-223">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="45265-224">この呼び出しを<xref:System.Collections.Generic.List%601.Sort%2A>のメソッド、<xref:System.Collections.Generic.List%601>により、`CompareTo`に対して自動的に呼び出されるメソッド、`Car`内のオブジェクト、 `List`</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A> 。</span><span class="sxs-lookup"><span data-stu-id="45265-224">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a><span data-ttu-id="45265-225">カスタム コレクションを定義する</span><span class="sxs-lookup"><span data-stu-id="45265-225">Defining a Custom Collection</span></span>  
 <span data-ttu-id="45265-226">コレクションを定義するには実装することによって、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Collections.IEnumerable>インターフェイス</xref:System.Collections.IEnumerable></xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="45265-226">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="45265-227">詳細については、次を参照してください。[コレクションを列挙する](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f)です。</span><span class="sxs-lookup"><span data-stu-id="45265-227">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="45265-228">カスタム コレクションを定義するには、通常に説明されている .NET Framework に含まれているコレクションを使用するように[コレクションの種類](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)このトピックの前です。</span><span class="sxs-lookup"><span data-stu-id="45265-228">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="45265-229">次の例は、`AllColors` という名前のカスタム コレクション クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="45265-229">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="45265-230">このクラスは、実装、<xref:System.Collections.IEnumerable>を必要とするインターフェイス、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドを実装する</xref:System.Collections.IEnumerable.GetEnumerator%2A></xref:System.Collections.IEnumerable>。</span><span class="sxs-lookup"><span data-stu-id="45265-230">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="45265-231">`GetEnumerator` メソッドは、`ColorEnumerator` クラスのインスタンスを戻します。</span><span class="sxs-lookup"><span data-stu-id="45265-231">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="45265-232">`ColorEnumerator`実装して、<xref:System.Collections.IEnumerator>を必要とするインターフェイス、<xref:System.Collections.IEnumerator.Current%2A>プロパティには、<xref:System.Collections.IEnumerator.MoveNext%2A>メソッド、および<xref:System.Collections.IEnumerator.Reset%2A>メソッドを実装する</xref:System.Collections.IEnumerator.Reset%2A></xref:System.Collections.IEnumerator.MoveNext%2A></xref:System.Collections.IEnumerator.Current%2A></xref:System.Collections.IEnumerator>。</span><span class="sxs-lookup"><span data-stu-id="45265-232">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a><span data-ttu-id="45265-233">反復子</span><span class="sxs-lookup"><span data-stu-id="45265-233">Iterators</span></span>  
 <span data-ttu-id="45265-234">*反復子*コレクションに対するカスタム イテレーションを実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="45265-234">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="45265-235">反復子は、メソッドまたは `get` アクセサーのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="45265-235">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="45265-236">反復子を使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを一度に&1; つのコレクションの各要素を返します。</span><span class="sxs-lookup"><span data-stu-id="45265-236">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="45265-237">使用して、反復子を呼び出す、[ごとにしています.次](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="45265-237">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="45265-238">`For Each` ループの各イテレーションは、反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="45265-238">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="45265-239">ときに、`Yield`反復子でステートメントに達すると、式が返され、コードの現在位置が保持されます。</span><span class="sxs-lookup"><span data-stu-id="45265-239">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="45265-240">次回、反復子が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="45265-240">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="45265-241">詳細については、次を参照してください。[反復子 (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md)します。</span><span class="sxs-lookup"><span data-stu-id="45265-241">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="45265-242">次の例は、Iterator メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="45265-242">The following example uses an iterator method.</span></span> <span data-ttu-id="45265-243">Iterator メソッドには、`Yield`ステートメント内にある、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。</span><span class="sxs-lookup"><span data-stu-id="45265-243">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="45265-244">`ListEvenNumbers`メソッドは、の各反復処理、`For Each`ステートメント本体を次の手順を実行する反復子メソッドの呼び出しを作成`Yield`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="45265-244">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="45265-245">関連項目</span><span class="sxs-lookup"><span data-stu-id="45265-245">See Also</span></span>  
 <span data-ttu-id="45265-246">[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span><span class="sxs-lookup"><span data-stu-id="45265-246">[Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md) </span></span>  
<span data-ttu-id="45265-247"> [プログラミングの概念 (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="45265-247"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="45265-248"> [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="45265-248"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="45265-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span><span class="sxs-lookup"><span data-stu-id="45265-249"> [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) </span></span>  
<span data-ttu-id="45265-250"> [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span><span class="sxs-lookup"><span data-stu-id="45265-250"> [Parallel LINQ (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455) </span></span>  
<span data-ttu-id="45265-251"> [コレクションとデータ構造体](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="45265-251"> [Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
<span data-ttu-id="45265-252"> [作成して、コレクションの操作](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span><span class="sxs-lookup"><span data-stu-id="45265-252"> [Creating and Manipulating Collections](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069) </span></span>  
<span data-ttu-id="45265-253"> [コレクション クラスの選択](../../../standard/collections/selecting-a-collection-class.md) </span><span class="sxs-lookup"><span data-stu-id="45265-253"> [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md) </span></span>  
<span data-ttu-id="45265-254"> [比較とコレクション内で並べ替え](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span><span class="sxs-lookup"><span data-stu-id="45265-254"> [Comparisons and Sorts Within Collections](../../../standard/collections/comparisons-and-sorts-within-collections.md) </span></span>  
<span data-ttu-id="45265-255"> [ジェネリック コレクションを使用する状況](../../../standard/collections/when-to-use-generic-collections.md)</span><span class="sxs-lookup"><span data-stu-id="45265-255"> [When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md)</span></span>
