---
title: コレクション (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 85cbabf74a702a4d6442a29c3cf3d7b726ab38da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="collections-c"></a><span data-ttu-id="2faf4-102">コレクション (C#)</span><span class="sxs-lookup"><span data-stu-id="2faf4-102">Collections (C#)</span></span>
<span data-ttu-id="2faf4-103">多くのアプリケーションで、関連するオブジェクトのグループの作成および管理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="2faf4-104">オブジェクトをグループ化するには、オブジェクトの配列を作成する方法と、オブジェクトのコレクションを作成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="2faf4-105">配列は、数が固定されている厳密に型指定されたオブジェクトの作成および処理に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="2faf4-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="2faf4-106">配列の詳細については、「[配列](../../../csharp/programming-guide/arrays/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faf4-106">For information about arrays, see [Arrays](../../../csharp/programming-guide/arrays/index.md).</span></span>  
  
 <span data-ttu-id="2faf4-107">コレクションは、オブジェクトのグループをより柔軟に処理できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="2faf4-108">配列の場合とは違って、コレクションで扱うオブジェクトのグループは、アプリケーションの変更に伴う必要に応じて動的に拡大および縮小できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="2faf4-109">コレクションによっては、コレクションに含まれるオブジェクトのキーを割り当てると、そのキーを使用してオブジェクトを迅速に取り出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="2faf4-110">コレクションはクラスであるため、そのコレクションに要素を追加するには、事前にそのクラスのインスタンスを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="2faf4-111">含まれる要素が 1 つのデータ型だけのコレクションの場合は、<xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間のクラスのいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="2faf4-112">ジェネリック コレクションでは、タイプ セーフが強制されるため、他のデータ型を追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="2faf4-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="2faf4-113">ジェネリック コレクションから要素を取得する場合は、データ型を判断したり、変換したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2faf4-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2faf4-114">このトピックの例には、`System.Collections.Generic` 名前空間および `System.Linq` 名前空間の [using](../../../csharp/language-reference/keywords/using-directive.md) ディレクティブがあります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-114">For the examples in this topic, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="2faf4-115">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2faf4-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="2faf4-116">単純なコレクションを使用する</span><span class="sxs-lookup"><span data-stu-id="2faf4-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="2faf4-117">コレクションの種類</span><span class="sxs-lookup"><span data-stu-id="2faf4-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="2faf4-118">System.Collections.Generic のクラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="2faf4-119">System.Collections.Concurrent のクラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="2faf4-120">System.Collections のクラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
-   [<span data-ttu-id="2faf4-121">キーと値のペアのコレクションを実装する</span><span class="sxs-lookup"><span data-stu-id="2faf4-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="2faf4-122">LINQ を使用してコレクションにアクセスする</span><span class="sxs-lookup"><span data-stu-id="2faf4-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="2faf4-123">コレクションを並べ替える</span><span class="sxs-lookup"><span data-stu-id="2faf4-123">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="2faf4-124">カスタム コレクションを定義する</span><span class="sxs-lookup"><span data-stu-id="2faf4-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="2faf4-125">反復子</span><span class="sxs-lookup"><span data-stu-id="2faf4-125">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="2faf4-126">単純なコレクションを使用する</span><span class="sxs-lookup"><span data-stu-id="2faf4-126">Using a Simple Collection</span></span>  
 <span data-ttu-id="2faf4-127">このセクションの例は、厳密に型指定されたオブジェクトの一覧を使用できる、ジェネリックの <xref:System.Collections.Generic.List%601> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="2faf4-128">次の例は、文字列の一覧を作成した後、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用して文字列を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-128">The following example creates a list of strings and then iterates through the strings by using a or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
```csharp  
// Create a list of strings.  
var salmons = new List<string>();  
salmons.Add("chinook");  
salmons.Add("coho");  
salmons.Add("pink");  
salmons.Add("sockeye");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="2faf4-129">コレクションのコンテンツが既知の場合、コレクションの初期化に*コレクション初期化子*を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="2faf4-130">詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faf4-130">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
 <span data-ttu-id="2faf4-131">次の例は、コレクションへの要素の追加にコレクション初期化子を使用する以外、前の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="2faf4-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="2faf4-132">コレクションを反復処理するには、`foreach` ステートメントの代わりに、[for](../../../csharp/language-reference/keywords/for.md) ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-132">You can use a [for](../../../csharp/language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="2faf4-133">インデックス位置によってコレクションの要素にアクセスすることで、これを実現します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="2faf4-134">要素のインデックスは、0 から開始し、要素の数から 1 少ない値で終了します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="2faf4-135">次の例は、`for` の代わりに `foreach` を使用して、コレクションの要素を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
for (var index = 0; index < salmons.Count; index++)  
{  
    Console.Write(salmons[index] + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="2faf4-136">次の例は、削除するオブジェクトを指定して、コレクションから要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-136">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Remove an element from the list by specifying  
// the object.  
salmons.Remove("coho");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="2faf4-137">次の例では、ジェネリック リストからすべての要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="2faf4-138">`foreach` ステートメントの代わりに、降順に反復する [for](../../../csharp/language-reference/keywords/for.md) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-138">Instead of a `foreach` statement, a [for](../../../csharp/language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="2faf4-139">これは、<xref:System.Collections.Generic.List%601.RemoveAt%2A> メソッドを実行すると、削除された要素の後にある各要素のインデックス値が小さくなるためです。</span><span class="sxs-lookup"><span data-stu-id="2faf4-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```csharp  
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
// Remove odd numbers.  
for (var index = numbers.Count - 1; index >= 0; index--)  
{  
    if (numbers[index] % 2 == 1)  
    {  
        // Remove the element by specifying  
        // the zero-based index in the list.  
        numbers.RemoveAt(index);  
    }  
}  
  
// Iterate through the list.  
// A lambda expression is placed in the ForEach method  
// of the List(T) object.  
numbers.ForEach(  
    number => Console.Write(number + " "));  
// Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="2faf4-140"><xref:System.Collections.Generic.List%601> の要素の型は、独自のクラスでも定義できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="2faf4-141">次の例では、`Galaxy` が使用する <xref:System.Collections.Generic.List%601> クラスがコードに定義されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```csharp  
private static void IterateThroughList()  
{  
    var theGalaxies = new List<Galaxy>  
        {  
            new Galaxy() { Name="Tadpole", MegaLightYears=400},  
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},  
            new Galaxy() { Name="Milky Way", MegaLightYears=0},  
            new Galaxy() { Name="Andromeda", MegaLightYears=3}  
        };  
  
    foreach (Galaxy theGalaxy in theGalaxies)  
    {  
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);  
    }  
  
    // Output:  
    //  Tadpole  400  
    //  Pinwheel  25  
    //  Milky Way  0  
    //  Andromeda  3  
}  
  
public class Galaxy  
{  
    public string Name { get; set; }  
    public int MegaLightYears { get; set; }  
}  
```  

<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="2faf4-142">コレクションの種類</span><span class="sxs-lookup"><span data-stu-id="2faf4-142">Kinds of Collections</span></span> 
 <span data-ttu-id="2faf4-143">.NET Framework は、多くの共通のコレクションを提供します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="2faf4-144">各コレクションの型は、固有の目的に合わせてデザインされています。</span><span class="sxs-lookup"><span data-stu-id="2faf4-144">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="2faf4-145">このセクションでは、次の共通のコレクション クラスをいつくか説明します:</span><span class="sxs-lookup"><span data-stu-id="2faf4-145">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="2faf4-146"><xref:System.Collections.Generic> クラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-146"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="2faf4-147"><xref:System.Collections.Concurrent> クラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-147"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="2faf4-148"><xref:System.Collections> クラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-148"><xref:System.Collections> classes</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="2faf4-149">System.Collections.Generic のクラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-149">System.Collections.Generic Classes</span></span>  
 <span data-ttu-id="2faf4-150"><xref:System.Collections.Generic> 名前空間の 1 つのクラスを使用すると、ジェネリック コレクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="2faf4-151">ジェネリック コレクションは、コレクション内のすべての項目が同じデータ型である場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="2faf4-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="2faf4-152">ジェネリック コレクションには該当するデータ型しか追加できないため、厳密な型指定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="2faf4-153">次のテーブルは <xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間でよく使用されるクラスの一覧です:</span><span class="sxs-lookup"><span data-stu-id="2faf4-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  

|<span data-ttu-id="2faf4-154">クラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-154">Class</span></span>|<span data-ttu-id="2faf4-155">説明</span><span class="sxs-lookup"><span data-stu-id="2faf4-155">Description</span></span>| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="2faf4-156">キーに基づいて編成された、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="2faf4-157">インデックスを使用してアクセスできる、オブジェクトの一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="2faf4-158">リストの検索、並べ替え、および変更のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-158">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="2faf4-159">先入れ先出し (FIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="2faf4-160">関連付けられた <xref:System.Collections.Generic.IComparer%601> 実装に基づいて、キーにより並べ替えられた、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="2faf4-161">後入れ先出し (LIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="2faf4-162">詳細については、「[一般的に使用されるコレクション型](../../../standard/collections/commonly-used-collection-types.md)」、「[コレクション クラスの選択](../../../standard/collections/selecting-a-collection-class.md)」、「<xref:System.Collections.Generic>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faf4-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="2faf4-163">System.Collections.Concurrent のクラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-163">System.Collections.Concurrent Classes</span></span>  
 <span data-ttu-id="2faf4-164">.NET Framework 4 以降では、<xref:System.Collections.Concurrent> 名前空間のコレクションによって、複数のスレッドからコレクション項目にアクセスするための効率的なスレッド セーフ操作が可能になります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="2faf4-165"><xref:System.Collections.Concurrent> 名前空間のクラスは、複数のスレッドがコレクションに同時にアクセスするときに、<xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間および <xref:System.Collections?displayProperty=nameWithType> 名前空間の対応する型の代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="2faf4-166">詳しくは、「[スレッド セーフなコレクション](../../../standard/collections/thread-safe/index.md)」と「<xref:System.Collections.Concurrent>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faf4-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="2faf4-167"><xref:System.Collections.Concurrent> 名前空間には、<xref:System.Collections.Concurrent.BlockingCollection%601>、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>、<xref:System.Collections.Concurrent.ConcurrentQueue%601>、および <xref:System.Collections.Concurrent.ConcurrentStack%601> などのクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="2faf4-168">System.Collections のクラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-168">System.Collections Classes</span></span>  
 <span data-ttu-id="2faf4-169"><xref:System.Collections?displayProperty=nameWithType> 名前空間のクラスでは、要素は、固有の型のオブジェクトとしてではなく `Object` 型のオブジェクトとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="2faf4-170">できる限り、<xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間の従来の型の代わりに、<xref:System.Collections.Concurrent> 名前空間または `System.Collections` 名前空間のジェネリック コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="2faf4-171">次のテーブルは `System.Collections` 名前空間でよく使用されるクラスの一覧です:</span><span class="sxs-lookup"><span data-stu-id="2faf4-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="2faf4-172">クラス</span><span class="sxs-lookup"><span data-stu-id="2faf4-172">Class</span></span>|<span data-ttu-id="2faf4-173">説明</span><span class="sxs-lookup"><span data-stu-id="2faf4-173">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="2faf4-174">必要に応じてサイズが動的に拡大されるオブジェクトの配列を表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="2faf4-175">キーのハッシュ コードに基づいて編成された、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="2faf4-176">先入れ先出し (FIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="2faf4-177">後入れ先出し (LIFO) のオブジェクトのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="2faf4-178"><xref:System.Collections.Specialized> 名前空間には、文字列専用のコレクションやリンク リスト、ハイブリッド ディクショナリなど、厳密に型指定された専用のコレクション クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2faf4-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="2faf4-179">キーと値のペアのコレクションを実装する</span><span class="sxs-lookup"><span data-stu-id="2faf4-179">Implementing a Collection of Key/Value Pairs</span></span>  
 <span data-ttu-id="2faf4-180"><xref:System.Collections.Generic.Dictionary%602> ジェネリック コレクションでは、各要素のキーを使用してコレクションの要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="2faf4-181">ディクショナリに追加される各エントリは、値とその値に関連付けられたキーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="2faf4-182">`Dictionary` クラスはハッシュ テーブルとして実装されているため、キーを使用した値の取得は非常に高速になります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="2faf4-183">次の例では `Dictionary` のコレクションを作成し、`foreach` ステートメントを使用してディクショナリを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>  
  
```csharp  
private static void IterateThruDictionary()  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    foreach (KeyValuePair<string, Element> kvp in elements)  
    {  
        Element theElement = kvp.Value;  
  
        Console.WriteLine("key: " + kvp.Key);  
        Console.WriteLine("values: " + theElement.Symbol + " " +  
            theElement.Name + " " + theElement.AtomicNumber);  
    }  
}  
  
