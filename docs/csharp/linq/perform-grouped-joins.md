---
title: グループ結合の実行
description: グループ結合を実行する方法。
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="228a7-103">グループ結合の実行</span><span class="sxs-lookup"><span data-stu-id="228a7-103">Perform grouped joins</span></span>

<span data-ttu-id="228a7-104">グループ結合は、階層データ構造を作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="228a7-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="228a7-105">これは、最初のコレクションの各要素と、2 番目のコレクションの相関関係を持つ要素のセットを組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="228a7-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>  
  
 <span data-ttu-id="228a7-106">たとえば、`Student` という名前のクラスまたはリレーショナル データベース テーブルに、`Id` と `Name` という 2 つのフィールドが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="228a7-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="228a7-107">`Course` という名前の 2 番目のクラスまたはリレーショナル データベース テーブルには、`StudentId` と `CourseTitle` という 2 つのフィールドが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="228a7-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="228a7-108">この 2 つのデータ ソースのグループ結合は、`Student.Id` と `Course.StudentId` の一致に基づいて、`Course` オブジェクトのコレクションを持つ各 `Student` をグループ化します (コレクションは空の場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="228a7-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="228a7-109">最初のコレクションの各要素は、2 番目のコレクションに相関関係を持つ要素があるかどうかにかかわらず、グループ結合の結果セットに表示されます。</span><span class="sxs-lookup"><span data-stu-id="228a7-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="228a7-110">相関関係を持つ要素が見つからない場合、その要素の相関関係を持つ要素のシーケンスは空です。</span><span class="sxs-lookup"><span data-stu-id="228a7-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="228a7-111">そのため、結果セレクターは最初のコレクションのすべての要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="228a7-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="228a7-112">これは、非グループ結合の結果セレクターとは異なります。非グループ結合の結果セレクターは、2 番目のコレクションに一致するものがない最初のコレクションの要素にアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="228a7-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>  
  
 <span data-ttu-id="228a7-113">このトピックの最初の例では、グループ結合を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="228a7-113">The first example in this topic shows you how to perform a group join.</span></span> <span data-ttu-id="228a7-114">2 つ目の例では、グループ結合を使用して XML 要素を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="228a7-114">The second example shows you how to use a group join to create XML elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="228a7-115">例</span><span class="sxs-lookup"><span data-stu-id="228a7-115">Example</span></span>  
  
### <a name="group-join-example"></a><span data-ttu-id="228a7-116">グループ結合の例</span><span class="sxs-lookup"><span data-stu-id="228a7-116">Group join example</span></span>  
 <span data-ttu-id="228a7-117">次の例では、`Pet.Owner` プロパティと一致する `Person` に基づいて、`Person` 型と `Pet` 型のオブジェクトのグループ結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="228a7-117">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="228a7-118">一致ごとに要素のペアを生成する非グループ結合と異なり、グループ結合は最初のコレクションの要素ごとに 1 つのオブジェクト (この例では `Person` オブジェクト) のみを作成します。</span><span class="sxs-lookup"><span data-stu-id="228a7-118">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="228a7-119">2 番目のコレクションの対応する要素 (この例では `Pet` オブジェクト) が 1 つのコレクションにグループ化されます。</span><span class="sxs-lookup"><span data-stu-id="228a7-119">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="228a7-120">最後に、結果セレクター機能により、`Person.FirstName` と、`Pet` オブジェクトのコレクションで構成される一致ごとに匿名型が作成されます。</span><span class="sxs-lookup"><span data-stu-id="228a7-120">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="228a7-121">例</span><span class="sxs-lookup"><span data-stu-id="228a7-121">Example</span></span>  
  
### <a name="group-join-to-create-xml-example"></a><span data-ttu-id="228a7-122">XML を作成するグループ結合の例</span><span class="sxs-lookup"><span data-stu-id="228a7-122">Group join to create XML example</span></span>  
 <span data-ttu-id="228a7-123">グループ結合は、LINQ to XML を使用した XML の作成に適しています。</span><span class="sxs-lookup"><span data-stu-id="228a7-123">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="228a7-124">次の例は前の例に似ていますが、匿名型を作成するのではなく、結果セレクター機能により、結合されたオブジェクトを表す XML 要素を作成する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="228a7-124">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="228a7-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="228a7-125">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="228a7-126">内部結合の実行</span><span class="sxs-lookup"><span data-stu-id="228a7-126">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="228a7-127">左外部結合の実行</span><span class="sxs-lookup"><span data-stu-id="228a7-127">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="228a7-128">匿名型</span><span class="sxs-lookup"><span data-stu-id="228a7-128">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
