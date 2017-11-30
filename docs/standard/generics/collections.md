---
title: ".NET Framework のジェネリック コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94da20072f793e137b0b7545c1a658ed20537a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="c44a6-102">.NET Framework のジェネリック コレクション</span><span class="sxs-lookup"><span data-stu-id="c44a6-102">Generic Collections in the .NET Framework</span></span>
<span data-ttu-id="c44a6-103">このトピックでは、.NET Framework のジェネリック コレクション クラスとその他のジェネリック型について概説します。</span><span class="sxs-lookup"><span data-stu-id="c44a6-103">This topic provides an overview of the generic collection classes and other generic types in the .NET Framework.</span></span>  
  
## <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="c44a6-104">.NET Framework のジェネリック コレクション</span><span class="sxs-lookup"><span data-stu-id="c44a6-104">Generic Collections in the .NET Framework</span></span>  
 <span data-ttu-id="c44a6-105">.NET Framework クラス ライブラリでは、<xref:System.Collections.Generic> および <xref:System.Collections.ObjectModel> の名前空間に多数のジェネリック コレクション クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="c44a6-105">The .NET Framework class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="c44a6-106">これらのクラスの詳細については、次を参照してください。[よく使用されるコレクション型](../../../docs/standard/collections/commonly-used-collection-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="c44a6-106">For more information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="c44a6-107">System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="c44a6-107">System.Collections.Generic</span></span>  
 <span data-ttu-id="c44a6-108">ジェネリック コレクション型の多くは、非ジェネリック型に直接類似しています。</span><span class="sxs-lookup"><span data-stu-id="c44a6-108">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="c44a6-109"><xref:System.Collections.Generic.Dictionary%602> は、<xref:System.Collections.Hashtable> のジェネリック バージョンです。これは列挙体のために <xref:System.Collections.DictionaryEntry> ではなくジェネリック構造体 <xref:System.Collections.Generic.KeyValuePair%602> を使用します。</span><span class="sxs-lookup"><span data-stu-id="c44a6-109"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="c44a6-110"><xref:System.Collections.Generic.List%601> は <xref:System.Collections.ArrayList> のジェネリック バージョンです。</span><span class="sxs-lookup"><span data-stu-id="c44a6-110"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="c44a6-111">ジェネリックの <xref:System.Collections.Generic.Queue%601> および <xref:System.Collections.Generic.Stack%601> クラスには、非ジェネリックのバージョンに対応するものがあります。</span><span class="sxs-lookup"><span data-stu-id="c44a6-111">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="c44a6-112"><xref:System.Collections.Generic.SortedList%602> には、ジェネリックおよび非ジェネリックのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="c44a6-112">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="c44a6-113">どちらのバージョンも、ディクショナリとリストのハイブリッドです。</span><span class="sxs-lookup"><span data-stu-id="c44a6-113">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="c44a6-114"><xref:System.Collections.Generic.SortedDictionary%602> ジェネリック クラスは純粋なディクショナリであり、対応する非ジェネリックのバージョンはありません。</span><span class="sxs-lookup"><span data-stu-id="c44a6-114">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="c44a6-115"><xref:System.Collections.Generic.LinkedList%601> ジェネリック クラスは、実際のリンク リストです。</span><span class="sxs-lookup"><span data-stu-id="c44a6-115">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="c44a6-116">これには、対応する非ジェネリックのバージョンはありません。</span><span class="sxs-lookup"><span data-stu-id="c44a6-116">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="c44a6-117">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="c44a6-117">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="c44a6-118"><xref:System.Collections.ObjectModel.Collection%601> ジェネリック クラスは、独自のジェネリック コレクション型を派生させるための基本クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c44a6-118">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="c44a6-119"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> クラスは、<xref:System.Collections.Generic.IList%601> ジェネリック インターフェイスを実装する任意の型から、読み取り専用のコレクションを生成するための簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="c44a6-119">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="c44a6-120"><xref:System.Collections.ObjectModel.KeyedCollection%602> ジェネリック クラスは、独自のキーを含むオブジェクトを格納するための方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="c44a6-120">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="c44a6-121">その他のジェネリック型</span><span class="sxs-lookup"><span data-stu-id="c44a6-121">Other Generic Types</span></span>  
 <span data-ttu-id="c44a6-122"><xref:System.Nullable%601> ジェネリック構造体により、`null` が割り当て可能であるかのように値型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c44a6-122">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="c44a6-123">これは、値型が含まれるフィールドが欠落している可能性のあるデータベース クエリで作業するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="c44a6-123">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="c44a6-124">ジェネリック型パラメーターには、任意の値型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c44a6-124">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c44a6-125">C# には null 許容型の構文があるので、その言語では <xref:System.Nullable%601> を明示的に使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c44a6-125">In C# it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span>  
  
 <span data-ttu-id="c44a6-126"><xref:System.ArraySegment%601> ジェネリック構造体は、任意の型の 0 から始まる 1 次元の配列内で、要素の範囲を区切る方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="c44a6-126">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="c44a6-127">ジェネリック型パラメーターは、配列の要素の型です。</span><span class="sxs-lookup"><span data-stu-id="c44a6-127">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="c44a6-128"><xref:System.EventHandler%601> ジェネリック デリゲートにより、イベントが [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] によって使用されるイベント処理パターンに従う場合に、イベントを処理するためにデリゲート型を宣言する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c44a6-128">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="c44a6-129">たとえば、イベントのデータを保持するために、<xref:System.EventArgs> から派生した `MyEventArgs` クラスを作成したとします。</span><span class="sxs-lookup"><span data-stu-id="c44a6-129">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="c44a6-130">その場合、イベントを次のように宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c44a6-130">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="c44a6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="c44a6-131">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="c44a6-132">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="c44a6-132">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="c44a6-133">配列とリストの操作に使用する汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="c44a6-133">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="c44a6-134">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c44a6-134">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