private static Dictionary<string, Element> BuildDictionary()  
{  
    var elements = new Dictionary<string, Element>();  
  
    AddToDictionary(elements, "K", "Potassium", 19);  
    AddToDictionary(elements, "Ca", "Calcium", 20);  
    AddToDictionary(elements, "Sc", "Scandium", 21);  
    AddToDictionary(elements, "Ti", "Titanium", 22);  
  
    return elements;  
}  
  
private static void AddToDictionary(Dictionary<string, Element> elements,  
    string symbol, string name, int atomicNumber)  
{  
    Element theElement = new Element();  
  
    theElement.Symbol = symbol;  
    theElement.Name = name;  
    theElement.AtomicNumber = atomicNumber;  
  
    elements.Add(key: theElement.Symbol, value: theElement);  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  
  
 <span data-ttu-id="2faf4-184">コレクション初期化子を使用して `Dictionary` コレクションをビルドする代わりに、`BuildDictionary` および `AddToDictionary` メソッドを次のメソッドに置換できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```csharp  
private static Dictionary<string, Element> BuildDictionary2()  
{  
    return new Dictionary<string, Element>  
    {  
        {"K",  
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        {"Ca",  
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        {"Sc",  
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        {"Ti",  
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
```  
  
 <span data-ttu-id="2faf4-185">次の例では、キーによって項目をすばやく検索するために、<xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> の <xref:System.Collections.Generic.Dictionary%602.Item%2A> メソッドと `Dictionary` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="2faf4-186">`Item` プロパティでは、C# の `elements[symbol]` を使用して `elements` コレクションの項目にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>  
  
```csharp  
private static void FindInDictionary(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    if (elements.ContainsKey(symbol) == false)  
    {  
        Console.WriteLine(symbol + " not found");  
    }  
    else  
    {  
        Element theElement = elements[symbol];  
        Console.WriteLine("found: " + theElement.Name);  
    }  
}  
```  
  
 <span data-ttu-id="2faf4-187">次の例では、キーによって項目をすばやく検索するために、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> メソッドを代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```csharp  
private static void FindInDictionary2(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    Element theElement = null;  
    if (elements.TryGetValue(symbol, out theElement) == false)  
        Console.WriteLine(symbol + " not found");  
    else  
        Console.WriteLine("found: " + theElement.Name);  
}  
```  

<a name="BKMK_LINQ"></a>
## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="2faf4-188">LINQ を使用してコレクションにアクセスする</span><span class="sxs-lookup"><span data-stu-id="2faf4-188">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="2faf4-189">統合言語クエリ (LINQ) を使用してコレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="2faf4-190">LINQ クエリは、フィルター処理、並べ替え、およびグループ化の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="2faf4-191">詳細については、「[Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)」 (C# での LINQ の概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faf4-191">For more information, see  [Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="2faf4-192">次の例では、ジェネリック `List` に対して LINQ クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="2faf4-193">LINQ クエリは、結果が格納されている別のコレクションを戻します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-193">The LINQ query returns a different collection that contains the results.</span></span>  
  
```csharp  
private static void ShowLINQ()  
{  
    List<Element> elements = BuildList();  
  
    // LINQ Query.  
    var subset = from theElement in elements  
                 where theElement.AtomicNumber < 22  
                 orderby theElement.Name  
                 select theElement;  
  
    foreach (Element theElement in subset)  
    {  
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);  
    }  
  
    // Output:  
    //  Calcium 20  
    //  Potassium 19  
    //  Scandium 21  
}  
  
private static List<Element> BuildList()  
{  
    return new List<Element>  
    {  
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  

<a name="BKMK_Sorting"></a>
## <a name="sorting-a-collection"></a><span data-ttu-id="2faf4-194">コレクションを並べ替える</span><span class="sxs-lookup"><span data-stu-id="2faf4-194">Sorting a Collection</span></span>  
 <span data-ttu-id="2faf4-195">次の例では、コレクションを並べ替えるための手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="2faf4-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="2faf4-196">この例は、`Car` に格納されている <xref:System.Collections.Generic.List%601> クラスのインスタンスの並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="2faf4-197">`Car` クラスは、<xref:System.IComparable%601> のメソッドの実装を必要とする <xref:System.IComparable%601.CompareTo%2A> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="2faf4-198"><xref:System.IComparable%601.CompareTo%2A> メソッドに対する各呼び出しは、並べ替えに使用される単一の比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="2faf4-199">`CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="2faf4-200">現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="2faf4-201">これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="2faf4-202">`ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="2faf4-203"><xref:System.Collections.Generic.List%601.Sort%2A> の <xref:System.Collections.Generic.List%601> メソッドへの呼び出しによって、`CompareTo` メソッドは `Car` 内の `List` オブジェクトに自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```csharp  
private static void ListCars()  
{  
    var cars = new List<Car>  
    {  
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},  
        { new Car() { Name = "car2", Color = "red", Speed = 50}},  
        { new Car() { Name = "car3", Color = "green", Speed = 10}},  
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},  
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},  
        { new Car() { Name = "car6", Color = "red", Speed = 60}},  
        { new Car() { Name = "car7", Color = "green", Speed = 50}}  
    };  
  
    // Sort the cars by color alphabetically, and then by speed  
    // in descending order.  
    cars.Sort();  
  
    // View all of the cars.  
    foreach (Car thisCar in cars)  
    {  
        Console.Write(thisCar.Color.PadRight(5) + " ");  
        Console.Write(thisCar.Speed.ToString() + " ");  
        Console.Write(thisCar.Name);  
        Console.WriteLine();  
    }  
  
    // Output:  
    //  blue  50 car4  
    //  blue  30 car5  
    //  blue  20 car1  
    //  green 50 car7  
    //  green 10 car3  
    //  red   60 car6  
    //  red   50 car2  
}  
  
