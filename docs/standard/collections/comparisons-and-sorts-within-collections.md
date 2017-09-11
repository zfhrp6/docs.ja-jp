---
title: "コレクション内での比較と並べ替え"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1033d7ec64641dd5904372bc05bd2076efe60d39
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="96196-102">コレクション内での比較と並べ替え</span><span class="sxs-lookup"><span data-stu-id="96196-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="96196-103"><xref:System.Collections> クラスは、削除する要素を検索するか、キーと値のペアの値を返すかに関係なく、コレクションの管理に関連するほぼすべての処理において比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="96196-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="96196-104">通常、コレクションは等値比較子か順序比較子、またはその両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="96196-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="96196-105">比較には 2 つのコンストラクターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="96196-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="96196-106">等価性のチェック</span><span class="sxs-lookup"><span data-stu-id="96196-106">Checking for equality</span></span>  
 <span data-ttu-id="96196-107">`Contains`、 <xref:System.Collections.IList.IndexOf%2A>、 <xref:System.Collections.Generic.List%601.LastIndexOf%2A>、 `Remove` などのメソッドは、コレクション要素に対して等値比較子を使用します。</span><span class="sxs-lookup"><span data-stu-id="96196-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="96196-108">コレクションがジェネリックの場合、次のガイドラインに従ってアイテムの等価性が比較されます。</span><span class="sxs-lookup"><span data-stu-id="96196-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
-   <span data-ttu-id="96196-109">T 型で <xref:System.IEquatable%601> ジェネリック インターフェイスが実装されている場合、等値比較子はそのインターフェイスの <xref:System.IEquatable%601.Equals%2A> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="96196-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
-   <span data-ttu-id="96196-110">T 型で <xref:System.IEquatable%601>が実装されていない場合、 <xref:System.Object.Equals%2A?displayProperty=fullName> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="96196-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=fullName> is used.</span></span>  
  
 <span data-ttu-id="96196-111">また、ディクショナリ コレクションの一部のコンストラクター オーバーロードでは、 <xref:System.Collections.Generic.IEqualityComparer%601> 実装が受け取られ、これを使用してキーの等価性が比較されます。</span><span class="sxs-lookup"><span data-stu-id="96196-111">In addition, Some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="96196-112">例については、 <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=fullName> コンストラクターに関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96196-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=fullName> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="96196-113">並べ替え順序の決定</span><span class="sxs-lookup"><span data-stu-id="96196-113">Determining sort order</span></span>  
 <span data-ttu-id="96196-114">`BinarySearch` 、 `Sort` などのメソッドは、コレクション要素に対して順序比較子を使用します。</span><span class="sxs-lookup"><span data-stu-id="96196-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="96196-115">コレクションの要素間または要素と指定された値との間で比較を実行できます。</span><span class="sxs-lookup"><span data-stu-id="96196-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="96196-116">オブジェクトの比較には、 `default comparer` と `explicit comparer`の概念が適用されます。</span><span class="sxs-lookup"><span data-stu-id="96196-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="96196-117">既定の比較子は、比較される 1 つ以上のオブジェクトに依存して **IComparable** インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="96196-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="96196-118">リスト コレクションの値として使用されるか、またはディクショナリ コレクションのキーとして使用されるすべてのクラスで、 **IComparable** を実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="96196-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="96196-119">ジェネリック コレクションの場合、等価比較は次の基準に従って決定されます。</span><span class="sxs-lookup"><span data-stu-id="96196-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
-   <span data-ttu-id="96196-120">T 型で <xref:System.IComparable%601?displayProperty=fullName> ジェネリック インターフェイスが実装されている場合、既定の比較子はそのインターフェイスの <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=fullName> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="96196-120">If type T implements the <xref:System.IComparable%601?displayProperty=fullName> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=fullName> method of that interface</span></span>  
  
-   <span data-ttu-id="96196-121">T 型で非ジェネリックの <xref:System.IComparable?displayProperty=fullName> インターフェイスが実装されている場合、既定の比較子はそのインターフェイスの <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=fullName> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="96196-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=fullName> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=fullName> method of that interface.</span></span>  
  
-   <span data-ttu-id="96196-122">T 型でいずれのインターフェイスも実装されていない場合、既定の比較子は存在せず、比較子または比較デリゲートを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96196-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="96196-123">明示的な比較を指定するために、一部のメソッドではパラメーターとして **IComparer** 実装を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="96196-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="96196-124">たとえば、 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=fullName> メソッドは <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> 実装を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="96196-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=fullName> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> implementation.</span></span>  
  
 <span data-ttu-id="96196-125">システムの現在のカルチャ設定は、コレクション内の比較と並べ替えに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="96196-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="96196-126">既定では、 **Collections** クラスの比較と並べ替えはカルチャに依存します。</span><span class="sxs-lookup"><span data-stu-id="96196-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="96196-127">カルチャ設定を無視して一貫した比較と並べ替えの結果を得るには、 <xref:System.Globalization.CultureInfo.InvariantCulture%2A> を受け取るメンバー オーバーロードと共に <xref:System.Globalization.CultureInfo>を使用します。</span><span class="sxs-lookup"><span data-stu-id="96196-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="96196-128">詳細については、次のトピックを参照してください。 [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) および [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="96196-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="96196-129">等価性と並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="96196-129">Equality and sort example</span></span>  
 <span data-ttu-id="96196-130">次のコードは、単純なビジネス オブジェクトでの <xref:System.IEquatable%601> と <xref:System.IComparable%601> の実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="96196-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="96196-131">また、オブジェクトがリストに格納され、並べ替えられている場合、 <xref:System.Collections.Generic.List%601.Sort> メソッドを呼び出すと、結果的に `Part` 型の既定の比較子と、匿名メソッドを使用して実装された <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> メソッドを使用することになります。</span><span class="sxs-lookup"><span data-stu-id="96196-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 <span data-ttu-id="96196-132">[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)] [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="96196-132">[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)] [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96196-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="96196-133">See Also</span></span>  
 <xref:System.Collections.IComparer>   
 <xref:System.IEquatable%601>   
 <xref:System.Collections.Generic.IComparer%601>   
 <xref:System.IComparable>   
 <xref:System.IComparable%601>

