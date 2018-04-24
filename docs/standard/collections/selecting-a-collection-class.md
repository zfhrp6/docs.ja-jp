---
title: コレクション クラスの選択
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
caps.latest.revision: 20
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cede57d398930684a68ad15f3e6426939bba2e08
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="selecting-a-collection-class"></a><span data-ttu-id="f9e22-102">コレクション クラスの選択</span><span class="sxs-lookup"><span data-stu-id="f9e22-102">Selecting a Collection Class</span></span>
<span data-ttu-id="f9e22-103">コレクション クラスは慎重に選択してください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-103">Be sure to choose your collection class carefully.</span></span> <span data-ttu-id="f9e22-104">間違った型を使用すると、コレクションの使用が制限されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f9e22-104">Using the wrong type can restrict your use of the collection.</span></span> <span data-ttu-id="f9e22-105">一般に、.NET Framework バージョン 1.1 を特に対象としている場合を除いて、<xref:System.Collections> 名前空間にある型は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-105">In general, avoid using the types in the <xref:System.Collections> namespace unless you are specifically targeting .NET Framework version 1.1.</span></span> <span data-ttu-id="f9e22-106">タイプ セーフの強化や他の改善があるため、コレクションの汎用および同時実行バージョンをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f9e22-106">The generic and concurrent versions of the collections are to be preferred because of their greater type safety and other improvements.</span></span>  
  
 <span data-ttu-id="f9e22-107">以下の質問を検討します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-107">Consider the following questions:</span></span>  
  
-   <span data-ttu-id="f9e22-108">値が取得された後に要素が通常は破棄されるシーケンシャル リストが必要ですか。</span><span class="sxs-lookup"><span data-stu-id="f9e22-108">Do you need a sequential list where the element is typically discarded after its value is retrieved?</span></span>  
  
    -   <span data-ttu-id="f9e22-109">そうである場合は、先入れ先出し (FIFO) の動作が必要であれば、<xref:System.Collections.Queue> クラスまたは <xref:System.Collections.Generic.Queue%601> ジェネリック クラスの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-109">If yes, consider using the <xref:System.Collections.Queue> class or the <xref:System.Collections.Generic.Queue%601> generic class if you need first-in, first-out (FIFO) behavior.</span></span> <span data-ttu-id="f9e22-110">後入れ先出し (LIFO) の動作が必要であれば、<xref:System.Collections.Stack> クラスまたは <xref:System.Collections.Generic.Stack%601> ジェネリック クラスの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-110">Consider using the <xref:System.Collections.Stack> class or the <xref:System.Collections.Generic.Stack%601> generic class if you need last-in, first-out (LIFO) behavior.</span></span> <span data-ttu-id="f9e22-111">複数のスレッドから安全にアクセスできるように、同時実行バージョンの <xref:System.Collections.Concurrent.ConcurrentQueue%601> と <xref:System.Collections.Concurrent.ConcurrentStack%601> を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-111">For safe access from multiple threads, use the concurrent versions <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
    -   <span data-ttu-id="f9e22-112">それ以外の場合は、その他のコレクションの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-112">If not, consider using the other collections.</span></span>  
  