public class Car : IComparable<Car>  
{  
    public string Name { get; set; }  
    public int Speed { get; set; }  
    public string Color { get; set; }  
  
    public int CompareTo(Car other)  
    {  
        // A call to this method makes a single comparison that is  
        // used for sorting.  
  
        // Determine the relative order of the objects being compared.  
        // Sort by color alphabetically, and then by speed in  
        // descending order.  
  
        // Compare the colors.  
        int compare;  
        compare = String.Compare(this.Color, other.Color, true);  
  
        // If the colors are the same, compare the speeds.  
        if (compare == 0)  
        {  
            compare = this.Speed.CompareTo(other.Speed);  
  
            // Use descending order for speed.  
            compare = -compare;  
        }  
  
        return compare;  
    }  
}  
```  
  
<a name="BKMK_CustomCollection"></a>
## <a name="defining-a-custom-collection"></a><span data-ttu-id="2faf4-204">カスタム コレクションを定義する</span><span class="sxs-lookup"><span data-stu-id="2faf4-204">Defining a Custom Collection</span></span>  
 <span data-ttu-id="2faf4-205"><xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Collections.IEnumerable> のインターフェイスを実装してコレクションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="2faf4-206">詳細については、「[方法 : foreach を使用してコレクション クラスにアクセスする](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faf4-206">For additional information, see [How to: Access a Collection Class with foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).</span></span>  
  
 <span data-ttu-id="2faf4-207">カスタム コレクションを定義できますが、通常は、.NET Framework に含まれるコレクションを使用することが推奨されます。これについては、このトピックの[コレクションの種類](#BKMK_KindsOfCollections)で既に説明されています。</span><span class="sxs-lookup"><span data-stu-id="2faf4-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="2faf4-208">次の例は、`AllColors` という名前のカスタム コレクション クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="2faf4-209">このクラスは、<xref:System.Collections.IEnumerable> メソッドの実装を必要とする <xref:System.Collections.IEnumerable.GetEnumerator%2A> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="2faf4-210">`GetEnumerator` メソッドは、`ColorEnumerator` クラスのインスタンスを戻します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="2faf4-211">`ColorEnumerator` は、<xref:System.Collections.IEnumerator> プロパティ、<xref:System.Collections.IEnumerator.Current%2A> メソッド、および <xref:System.Collections.IEnumerator.MoveNext%2A> メソッドの実装を必要とする <xref:System.Collections.IEnumerator.Reset%2A> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```csharp  
