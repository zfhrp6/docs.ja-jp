---
title: データのフィルター処理 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: d3f44d0b6478103a10fb731988aeebc005cde82e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644343"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="48a2f-102">データのフィルター処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a2f-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="48a2f-103">フィルター処理とは、特定の条件を満たす要素のみが含まれるように結果セットを限定する操作のことです。</span><span class="sxs-lookup"><span data-stu-id="48a2f-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="48a2f-104">選択とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="48a2f-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="48a2f-105">次の図は、文字のシーケンスをフィルター処理した結果を示したものです。</span><span class="sxs-lookup"><span data-stu-id="48a2f-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="48a2f-106">フィルター処理操作の述語では、文字が "A" でなければならないことが指定されています。</span><span class="sxs-lookup"><span data-stu-id="48a2f-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="48a2f-107">![LINQ フィルター処理操作](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="48a2f-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="48a2f-108">次のセクションでは、選択を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="48a2f-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48a2f-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="48a2f-109">Methods</span></span>  
  
|<span data-ttu-id="48a2f-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="48a2f-110">Method Name</span></span>|<span data-ttu-id="48a2f-111">説明</span><span class="sxs-lookup"><span data-stu-id="48a2f-111">Description</span></span>|<span data-ttu-id="48a2f-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="48a2f-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="48a2f-113">説明</span><span class="sxs-lookup"><span data-stu-id="48a2f-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="48a2f-114">OfType</span><span class="sxs-lookup"><span data-stu-id="48a2f-114">OfType</span></span>|<span data-ttu-id="48a2f-115">指定した型にキャストできるかどうかにより、値を選択します。</span><span class="sxs-lookup"><span data-stu-id="48a2f-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="48a2f-116">該当なし。</span><span class="sxs-lookup"><span data-stu-id="48a2f-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="48a2f-117">Where</span><span class="sxs-lookup"><span data-stu-id="48a2f-117">Where</span></span>|<span data-ttu-id="48a2f-118">述語関数に基づいて値を選択します。</span><span class="sxs-lookup"><span data-stu-id="48a2f-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="48a2f-119">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="48a2f-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="48a2f-120">次の例では、`Where`を特定の長さを持つそれらの文字列の配列からフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="48a2f-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48a2f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="48a2f-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="48a2f-122">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a2f-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="48a2f-123">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="48a2f-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="48a2f-124">方法 : クエリ結果のフィルター処理</span><span class="sxs-lookup"><span data-stu-id="48a2f-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="48a2f-125">方法: リフレクション (LINQ) (Visual Basic) を使用してアセンブリのメタデータを照会します。</span><span class="sxs-lookup"><span data-stu-id="48a2f-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="48a2f-126">方法: クエリのファイルで指定された属性または名前 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a2f-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="48a2f-127">方法: 並べ替えまたはフィルター テキスト データで任意の単語またはフィールド (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a2f-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