-   <span data-ttu-id="f9e22-113">FIFO や LIFO など特定の順序で要素にアクセスする必要がありますか。またはランダムにアクセスできますか。</span><span class="sxs-lookup"><span data-stu-id="f9e22-113">Do you need to access the elements in a certain order, such as FIFO, LIFO, or random?</span></span>  
  
    -   <span data-ttu-id="f9e22-114"><xref:System.Collections.Queue> クラスおよび <xref:System.Collections.Generic.Queue%601> または <xref:System.Collections.Concurrent.ConcurrentQueue%601> ジェネリック クラスは、FIFO アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-114">The <xref:System.Collections.Queue> class and the <xref:System.Collections.Generic.Queue%601> or <xref:System.Collections.Concurrent.ConcurrentQueue%601> generic class offer FIFO access.</span></span> <span data-ttu-id="f9e22-115">詳細については、「[スレッド セーフなコレクションを使用する状況](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-115">For more information, see [When to Use a Thread-Safe Collection](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).</span></span>  
  
    -   <span data-ttu-id="f9e22-116"><xref:System.Collections.Stack> クラスおよび <xref:System.Collections.Generic.Stack%601> または <xref:System.Collections.Concurrent.ConcurrentStack%601> ジェネリック クラスは、LIFO アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-116">The <xref:System.Collections.Stack> class and the <xref:System.Collections.Generic.Stack%601> or <xref:System.Collections.Concurrent.ConcurrentStack%601> generic class offer LIFO access.</span></span> <span data-ttu-id="f9e22-117">詳細については、「[スレッド セーフなコレクションを使用する状況](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-117">For more information, see [When to Use a Thread-Safe Collection](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).</span></span>  
  
    -   <span data-ttu-id="f9e22-118"><xref:System.Collections.Generic.LinkedList%601> ジェネリック クラスは、先頭から末尾または末尾から先頭への順次アクセスを可能にします。</span><span class="sxs-lookup"><span data-stu-id="f9e22-118">The <xref:System.Collections.Generic.LinkedList%601> generic class allows sequential access either from the head to the tail, or from the tail to the head.</span></span>  
  
-   <span data-ttu-id="f9e22-119">インデックスで各要素にアクセスする必要があるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="f9e22-119">Do you need to access each element by index?</span></span>  
  
    -   <span data-ttu-id="f9e22-120"><xref:System.Collections.ArrayList> と <xref:System.Collections.Specialized.StringCollection> クラス、および <xref:System.Collections.Generic.List%601> ジェネリック クラスは、要素の 0 から始まるインデックスによってその要素へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-120">The <xref:System.Collections.ArrayList> and <xref:System.Collections.Specialized.StringCollection> classes and the <xref:System.Collections.Generic.List%601> generic class offer access to their elements by the zero-based index of the element.</span></span>  
  
    -   <span data-ttu-id="f9e22-121"><xref:System.Collections.Hashtable>、<xref:System.Collections.SortedList>、<xref:System.Collections.Specialized.ListDictionary>、<xref:System.Collections.Specialized.StringDictionary> クラス、および <xref:System.Collections.Generic.Dictionary%602>、<xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラスは、要素のキーによってその要素へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-121">The <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, and <xref:System.Collections.Specialized.StringDictionary> classes, and the <xref:System.Collections.Generic.Dictionary%602> and <xref:System.Collections.Generic.SortedDictionary%602> generic classes offer access to their elements by the key of the element.</span></span>  
  
    -   <span data-ttu-id="f9e22-122"><xref:System.Collections.Specialized.NameObjectCollectionBase> と <xref:System.Collections.Specialized.NameValueCollection> クラス、および <xref:System.Collections.ObjectModel.KeyedCollection%602> と <xref:System.Collections.Generic.SortedList%602> ジェネリック クラスは、要素の 0 から始まるインデックスまたはキーのいずれかによって、その要素へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-122">The <xref:System.Collections.Specialized.NameObjectCollectionBase> and <xref:System.Collections.Specialized.NameValueCollection> classes, and the <xref:System.Collections.ObjectModel.KeyedCollection%602> and <xref:System.Collections.Generic.SortedList%602> generic classes offer access to their elements by either the zero-based index or the key of the element.</span></span>  
  
-   <span data-ttu-id="f9e22-123">各要素に含まれることになるのは、1 つの値、1 つのキーと 1 つの値の組み合わせ、または 1 つのキーと複数の値の組み合わせのどれですか。</span><span class="sxs-lookup"><span data-stu-id="f9e22-123">Will each element contain one value, a combination of one key and one value, or a combination of one key and multiple values?</span></span>  
  
    -   <span data-ttu-id="f9e22-124">1 つの値: <xref:System.Collections.IList> インターフェイスまたは <xref:System.Collections.Generic.IList%601> ジェネリック インターフェイスに基づくいずれかのコレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-124">One value: Use any of the collections based on the <xref:System.Collections.IList> interface or the <xref:System.Collections.Generic.IList%601> generic interface.</span></span>  
  
    -   <span data-ttu-id="f9e22-125">1 つのキーと 1 つの値: <xref:System.Collections.IDictionary> インターフェイスまたは <xref:System.Collections.Generic.IDictionary%602> ジェネリック インターフェイスに基づくいずれかのコレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-125">One key and one value: Use any of the collections based on the <xref:System.Collections.IDictionary> interface or the <xref:System.Collections.Generic.IDictionary%602> generic interface.</span></span>  
  
    -   <span data-ttu-id="f9e22-126">埋め込みのキーを持つ 1 つの値: <xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-126">One value with embedded key: Use the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>  
  
    -   <span data-ttu-id="f9e22-127">複数の値を持つ 1 つのキー: <xref:System.Collections.Specialized.NameValueCollection> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-127">One key and multiple values: Use the <xref:System.Collections.Specialized.NameValueCollection> class.</span></span>  
  