private static void ListColors()  
{  
    var colors = new AllColors();  
  
    foreach (Color theColor in colors)  
    {  
        Console.Write(theColor.Name + " ");  
    }  
    Console.WriteLine();  
    // Output: red blue green  
}  
  
// Collection class.  
public class AllColors : System.Collections.IEnumerable  
{  
    Color[] _colors =  
    {  
        new Color() { Name = "red" },  
        new Color() { Name = "blue" },  
        new Color() { Name = "green" }  
    };  
  
    public System.Collections.IEnumerator GetEnumerator()  
    {  
        return new ColorEnumerator(_colors);  
  
        // Instead of creating a custom enumerator, you could  
        // use the GetEnumerator of the array.  
        //return _colors.GetEnumerator();  
    }  
  
    // Custom enumerator.  
    private class ColorEnumerator : System.Collections.IEnumerator  
    {  
        private Color[] _colors;  
        private int _position = -1;  
  
        public ColorEnumerator(Color[] colors)  
        {  
            _colors = colors;  
        }  
  
        object System.Collections.IEnumerator.Current  
        {  
            get  
            {  
                return _colors[_position];  
            }  
        }  
  
        bool System.Collections.IEnumerator.MoveNext()  
        {  
            _position++;  
            return (_position < _colors.Length);  
        }  
  
