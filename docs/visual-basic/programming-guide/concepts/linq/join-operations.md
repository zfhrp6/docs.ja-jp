---
title: "結合操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5b561f66069b042f3216c80c7b8b3a13df63647e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="join-operations-visual-basic"></a><span data-ttu-id="9ff46-102">結合操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ff46-102">Join Operations (Visual Basic)</span></span>
<span data-ttu-id="9ff46-103">A*結合*を別のデータ ソースの共通の属性を共有するオブジェクトと&1; つのデータ ソース内のオブジェクトの関連付けは、2 つのデータ ソースのです。</span><span class="sxs-lookup"><span data-stu-id="9ff46-103">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="9ff46-104">相互に直接の関連がない&2; つのデータ ソースを対象とするクエリにおいて、結合は重要な操作になります。</span><span class="sxs-lookup"><span data-stu-id="9ff46-104">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="9ff46-105">オブジェクト指向プログラミングでは、これは一方向の関係における逆の方向など、モデル化されていないオブジェクト間の相関関係を意味する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ff46-105">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="9ff46-106">一方向の関係の例として、City 型のプロパティを持つ Customer クラスがあるとします。ただし、City クラスには、Customer オブジェクトのコレクションを表すプロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="9ff46-106">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="9ff46-107">City オブジェクトのリストから各都市のすべての顧客を取得する場合は、結合演算を使用して顧客を検索できます。</span><span class="sxs-lookup"><span data-stu-id="9ff46-107">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="9ff46-108">LINQ フレームワークで提供されている結合メソッドは、 <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>。</xref:System.Linq.Enumerable.GroupJoin%2A> </xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="9ff46-108">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="9ff46-109">これらのメソッドでは、等キーが等しいかどうかに基づいて&2; つのデータ ソースに一致する結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="9ff46-109">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="9ff46-110">(比較に関して、Transact-SQL では、"小なり" 演算子などの "等値" 以外の結合演算子もサポートされます)。リレーショナル データベース用語で<xref:System.Linq.Enumerable.Join%2A>は内部結合、結合の種類のデータ セットで一致するオブジェクトのみが返される</xref:System.Linq.Enumerable.Join%2A>。</span><span class="sxs-lookup"><span data-stu-id="9ff46-110">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="9ff46-111"><xref:System.Linq.Enumerable.GroupJoin%2A>でもメソッドのリレーショナル データベース用語では、直接相当するものはありませんが、内部結合と左外部結合のスーパー セットを実装します</xref:System.Linq.Enumerable.GroupJoin%2A>。</span><span class="sxs-lookup"><span data-stu-id="9ff46-111">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="9ff46-112">左外部結合では、他のデータ ソースには相関関係を持つ要素があるない場合でも、最初 (左側) のデータ ソースの各要素を返す結合ですが、します。</span><span class="sxs-lookup"><span data-stu-id="9ff46-112">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="9ff46-113">次の図は、2 つのセットと、内部結合または左外部結合としてこれらのセットに含まれている要素の概念図を示しています。</span><span class="sxs-lookup"><span data-stu-id="9ff46-113">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 <span data-ttu-id="9ff46-114">![内側/外側を示す&2; つの重なり合う円します。] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")</span><span class="sxs-lookup"><span data-stu-id="9ff46-114">![Two overlapping circles showing inner&#47;outer.](../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ff46-115">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ff46-115">Methods</span></span>  
  
|<span data-ttu-id="9ff46-116">メソッド名</span><span class="sxs-lookup"><span data-stu-id="9ff46-116">Method Name</span></span>|<span data-ttu-id="9ff46-117">説明</span><span class="sxs-lookup"><span data-stu-id="9ff46-117">Description</span></span>|<span data-ttu-id="9ff46-118">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="9ff46-118">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="9ff46-119">説明</span><span class="sxs-lookup"><span data-stu-id="9ff46-119">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="9ff46-120">Join</span><span class="sxs-lookup"><span data-stu-id="9ff46-120">Join</span></span>|<span data-ttu-id="9ff46-121">キー セレクター関数に基づいて&2; つのシーケンスを結合し、値のペアを抽出します。</span><span class="sxs-lookup"><span data-stu-id="9ff46-121">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`From x In …, y In … Where x.a = y.a`<br /><br /> <span data-ttu-id="9ff46-122">または</span><span class="sxs-lookup"><span data-stu-id="9ff46-122">-or-</span></span><br /><br /> `Join … [As …]In … On …`|<span data-ttu-id="9ff46-123"><xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9ff46-123"><xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="9ff46-124"><xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9ff46-124"><xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="9ff46-125">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="9ff46-125">GroupJoin</span></span>|<span data-ttu-id="9ff46-126">キー セレクター関数に基づいて&2; つのシーケンスを結合し、各要素について結果として得られる一致をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="9ff46-126">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`Group Join … In … On …`|<span data-ttu-id="9ff46-127"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9ff46-127"><xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="9ff46-128"><xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9ff46-128"><xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ff46-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ff46-129">See Also</span></span>  
 <span data-ttu-id="9ff46-130"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="9ff46-130"><xref:System.Linq></span></span>   
<span data-ttu-id="9ff46-131"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="9ff46-131"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="9ff46-132"> [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="9ff46-132"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="9ff46-133"> [結合およびクロス積クエリを作成します。](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b) </span><span class="sxs-lookup"><span data-stu-id="9ff46-133"> [Formulate Joins and Cross-Product Queries](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b) </span></span>  
<span data-ttu-id="9ff46-134"> [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="9ff46-134"> [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) </span></span>  
<span data-ttu-id="9ff46-135"> [方法: 異種ファイル (LINQ) (Visual Basic の場合) からコンテンツを結合します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) </span><span class="sxs-lookup"><span data-stu-id="9ff46-135"> [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) </span></span>  
<span data-ttu-id="9ff46-136"> [方法: 複数のソース (LINQ) (Visual Basic の場合) からオブジェクトのコレクション設定](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)</span><span class="sxs-lookup"><span data-stu-id="9ff46-136"> [How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)</span></span>
