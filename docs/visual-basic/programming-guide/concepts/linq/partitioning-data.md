---
title: "(Visual Basic) のデータをパーティション分割 |Microsoft ドキュメント"
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
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
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
ms.openlocfilehash: 9d0df2bc473f48fba4bbb094317166407f7c7ec2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="64e4a-102">データのパーティション分割 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64e4a-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="64e4a-103">LINQ でのパーティション分割は、要素を再配置して、セクションでは、のいずれかを返すことがなく、入力シーケンスを&2; つのセクションに分割の操作です。</span><span class="sxs-lookup"><span data-stu-id="64e4a-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="64e4a-104">次の図は、文字のシーケンスに対して次の&3; つの異なる方法でパーティション分割に操作の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="64e4a-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="64e4a-105">最初の操作は、シーケンス内の最初の&3; つの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="64e4a-106">2 番目の操作では、最初の&3; つの要素をスキップし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="64e4a-107">3 番目の操作では、シーケンス内の最初の&2; つの要素をスキップし、次の&3; つの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="64e4a-108">![LINQ の操作をパーティション分割](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="64e4a-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="64e4a-109">次のセクションでは、シーケンスのパーティション分割する標準クエリ演算子のメソッドが一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="64e4a-110">演算子</span><span class="sxs-lookup"><span data-stu-id="64e4a-110">Operators</span></span>  
  
|<span data-ttu-id="64e4a-111">演算子名</span><span class="sxs-lookup"><span data-stu-id="64e4a-111">Operator Name</span></span>|<span data-ttu-id="64e4a-112">説明</span><span class="sxs-lookup"><span data-stu-id="64e4a-112">Description</span></span>|<span data-ttu-id="64e4a-113">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="64e4a-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="64e4a-114">説明</span><span class="sxs-lookup"><span data-stu-id="64e4a-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="64e4a-115">Skip</span><span class="sxs-lookup"><span data-stu-id="64e4a-115">Skip</span></span>|<span data-ttu-id="64e4a-116">シーケンス内の指定した位置までの要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="64e4a-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<span data-ttu-id="64e4a-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-117"><xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="64e4a-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-118"><xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="64e4a-119">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="64e4a-119">SkipWhile</span></span>|<span data-ttu-id="64e4a-120">要素が条件を満たさないまでは、述語関数に基づいて要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="64e4a-120">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<span data-ttu-id="64e4a-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-121"><xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="64e4a-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-122"><xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="64e4a-123">Take</span><span class="sxs-lookup"><span data-stu-id="64e4a-123">Take</span></span>|<span data-ttu-id="64e4a-124">シーケンス内の指定した位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-124">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<span data-ttu-id="64e4a-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-125"><xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="64e4a-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-126"><xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="64e4a-127">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="64e4a-127">TakeWhile</span></span>|<span data-ttu-id="64e4a-128">要素が条件を満たさないまでは、述語関数に基づいて要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-128">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<span data-ttu-id="64e4a-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-129"><xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="64e4a-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="64e4a-130"><xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="64e4a-131">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="64e4a-131">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="64e4a-132">Skip</span><span class="sxs-lookup"><span data-stu-id="64e4a-132">Skip</span></span>  
 <span data-ttu-id="64e4a-133">次のコード例では、`Skip`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を配列内の残りの文字列を返す前に、文字列の配列内の最初の&4; つの文字列をスキップします。</span><span class="sxs-lookup"><span data-stu-id="64e4a-133">The following code example uses the `Skip` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 <span data-ttu-id="64e4a-134">[!code-vb[CsLINQPartitioning&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e4a-134">[!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]</span></span>  
  
### <a name="skipwhile"></a><span data-ttu-id="64e4a-135">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="64e4a-135">SkipWhile</span></span>  
 <span data-ttu-id="64e4a-136">次のコード例では、`Skip While`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列の最初の文字の中に、配列内の文字列をスキップするは、"a"です。</span><span class="sxs-lookup"><span data-stu-id="64e4a-136">The following code example uses the `Skip While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="64e4a-137">配列内の残りの文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="64e4a-137">The remaining strings in the array are returned.</span></span>  
  
 <span data-ttu-id="64e4a-138">[!code-vb[CsLINQPartitioning&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e4a-138">[!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]</span></span>  
  
### <a name="take"></a><span data-ttu-id="64e4a-139">Take</span><span class="sxs-lookup"><span data-stu-id="64e4a-139">Take</span></span>  
 <span data-ttu-id="64e4a-140">次のコード例では、`Take`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列の配列の最初の&2; つの文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-140">The following code example uses the `Take` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return the first two strings in an array of strings.</span></span>  
  
 <span data-ttu-id="64e4a-141">[!code-vb[CsLINQPartitioning&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e4a-141">[!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]</span></span>  
  
### <a name="takewhile"></a><span data-ttu-id="64e4a-142">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="64e4a-142">TakeWhile</span></span>  
 <span data-ttu-id="64e4a-143">次のコード例では、`Take While`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列の長さが&5; 個以下に、配列から文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="64e4a-143">The following code example uses the `Take While` clause in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to return strings from an array while the length of the string is five or less.</span></span>  
  
 <span data-ttu-id="64e4a-144">[!code-vb[CsLINQPartitioning&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="64e4a-144">[!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e4a-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="64e4a-145">See Also</span></span>  
 <span data-ttu-id="64e4a-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="64e4a-146"><xref:System.Linq></span></span>   
<span data-ttu-id="64e4a-147"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="64e4a-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="64e4a-148"> [Skip 句](../../../../visual-basic/language-reference/queries/skip-clause.md) </span><span class="sxs-lookup"><span data-stu-id="64e4a-148"> [Skip Clause](../../../../visual-basic/language-reference/queries/skip-clause.md) </span></span>  
<span data-ttu-id="64e4a-149"> [Skip While 句](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span><span class="sxs-lookup"><span data-stu-id="64e4a-149"> [Skip While Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) </span></span>  
<span data-ttu-id="64e4a-150"> [Take 句](../../../../visual-basic/language-reference/queries/take-clause.md) </span><span class="sxs-lookup"><span data-stu-id="64e4a-150"> [Take Clause](../../../../visual-basic/language-reference/queries/take-clause.md) </span></span>  
<span data-ttu-id="64e4a-151"> [Take While 句](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span><span class="sxs-lookup"><span data-stu-id="64e4a-151"> [Take While Clause](../../../../visual-basic/language-reference/queries/take-while-clause.md)</span></span>