        void System.Collections.IEnumerator.Reset()  
        {  
            _position = -1;  
        }  
    }  
}  
  
// Element class.  
public class Color  
{  
    public string Name { get; set; }  
}  
```  

<a name="BKMK_Iterators"></a> 
##  <a name="iterators"></a><span data-ttu-id="2faf4-212">Iterators</span><span class="sxs-lookup"><span data-stu-id="2faf4-212">Iterators</span></span>  
 <span data-ttu-id="2faf4-213">*反復子*は、コレクションに対するカスタム イテレーションを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="2faf4-214">反復子は、メソッドまたは `get` アクセサーのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="2faf4-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="2faf4-215">反復子は、[yield return](../../../csharp/language-reference/keywords/yield.md) ステートメントを使用して、コレクションの各要素を 1 回に 1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-215">An iterator uses a [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="2faf4-216">[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用して、反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-216">You call an iterator by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="2faf4-217">`foreach` ループの各イテレーションは、反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-217">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="2faf4-218">`yield return` ステートメントが反復子に到達すると、式が戻され、コードの現在の位置が保持されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-218">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="2faf4-219">次回、反復子が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-219">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="2faf4-220">詳細については、「[反復子 (C#)](../../../csharp/programming-guide/concepts/iterators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2faf4-220">For more information, see [Iterators (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="2faf4-221">次の例は、反復子メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="2faf4-221">The following example uses an iterator method.</span></span> <span data-ttu-id="2faf4-222">反復子メソッドには、[for](../../../csharp/language-reference/keywords/for.md) ループ内に `yield return` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="2faf4-222">The iterator method has a `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="2faf4-223">`ListEvenNumbers` メソッドでは、`foreach` ステートメント本文の各イテレーションが、反復子メソッドの呼び出しを作成し、これが次の `yield return` ステートメントに続行されます。</span><span class="sxs-lookup"><span data-stu-id="2faf4-223">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>  
  
