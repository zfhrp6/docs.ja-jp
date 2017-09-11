---
title: "(Visual Basic) のデータをフィルター処理 |Microsoft ドキュメント"
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
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fa2d3b6c5b81f137ab3a81f9b18707bb2da91f6e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="302b1-102">データのフィルター処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="302b1-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="302b1-103">フィルター処理は、指定した条件を満たす要素のみを含めるように結果セットを制限する操作です。</span><span class="sxs-lookup"><span data-stu-id="302b1-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="302b1-104">選択範囲でとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="302b1-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="302b1-105">次の図は、文字のシーケンスをフィルター処理結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="302b1-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="302b1-106">フィルター処理するための述語では、文字は 'A' である必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="302b1-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="302b1-107">![LINQ の操作をフィルタ リング](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="302b1-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="302b1-108">選択を実行する標準クエリ演算子メソッドは、次のように記載されています。</span><span class="sxs-lookup"><span data-stu-id="302b1-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="302b1-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="302b1-109">Methods</span></span>  
  
|<span data-ttu-id="302b1-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="302b1-110">Method Name</span></span>|<span data-ttu-id="302b1-111">説明</span><span class="sxs-lookup"><span data-stu-id="302b1-111">Description</span></span>|<span data-ttu-id="302b1-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="302b1-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="302b1-113">説明</span><span class="sxs-lookup"><span data-stu-id="302b1-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="302b1-114">OfType</span><span class="sxs-lookup"><span data-stu-id="302b1-114">OfType</span></span>|<span data-ttu-id="302b1-115">指定した型にキャストするかどうかによって、値を選択します。</span><span class="sxs-lookup"><span data-stu-id="302b1-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="302b1-116">該当なし。</span><span class="sxs-lookup"><span data-stu-id="302b1-116">Not applicable.</span></span>|<span data-ttu-id="302b1-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="302b1-117"><xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="302b1-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="302b1-118"><xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="302b1-119">Where</span><span class="sxs-lookup"><span data-stu-id="302b1-119">Where</span></span>|<span data-ttu-id="302b1-120">述語関数に基づいた値を選択します。</span><span class="sxs-lookup"><span data-stu-id="302b1-120">Selects values that are based on a predicate function.</span></span>|`Where`|<span data-ttu-id="302b1-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="302b1-121"><xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="302b1-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="302b1-122"><xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="302b1-123">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="302b1-123">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="302b1-124">次の例では、`Where`を特定の長さを持つこれらの文字列の配列からフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="302b1-124">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a><span data-ttu-id="302b1-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="302b1-125">See Also</span></span>  
 <span data-ttu-id="302b1-126"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="302b1-126"><xref:System.Linq></span></span>   
<span data-ttu-id="302b1-127"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="302b1-127"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="302b1-128"> [ここで句](../../../../visual-basic/language-reference/queries/where-clause.md) </span><span class="sxs-lookup"><span data-stu-id="302b1-128"> [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md) </span></span>  
<span data-ttu-id="302b1-129"> [方法: クエリ結果をフィルター処理](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="302b1-129"> [How to: Filter Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="302b1-130"> [方法: リフレクション (LINQ) (Visual Basic) を使用してアセンブリのメタデータを照会します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span><span class="sxs-lookup"><span data-stu-id="302b1-130"> [How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md) </span></span>  
<span data-ttu-id="302b1-131"> [方法: 指定された属性または名前 (Visual Basic) のファイルをクエリ](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span><span class="sxs-lookup"><span data-stu-id="302b1-131"> [How to: Query for Files with a Specified Attribute or Name (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md) </span></span>  
<span data-ttu-id="302b1-132"> [方法: 並べ替えまたはフィルター テキスト データでは、任意の単語またはフィールド (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="302b1-132"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
