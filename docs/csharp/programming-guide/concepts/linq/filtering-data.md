---
title: "データのフィルター処理 (C#)"
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
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: defa6716f677c44da5dd27cb64b3b1d140a65272
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="filtering-data-c"></a><span data-ttu-id="26c55-102">データのフィルター処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="26c55-102">Filtering Data (C#)</span></span>
<span data-ttu-id="26c55-103">フィルター処理とは、特定の条件を満たす要素のみが含まれるように結果セットを限定する操作のことです。</span><span class="sxs-lookup"><span data-stu-id="26c55-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="26c55-104">選択とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="26c55-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="26c55-105">次の図は、文字のシーケンスをフィルター処理した結果を示したものです。</span><span class="sxs-lookup"><span data-stu-id="26c55-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="26c55-106">フィルター処理操作の述語では、文字が "A" でなければならないことが指定されています。</span><span class="sxs-lookup"><span data-stu-id="26c55-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="26c55-107">![LINQ フィルター処理操作](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="26c55-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="26c55-108">次のセクションでは、選択を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="26c55-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26c55-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="26c55-109">Methods</span></span>  
  
|<span data-ttu-id="26c55-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="26c55-110">Method Name</span></span>|<span data-ttu-id="26c55-111">説明</span><span class="sxs-lookup"><span data-stu-id="26c55-111">Description</span></span>|<span data-ttu-id="26c55-112">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="26c55-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="26c55-113">説明</span><span class="sxs-lookup"><span data-stu-id="26c55-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="26c55-114">OfType</span><span class="sxs-lookup"><span data-stu-id="26c55-114">OfType</span></span>|<span data-ttu-id="26c55-115">指定した型にキャストできるかどうかにより、値を選択します。</span><span class="sxs-lookup"><span data-stu-id="26c55-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="26c55-116">該当なし。</span><span class="sxs-lookup"><span data-stu-id="26c55-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|<span data-ttu-id="26c55-117">Where</span><span class="sxs-lookup"><span data-stu-id="26c55-117">Where</span></span>|<span data-ttu-id="26c55-118">述語関数に基づいて値を選択します。</span><span class="sxs-lookup"><span data-stu-id="26c55-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="26c55-119">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="26c55-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="26c55-120">次の例では、`where` 句を使って、配列から特定の長さを持つ文字列をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="26c55-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="26c55-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="26c55-121">See Also</span></span>  
 <span data-ttu-id="26c55-122"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="26c55-122"><xref:System.Linq></span></span>   
 <span data-ttu-id="26c55-123">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="26c55-123">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="26c55-124">[where 句](../../../../csharp/language-reference/keywords/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="26c55-124">[where clause](../../../../csharp/language-reference/keywords/where-clause.md) </span></span>  
 <span data-ttu-id="26c55-125">[方法: 実行時に述語フィルターを動的に指定する](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="26c55-125">[How to: Dynamically Specify Predicate Filters at Runtime](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span></span>  
 <span data-ttu-id="26c55-126">[方法: リフレクションを使用してアセンブリのメタデータを照会する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span><span class="sxs-lookup"><span data-stu-id="26c55-126">[How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span></span>  
 <span data-ttu-id="26c55-127">[方法: 指定された属性または名前のファイルを照会する (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span><span class="sxs-lookup"><span data-stu-id="26c55-127">[How to: Query for Files with a Specified Attribute or Name (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span></span>  
 [<span data-ttu-id="26c55-128">方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="26c55-128">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