```csharp  
private static void ListEvenNumbers()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    Console.WriteLine();  
    // Output: 6 8 10 12 14 16 18  
}  
  
private static IEnumerable<int> EvenSequence(  
    int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (var number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2faf4-224">参照</span><span class="sxs-lookup"><span data-stu-id="2faf4-224">See Also</span></span>  
 [<span data-ttu-id="2faf4-225">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="2faf4-225">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="2faf4-226">プログラミングの概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="2faf4-226">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)  
 [<span data-ttu-id="2faf4-227">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="2faf4-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="2faf4-228">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="2faf4-228">LINQ to Objects (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="2faf4-229">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2faf4-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="2faf4-230">コレクションとデータ構造体</span><span class="sxs-lookup"><span data-stu-id="2faf4-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="2faf4-231">コレクションの作成と操作</span><span class="sxs-lookup"><span data-stu-id="2faf4-231">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="2faf4-232">コレクション クラスの選択</span><span class="sxs-lookup"><span data-stu-id="2faf4-232">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="2faf4-233">コレクション内での比較と並べ替え</span><span class="sxs-lookup"><span data-stu-id="2faf4-233">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="2faf4-234">ジェネリック コレクションを使用する状況</span><span class="sxs-lookup"><span data-stu-id="2faf4-234">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
 [<span data-ttu-id="2faf4-235">方法: foreach を使用してコレクション クラスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="2faf4-235">How to: Access a Collection Class with foreach</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)
