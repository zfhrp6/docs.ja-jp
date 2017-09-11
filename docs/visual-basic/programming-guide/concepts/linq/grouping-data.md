---
title: "データ (Visual Basic) をグループ化 |Microsoft ドキュメント"
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
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
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
ms.openlocfilehash: ce4e8f924f91eed451d3b1a02cd0bcff75589537
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="d8c20-102">データのグループ化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8c20-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="d8c20-103">グループ化は、各グループ内の要素は、共通の属性を共有できるようにこのデータをグループに追加の操作を参照します。</span><span class="sxs-lookup"><span data-stu-id="d8c20-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="d8c20-104">次の図は、文字のシーケンスをグループ化の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="d8c20-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="d8c20-105">各グループのキーは、文字です。</span><span class="sxs-lookup"><span data-stu-id="d8c20-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="d8c20-106">![LINQ グループ化操作](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="d8c20-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="d8c20-107">データ要素をグループ化する標準クエリ演算子メソッドは、次のように記載されています。</span><span class="sxs-lookup"><span data-stu-id="d8c20-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8c20-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="d8c20-108">Methods</span></span>  
  
|<span data-ttu-id="d8c20-109">メソッド名</span><span class="sxs-lookup"><span data-stu-id="d8c20-109">Method Name</span></span>|<span data-ttu-id="d8c20-110">説明</span><span class="sxs-lookup"><span data-stu-id="d8c20-110">Description</span></span>|<span data-ttu-id="d8c20-111">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="d8c20-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="d8c20-112">説明</span><span class="sxs-lookup"><span data-stu-id="d8c20-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="d8c20-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="d8c20-113">GroupBy</span></span>|<span data-ttu-id="d8c20-114">一般的な属性を共有する要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="d8c20-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="d8c20-115">各グループがによって表される、<xref:System.Linq.IGrouping%602>オブジェクト</xref:System.Linq.IGrouping%602>。</span><span class="sxs-lookup"><span data-stu-id="d8c20-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<span data-ttu-id="d8c20-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d8c20-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="d8c20-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d8c20-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="d8c20-118">ToLookup</span><span class="sxs-lookup"><span data-stu-id="d8c20-118">ToLookup</span></span>|<span data-ttu-id="d8c20-119">要素を挿入、<xref:System.Linq.Lookup%602>されたキー セレクター関数に基づいて、(一対多辞書).</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="d8c20-119">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="d8c20-120">該当なし。</span><span class="sxs-lookup"><span data-stu-id="d8c20-120">Not applicable.</span></span>|<span data-ttu-id="d8c20-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d8c20-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="d8c20-122">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="d8c20-122">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="d8c20-123">次のコード例では、`Group By`句は偶数か奇数かどうかを基に、一覧内のグループの整数をします。</span><span class="sxs-lookup"><span data-stu-id="d8c20-123">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8c20-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8c20-124">See Also</span></span>  
 <span data-ttu-id="d8c20-125"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="d8c20-125"><xref:System.Linq></span></span>   
<span data-ttu-id="d8c20-126"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="d8c20-126"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="d8c20-127"> [Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="d8c20-127"> [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span></span>  
<span data-ttu-id="d8c20-128"> [方法: 拡張機能 (LINQ) (Visual Basic) でファイルをグループ化](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span><span class="sxs-lookup"><span data-stu-id="d8c20-128"> [How to: Group Files by Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span></span>  
<span data-ttu-id="d8c20-129"> [方法: 多くのファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="d8c20-129"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