-   <span data-ttu-id="f9e22-128">要素を入力されたときとは異なる方法で並べ替える必要がありますか。</span><span class="sxs-lookup"><span data-stu-id="f9e22-128">Do you need to sort the elements differently from how they were entered?</span></span>  
  
    -   <span data-ttu-id="f9e22-129"><xref:System.Collections.Hashtable> クラスは、ハッシュ コードによってその要素を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="f9e22-129">The <xref:System.Collections.Hashtable> class sorts its elements by their hash codes.</span></span>  
  
    -   <span data-ttu-id="f9e22-130"><xref:System.Collections.SortedList> クラスおよび <xref:System.Collections.Generic.SortedDictionary%602> と <xref:System.Collections.Generic.SortedList%602> ジェネリック クラスは、<xref:System.Collections.IComparer> インターフェイスおよび <xref:System.Collections.Generic.IComparer%601> ジェネリック インターフェイスの実装に基づいて、キーによってその要素を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="f9e22-130">The <xref:System.Collections.SortedList> class and the <xref:System.Collections.Generic.SortedDictionary%602> and <xref:System.Collections.Generic.SortedList%602> generic classes sort their elements by the key, based on implementations of the <xref:System.Collections.IComparer> interface and the <xref:System.Collections.Generic.IComparer%601> generic interface.</span></span>  
  
    -   <span data-ttu-id="f9e22-131"><xref:System.Collections.ArrayList> は、<xref:System.Collections.IComparer> 実装をパラメーターとして受け取る、<xref:System.Collections.ArrayList.Sort%2A> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-131"><xref:System.Collections.ArrayList> provides a <xref:System.Collections.ArrayList.Sort%2A> method that takes an <xref:System.Collections.IComparer> implementation as a parameter.</span></span> <span data-ttu-id="f9e22-132">それに対応するジェネリックである <xref:System.Collections.Generic.List%601> ジェネリック クラスは、<xref:System.Collections.Generic.IComparer%601> ジェネリック インターフェイスの実装をパラメーターとして受け取る、<xref:System.Collections.Generic.List%601.Sort%2A> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-132">Its generic counterpart, the <xref:System.Collections.Generic.List%601> generic class, provides a <xref:System.Collections.Generic.List%601.Sort%2A> method that takes an implementation of the <xref:System.Collections.Generic.IComparer%601> generic interface as a parameter.</span></span>  
  
