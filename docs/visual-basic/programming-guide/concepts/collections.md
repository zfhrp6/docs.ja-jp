---
title: コレクション (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 563cef59c0e52d41dcdeaa51b5bc4d7b8f9554f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="collections-visual-basic"></a><span data-ttu-id="34272-102">コレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34272-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="34272-103">多くのアプリケーションで、関連するオブジェクトのグループの作成および管理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="34272-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="34272-104">オブジェクトをグループ化するには、オブジェクトの配列を作成する方法と、オブジェクトのコレクションを作成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="34272-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="34272-105">配列は、数が固定されている厳密に型指定されたオブジェクトの作成および処理に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="34272-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="34272-106">配列の詳細については、「[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34272-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="34272-107">コレクションは、オブジェクトのグループをより柔軟に処理できます。</span><span class="sxs-lookup"><span data-stu-id="34272-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="34272-108">配列の場合とは違って、コレクションで扱うオブジェクトのグループは、アプリケーションの変更に伴う必要に応じて動的に拡大および縮小できます。</span><span class="sxs-lookup"><span data-stu-id="34272-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="34272-109">コレクションによっては、コレクションに含まれるオブジェクトのキーを割り当てると、そのキーを使用してオブジェクトを迅速に取り出すことができます。</span><span class="sxs-lookup"><span data-stu-id="34272-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="34272-110">コレクションはクラスであるため、そのコレクションに要素を追加するには、事前にそのクラスのインスタンスを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34272-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="34272-111">含まれる要素が 1 つのデータ型だけのコレクションの場合は、<xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間のクラスのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="34272-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="34272-112">ジェネリック コレクションでは、タイプ セーフが強制されるため、他のデータ型を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="34272-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="34272-113">ジェネリック コレクションから要素を取得する場合は、データ型を判断したり、変換したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="34272-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34272-114">このトピックの例については、含める[Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)のステートメント、`System.Collections.Generic`と`System.Linq`名前空間。</span><span class="sxs-lookup"><span data-stu-id="34272-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="34272-115">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="34272-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="34272-116">単純なコレクションを使用する</span><span class="sxs-lookup"><span data-stu-id="34272-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="34272-117">コレクションの種類</span><span class="sxs-lookup"><span data-stu-id="34272-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="34272-118">System.Collections.Generic のクラス</span><span class="sxs-lookup"><span data-stu-id="34272-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="34272-119">System.Collections.Concurrent のクラス</span><span class="sxs-lookup"><span data-stu-id="34272-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="34272-120">System.Collections のクラス</span><span class="sxs-lookup"><span data-stu-id="34272-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="34272-121">Visual Basic のコレクション クラス</span><span class="sxs-lookup"><span data-stu-id="34272-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="34272-122">キーと値のペアのコレクションを実装する</span><span class="sxs-lookup"><span data-stu-id="34272-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="34272-123">LINQ を使用してコレクションにアクセスする</span><span class="sxs-lookup"><span data-stu-id="34272-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="34272-124">コレクションを並べ替える</span><span class="sxs-lookup"><span data-stu-id="34272-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="34272-125">カスタム コレクションを定義する</span><span class="sxs-lookup"><span data-stu-id="34272-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="34272-126">反復子</span><span class="sxs-lookup"><span data-stu-id="34272-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="34272-127">単純なコレクションを使用する</span><span class="sxs-lookup"><span data-stu-id="34272-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="34272-128">このセクションの例は、厳密に型指定されたオブジェクトの一覧を使用できる、ジェネリックの <xref:System.Collections.Generic.List%601> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="34272-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="34272-129">次の例は、文字列のリストを作成しを使用して、文字列を反復処理し、[ごとにしています.[次へ]](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="34272-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="34272-130">コレクションのコンテンツが既知の場合、コレクションの初期化に*コレクション初期化子*を使用できます。</span><span class="sxs-lookup"><span data-stu-id="34272-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="34272-131">詳細については、「[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34272-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="34272-132">次の例は、コレクションへの要素の追加にコレクション初期化子を使用する以外、前の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="34272-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="34272-133">使用することができます、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)ステートメントの代わりに、`For Each`コレクションを反復処理するステートメント。</span><span class="sxs-lookup"><span data-stu-id="34272-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="34272-134">インデックス位置によってコレクションの要素にアクセスすることで、これを実現します。</span><span class="sxs-lookup"><span data-stu-id="34272-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="34272-135">要素のインデックスは、0 から開始し、要素の数から 1 少ない値で終了します。</span><span class="sxs-lookup"><span data-stu-id="34272-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="34272-136">次の例は、`For…Next` の代わりに `For Each` を使用して、コレクションの要素を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="34272-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="34272-137">次の例は、削除するオブジェクトを指定して、コレクションから要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="34272-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="34272-138">次の例では、ジェネリック リストからすべての要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="34272-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="34272-139">代わりに、`For Each`ステートメント、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)降順に反復処理するステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="34272-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="34272-140">これは、<xref:System.Collections.Generic.List%601.RemoveAt%2A> メソッドを実行すると、削除された要素の後にある各要素のインデックス値が小さくなるためです。</span><span class="sxs-lookup"><span data-stu-id="34272-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="34272-141"><xref:System.Collections.Generic.List%601> の要素の型は、独自のクラスでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="34272-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="34272-142">次の例では、`Galaxy` が使用する <xref:System.Collections.Generic.List%601> クラスがコードに定義されます。</span><span class="sxs-lookup"><span data-stu-id="34272-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="34272-143">コレクションの種類</span><span class="sxs-lookup"><span data-stu-id="34272-143">Kinds of Collections</span></span>   
 <span data-ttu-id="34272-144">.NET Framework は、多くの共通のコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="34272-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="34272-145">各コレクションの型は、固有の目的に合わせてデザインされています。</span><span class="sxs-lookup"><span data-stu-id="34272-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="34272-146">このセクションでは、次の共通のコレクション クラスをいつくか説明します:</span><span class="sxs-lookup"><span data-stu-id="34272-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="34272-147"><xref:System.Collections.Generic> クラス</span><span class="sxs-lookup"><span data-stu-id="34272-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="34272-148"><xref:System.Collections.Concurrent> クラス</span><span class="sxs-lookup"><span data-stu-id="34272-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="34272-149"><xref:System.Collections> クラス</span><span class="sxs-lookup"><span data-stu-id="34272-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="34272-150">Visual Basic の `Collection` クラス</span><span class="sxs-lookup"><span data-stu-id="34272-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="34272-151">System.Collections.Generic のクラス</span><span class="sxs-lookup"><span data-stu-id="34272-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="34272-152"><xref:System.Collections.Generic> 名前空間の 1 つのクラスを使用すると、ジェネリック コレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="34272-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="34272-153">ジェネリック コレクションは、コレクション内のすべての項目が同じデータ型である場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="34272-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="34272-154">ジェネリック コレクションには該当するデータ型しか追加できないため、厳密な型指定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="34272-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="34272-155">次のテーブルは <xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間でよく使用されるクラスの一覧です:</span><span class="sxs-lookup"><span data-stu-id="34272-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="34272-156">クラス</span><span class="sxs-lookup"><span data-stu-id="34272-156">Class</span></span>|<span data-ttu-id="34272-157">説明</span><span class="sxs-lookup"><span data-stu-id="34272-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="34272-158">キーに基づいて編成された、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="34272-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="34272-159">インデックスを使用してアクセスできる、オブジェクトの一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="34272-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="34272-160">リストの検索、並べ替え、および変更のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="34272-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="34272-161">先入れ先出し (FIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="34272-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="34272-162">関連付けられた <xref:System.Collections.Generic.IComparer%601> 実装に基づいて、キーにより並べ替えられた、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="34272-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="34272-163">後入れ先出し (LIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="34272-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="34272-164">詳細については、「[一般的に使用されるコレクション型](../../../standard/collections/commonly-used-collection-types.md)」、「[コレクション クラスの選択](../../../standard/collections/selecting-a-collection-class.md)」、「<xref:System.Collections.Generic?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34272-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="34272-165">System.Collections.Concurrent のクラス</span><span class="sxs-lookup"><span data-stu-id="34272-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="34272-166">.NET Framework 4 以降では、<xref:System.Collections.Concurrent> 名前空間のコレクションによって、複数のスレッドからコレクション項目にアクセスするための効率的なスレッド セーフ操作が可能になります。</span><span class="sxs-lookup"><span data-stu-id="34272-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="34272-167"><xref:System.Collections.Concurrent> 名前空間のクラスは、複数のスレッドがコレクションに同時にアクセスするときに、<xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間および <xref:System.Collections?displayProperty=nameWithType> 名前空間の対応する型の代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34272-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="34272-168">詳しくは、「[スレッド セーフなコレクション](../../../standard/collections/thread-safe/index.md)」と「<xref:System.Collections.Concurrent>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34272-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="34272-169"><xref:System.Collections.Concurrent> 名前空間には、<xref:System.Collections.Concurrent.BlockingCollection%601>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>、<xref:System.Collections.Concurrent.ConcurrentQueue%601>、および <xref:System.Collections.Concurrent.ConcurrentStack%601> などのクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="34272-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="34272-170">System.Collections のクラス</span><span class="sxs-lookup"><span data-stu-id="34272-170">System.Collections Classes</span></span>    
 <span data-ttu-id="34272-171"><xref:System.Collections?displayProperty=nameWithType> 名前空間のクラスでは、要素は、固有の型のオブジェクトとしてではなく `Object` 型のオブジェクトとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="34272-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="34272-172">できる限り、<xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間の従来の型の代わりに、<xref:System.Collections.Concurrent> 名前空間または `System.Collections` 名前空間のジェネリック コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="34272-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="34272-173">次のテーブルは `System.Collections` 名前空間でよく使用されるクラスの一覧です:</span><span class="sxs-lookup"><span data-stu-id="34272-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="34272-174">クラス</span><span class="sxs-lookup"><span data-stu-id="34272-174">Class</span></span>|<span data-ttu-id="34272-175">説明</span><span class="sxs-lookup"><span data-stu-id="34272-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="34272-176">必要に応じてサイズが動的に拡大されるオブジェクトの配列を表します。</span><span class="sxs-lookup"><span data-stu-id="34272-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="34272-177">キーのハッシュ コードに基づいて編成された、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="34272-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="34272-178">先入れ先出し (FIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="34272-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="34272-179">後入れ先出し (LIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="34272-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="34272-180"><xref:System.Collections.Specialized> 名前空間には、文字列専用のコレクションやリンク リスト、ハイブリッド ディクショナリなど、厳密に型指定された専用のコレクション クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="34272-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="34272-181">Visual Basic のコレクション クラス</span><span class="sxs-lookup"><span data-stu-id="34272-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="34272-182">数値インデックスまたは <xref:Microsoft.VisualBasic.Collection> キーを使用したコレクション項目にアクセスするには、Visual Basic の `String` のクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="34272-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="34272-183">キーを指定してもしなくても、項目をコレクション オブジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="34272-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="34272-184">キーを使わずに項目を追加した場合は、その項目にアクセスするときに数値インデックスを使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="34272-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="34272-185">Visual Basic の `Collection` クラスは、そのすべての要素を `Object` 型として保存するため、任意のデータ型の項目を追加できます。</span><span class="sxs-lookup"><span data-stu-id="34272-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="34272-186">不適切なデータ型が追加されないようにする保護機能はありません。</span><span class="sxs-lookup"><span data-stu-id="34272-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="34272-187">Visual Basic の `Collection` クラスを使用すると、コレクション内の最初の項目はインデックス 1 となります。</span><span class="sxs-lookup"><span data-stu-id="34272-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="34272-188">これは、インデックスが 0 から開始される .NET Framework のコレクション クラスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="34272-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="34272-189">できる限り、Visual Basic の <xref:System.Collections.Generic?displayProperty=nameWithType> クラスの代わりに、<xref:System.Collections.Concurrent> 名前空間または `Collection` 名前空間のジェネリック コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="34272-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="34272-190">詳細については、「<xref:Microsoft.VisualBasic.Collection>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34272-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="34272-191">キーと値のペアのコレクションを実装する</span><span class="sxs-lookup"><span data-stu-id="34272-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="34272-192"><xref:System.Collections.Generic.Dictionary%602> ジェネリック コレクションでは、各要素のキーを使用してコレクションの要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="34272-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="34272-193">ディクショナリに追加される各エントリは、値とその値に関連付けられたキーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="34272-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="34272-194">`Dictionary` クラスはハッシュ テーブルとして実装されているため、キーを使用した値の取得は非常に高速になります。</span><span class="sxs-lookup"><span data-stu-id="34272-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="34272-195">次の例では `Dictionary` のコレクションを作成し、`For Each` ステートメントを使用してディクショナリを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="34272-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
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
  
 <span data-ttu-id="34272-196">コレクション初期化子を使用して `Dictionary` コレクションをビルドする代わりに、`BuildDictionary` および `AddToDictionary` メソッドを次のメソッドに置換できます。</span><span class="sxs-lookup"><span data-stu-id="34272-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="34272-197">次の例では、キーによって項目をすばやく検索するために、<xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> の <xref:System.Collections.Generic.Dictionary%602.Item%2A> メソッドと `Dictionary` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="34272-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="34272-198">`Item`プロパティでは、項目にアクセスすることができます、`elements`コレクションを使用して、 `elements(symbol)` Visual basic コードです。</span><span class="sxs-lookup"><span data-stu-id="34272-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
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
  
 <span data-ttu-id="34272-199">次の例では、キーによって項目をすばやく検索するために、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> メソッドを代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="34272-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="34272-200">LINQ を使用してコレクションにアクセスする</span><span class="sxs-lookup"><span data-stu-id="34272-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="34272-201">統合言語クエリ (LINQ) を使用してコレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="34272-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="34272-202">LINQ クエリは、フィルター処理、並べ替え、およびグループ化の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="34272-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="34272-203">詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)です。</span><span class="sxs-lookup"><span data-stu-id="34272-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="34272-204">次の例では、ジェネリック `List` に対して LINQ クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="34272-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="34272-205">LINQ クエリは、結果が格納されている別のコレクションを戻します。</span><span class="sxs-lookup"><span data-stu-id="34272-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="34272-206">コレクションを並べ替える</span><span class="sxs-lookup"><span data-stu-id="34272-206">Sorting a Collection</span></span>  
 <span data-ttu-id="34272-207">次の例では、コレクションを並べ替えるための手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="34272-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="34272-208">この例は、`Car` に格納されている <xref:System.Collections.Generic.List%601> クラスのインスタンスの並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="34272-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="34272-209">`Car` クラスは、<xref:System.IComparable%601> のメソッドの実装を必要とする <xref:System.IComparable%601.CompareTo%2A> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="34272-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="34272-210"><xref:System.IComparable%601.CompareTo%2A> メソッドに対する各呼び出しは、並べ替えに使用される単一の比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="34272-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="34272-211">`CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。</span><span class="sxs-lookup"><span data-stu-id="34272-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="34272-212">現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。</span><span class="sxs-lookup"><span data-stu-id="34272-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="34272-213">これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。</span><span class="sxs-lookup"><span data-stu-id="34272-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="34272-214">`ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="34272-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="34272-215"><xref:System.Collections.Generic.List%601.Sort%2A> の <xref:System.Collections.Generic.List%601> メソッドへの呼び出しによって、`CompareTo` メソッドは `Car` 内の `List` オブジェクトに自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="34272-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="34272-216">カスタム コレクションを定義する</span><span class="sxs-lookup"><span data-stu-id="34272-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="34272-217"><xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Collections.IEnumerable> のインターフェイスを実装してコレクションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="34272-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="34272-218">詳細については、次を参照してください。[コレクションを列挙して](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f)です。</span><span class="sxs-lookup"><span data-stu-id="34272-218">For additional information, see [Enumerating a Collection](http://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="34272-219">カスタム コレクションを定義できますが、通常は、.NET Framework に含まれるコレクションを使用することが推奨されます。これについては、このトピックの[コレクションの種類](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)で既に説明されています。</span><span class="sxs-lookup"><span data-stu-id="34272-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) earlier in this topic.</span></span>  
  
 <span data-ttu-id="34272-220">次の例は、`AllColors` という名前のカスタム コレクション クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="34272-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="34272-221">このクラスは、<xref:System.Collections.IEnumerable> メソッドの実装を必要とする <xref:System.Collections.IEnumerable.GetEnumerator%2A> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="34272-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="34272-222">`GetEnumerator` メソッドは、`ColorEnumerator` クラスのインスタンスを戻します。</span><span class="sxs-lookup"><span data-stu-id="34272-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="34272-223">`ColorEnumerator` は、<xref:System.Collections.IEnumerator> プロパティ、<xref:System.Collections.IEnumerator.Current%2A> メソッド、および <xref:System.Collections.IEnumerator.MoveNext%2A> メソッドの実装を必要とする <xref:System.Collections.IEnumerator.Reset%2A> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="34272-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="34272-224">Iterators</span><span class="sxs-lookup"><span data-stu-id="34272-224">Iterators</span></span>  
 <span data-ttu-id="34272-225">*反復子*は、コレクションに対するカスタム イテレーションを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="34272-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="34272-226">反復子は、メソッドまたは `get` アクセサーのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="34272-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="34272-227">反復子を使用して、 [Yield](../../../visual-basic/language-reference/statements/yield-statement.md)ステートメントを一度にいずれかのコレクションの各要素を返します。</span><span class="sxs-lookup"><span data-stu-id="34272-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="34272-228">使用して、反復子を呼び出す、[ごとにしています.[次へ]](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="34272-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="34272-229">`For Each` ループの各イテレーションは、反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="34272-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="34272-230">`Yield` ステートメントが反復子に到達すると、式が戻され、コードの現在の位置が保持されます。</span><span class="sxs-lookup"><span data-stu-id="34272-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="34272-231">次回、反復子が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="34272-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="34272-232">詳細については、次を参照してください。[反復子 (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md)です。</span><span class="sxs-lookup"><span data-stu-id="34272-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="34272-233">次の例は、反復子メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="34272-233">The following example uses an iterator method.</span></span> <span data-ttu-id="34272-234">Iterator メソッドには、`Yield`内にあるステートメント、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。</span><span class="sxs-lookup"><span data-stu-id="34272-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="34272-235">`ListEvenNumbers` メソッドでは、`For Each` ステートメント本文の各イテレーションが、反復子メソッドの呼び出しを作成し、これが次の `Yield` ステートメントに続行されます。</span><span class="sxs-lookup"><span data-stu-id="34272-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34272-236">関連項目</span><span class="sxs-lookup"><span data-stu-id="34272-236">See Also</span></span>  
 [<span data-ttu-id="34272-237">コレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="34272-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="34272-238">プログラミングの概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34272-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="34272-239">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="34272-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="34272-240">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34272-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="34272-241">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="34272-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="34272-242">コレクションとデータ構造体</span><span class="sxs-lookup"><span data-stu-id="34272-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="34272-243">コレクションの作成と操作</span><span class="sxs-lookup"><span data-stu-id="34272-243">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="34272-244">コレクション クラスの選択</span><span class="sxs-lookup"><span data-stu-id="34272-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="34272-245">コレクション内での比較と並べ替え</span><span class="sxs-lookup"><span data-stu-id="34272-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="34272-246">ジェネリック コレクションを使用する状況</span><span class="sxs-lookup"><span data-stu-id="34272-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
