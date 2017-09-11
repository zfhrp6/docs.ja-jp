---
title: "データのグループ化 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2cf1b228a5ff4120bdf3b97a7ec9308f11d7b8ee
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="grouping-data-c"></a><span data-ttu-id="0b3e1-102">データのグループ化 (C#)</span><span class="sxs-lookup"><span data-stu-id="0b3e1-102">Grouping Data (C#)</span></span>
<span data-ttu-id="0b3e1-103">グループ化とは、各グループの要素が共通の属性を持つようにデータをグループに分ける操作を指します。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="0b3e1-104">次の図は、文字のシーケンスをグループ化した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="0b3e1-105">各グループのキーは文字です。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="0b3e1-106">![LINQ グループ化操作](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="0b3e1-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="0b3e1-107">次のセクションでは、データ要素をグループ化する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b3e1-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="0b3e1-108">Methods</span></span>  
  
|<span data-ttu-id="0b3e1-109">メソッド名</span><span class="sxs-lookup"><span data-stu-id="0b3e1-109">Method Name</span></span>|<span data-ttu-id="0b3e1-110">説明</span><span class="sxs-lookup"><span data-stu-id="0b3e1-110">Description</span></span>|<span data-ttu-id="0b3e1-111">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="0b3e1-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="0b3e1-112">説明</span><span class="sxs-lookup"><span data-stu-id="0b3e1-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="0b3e1-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="0b3e1-113">GroupBy</span></span>|<span data-ttu-id="0b3e1-114">共通の属性を共有する要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="0b3e1-115">各グループは <xref:System.Linq.IGrouping%602> オブジェクトによって表されます。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="0b3e1-116">または</span><span class="sxs-lookup"><span data-stu-id="0b3e1-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName>|  
|<span data-ttu-id="0b3e1-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="0b3e1-117">ToLookup</span></span>|<span data-ttu-id="0b3e1-118">キー セレクター関数に基づいて、<xref:System.Linq.Lookup%602> (一対多の辞書) に要素を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="0b3e1-119">該当なし。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="0b3e1-120">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="0b3e1-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="0b3e1-121">次のコード例では、`group by` 句を使用して、偶数か奇数かによってリスト内の整数をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="0b3e1-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b3e1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b3e1-122">See Also</span></span>  
 <span data-ttu-id="0b3e1-123"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="0b3e1-123"><xref:System.Linq></span></span>   
 <span data-ttu-id="0b3e1-124">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="0b3e1-124">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="0b3e1-125">[group 句](../../../../csharp/language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0b3e1-125">[group clause](../../../../csharp/language-reference/keywords/group-clause.md) </span></span>  
 <span data-ttu-id="0b3e1-126">[方法: 入れ子になったグループを作成する](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="0b3e1-126">[How to: Create a Nested Group](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span></span>  
 <span data-ttu-id="0b3e1-127">[方法: 拡張子別にファイルをグループ化する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span><span class="sxs-lookup"><span data-stu-id="0b3e1-127">[How to: Group Files by Extension (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span></span>  
 <span data-ttu-id="0b3e1-128">[方法: クエリ結果をグループ化する](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span><span class="sxs-lookup"><span data-stu-id="0b3e1-128">[How to: Group Query Results](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span></span>  
 <span data-ttu-id="0b3e1-129">[方法: グループ化操作でサブクエリを実行する](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md) </span><span class="sxs-lookup"><span data-stu-id="0b3e1-129">[How to: Perform a Subquery on a Grouping Operation](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md) </span></span>  
 [<span data-ttu-id="0b3e1-130">方法: グループを使用して 1 つのファイルを複数のファイルに分割する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0b3e1-130">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)