-   <span data-ttu-id="f9e22-133">高速な検索と情報の取得が必要ですか。</span><span class="sxs-lookup"><span data-stu-id="f9e22-133">Do you need fast searches and retrieval of information?</span></span>  
  
    -   <span data-ttu-id="f9e22-134"><xref:System.Collections.Specialized.ListDictionary> は、小規模なコレクション (10 個以下のアイテム) では <xref:System.Collections.Hashtable> より高速です。</span><span class="sxs-lookup"><span data-stu-id="f9e22-134"><xref:System.Collections.Specialized.ListDictionary> is faster than <xref:System.Collections.Hashtable> for small collections (10 items or fewer).</span></span> <span data-ttu-id="f9e22-135"><xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスは、<xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラスよりも高速の参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-135">The <xref:System.Collections.Generic.Dictionary%602> generic class provides faster lookup than the <xref:System.Collections.Generic.SortedDictionary%602> generic class.</span></span> <span data-ttu-id="f9e22-136">マルチスレッドの実装は <xref:System.Collections.Concurrent.ConcurrentDictionary%602> です。</span><span class="sxs-lookup"><span data-stu-id="f9e22-136">The multi-threaded implementation is <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span> <span data-ttu-id="f9e22-137"><xref:System.Collections.Concurrent.ConcurrentBag%601> は、順序指定されていないデータのために、高速なマルチスレッドの挿入を提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-137"><xref:System.Collections.Concurrent.ConcurrentBag%601> provides fast multi-threaded insertion for unordered data.</span></span> <span data-ttu-id="f9e22-138">両方のマルチスレッドのタイプについては、「[スレッド セーフなコレクションを使用する状況](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-138">For more information about both multi-threaded types, see [When to Use a Thread-Safe Collection](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).</span></span>  
  
-   <span data-ttu-id="f9e22-139">文字列だけを受け入れるコレクションは必要ですか。</span><span class="sxs-lookup"><span data-stu-id="f9e22-139">Do you need collections that accept only strings?</span></span>  
  
    -   <span data-ttu-id="f9e22-140"><xref:System.Collections.Specialized.StringCollection> (<xref:System.Collections.IList> に基づく) および <xref:System.Collections.Specialized.StringDictionary> (<xref:System.Collections.IDictionary> に基づく) は、<xref:System.Collections.Specialized> 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="f9e22-140"><xref:System.Collections.Specialized.StringCollection> (based on <xref:System.Collections.IList>) and <xref:System.Collections.Specialized.StringDictionary> (based on <xref:System.Collections.IDictionary>) are in the <xref:System.Collections.Specialized> namespace.</span></span>  
  
    -   <span data-ttu-id="f9e22-141">さらに、ジェネリック型の引数として <xref:System.String> クラスを指定することにより、<xref:System.Collections.Generic> 名前空間にある任意のジェネリック コレクション クラスを厳密に型指定された文字列コレクションとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9e22-141">In addition, you can use any of the generic collection classes in the <xref:System.Collections.Generic> namespace as strongly typed string collections by specifying the <xref:System.String> class for their generic type arguments.</span></span>  
  
## <a name="linq-to-objects-and-plinq"></a><span data-ttu-id="f9e22-142">LINQ to Objects および PLINQ</span><span class="sxs-lookup"><span data-stu-id="f9e22-142">LINQ to Objects and PLINQ</span></span>  
 <span data-ttu-id="f9e22-143">LINQ to Objects により、開発者は、オブジェクト型で <xref:System.Collections.IEnumerable> または <xref:System.Collections.Generic.IEnumerable%601> を実装している限り、LINQ クエリを使用してインメモリ オブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f9e22-143">LINQ to Objects enables developers to use LINQ queries to access in-memory objects as long as the object type implements <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f9e22-144">LINQ クエリはデータ アクセス用の一般的なパターンです。通常、これは標準の `foreach` ループよりも簡潔で読みやすく、フィルター処理、並べ替え、およびグループ化機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="f9e22-144">LINQ queries provide a common pattern for accessing data, are typically more concise and readable than standard `foreach` loops, and provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="f9e22-145">詳細については、「[LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-145">For more information, see [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).</span></span>  
  
 <span data-ttu-id="f9e22-146">PLINQ は、マルチコア コンピューターをより効率的に使用することにより、多くのシナリオでより高速にクエリを実行できる LINQ to Objects の並列実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="f9e22-146">PLINQ provides a parallel implementation of LINQ to Objects that can offer faster query execution in many scenarios, through more efficient use of multi-core computers.</span></span> <span data-ttu-id="f9e22-147">詳細については、「[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9e22-147">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e22-148">参照</span><span class="sxs-lookup"><span data-stu-id="f9e22-148">See Also</span></span>  
 <xref:System.Collections>  
 <xref:System.Collections.Specialized>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="f9e22-149">スレッドセーフなコレクション</span><span class="sxs-lookup"><span data-stu-id="f9e22-149">Thread-Safe Collections</span></span>](../../../docs/standard/collections/thread-safe/index.md)
