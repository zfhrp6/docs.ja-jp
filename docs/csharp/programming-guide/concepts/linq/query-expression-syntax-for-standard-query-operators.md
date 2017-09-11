---
title: "標準クエリ演算子のクエリ式構文 (C#)"
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
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
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
ms.openlocfilehash: 30e994329234b8bd455f739694e50121bac63d5d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a><span data-ttu-id="36bf5-102">標準クエリ演算子のクエリ式構文 (C#)</span><span class="sxs-lookup"><span data-stu-id="36bf5-102">Query Expression Syntax for Standard Query Operators (C#)</span></span>
<span data-ttu-id="36bf5-103">頻繁に使用される標準クエリ演算子の中には、C# 言語専用のキーワード構文が使用されているものがあります。こうした構文では、標準クエリ演算子を、"*クエリ式*" の一部として呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="36bf5-103">Some of the more frequently used standard query operators have dedicated C# language keyword syntax that enables them to be called as part of a *query expression*.</span></span> <span data-ttu-id="36bf5-104">クエリ式は*メソッド ベース*の方法とは異なり、より読み取りやすいクエリの表現形式です。</span><span class="sxs-lookup"><span data-stu-id="36bf5-104">A query expression is a different, more readable form of expressing a query than its *method-based*  equivalent.</span></span> <span data-ttu-id="36bf5-105">クエリ式の句は、コンパイル時にクエリ メソッドへの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="36bf5-105">Query expression clauses are translated into calls to the query methods at compile time.</span></span>  
  
## <a name="query-expression-syntax-table"></a><span data-ttu-id="36bf5-106">クエリ式の構文表</span><span class="sxs-lookup"><span data-stu-id="36bf5-106">Query Expression Syntax Table</span></span>  
 <span data-ttu-id="36bf5-107">次の表は、同等なクエリ式の句がある標準クエリ演算子の一覧です。</span><span class="sxs-lookup"><span data-stu-id="36bf5-107">The following table lists the standard query operators that have equivalent query expression clauses.</span></span>  
  
|<span data-ttu-id="36bf5-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="36bf5-108">Method</span></span>|<span data-ttu-id="36bf5-109">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="36bf5-109">C# Query Expression Syntax</span></span>|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|<span data-ttu-id="36bf5-110">明示的に型指定された範囲変数を使用します。例:</span><span class="sxs-lookup"><span data-stu-id="36bf5-110">Use an explicitly typed range variable, for example:</span></span><br /><br /> `from int i in numbers`<br /><br /> <span data-ttu-id="36bf5-111">(詳しくは、「[from 句](../../../../csharp/language-reference/keywords/from-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-111">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> <span data-ttu-id="36bf5-112">または</span><span class="sxs-lookup"><span data-stu-id="36bf5-112">-or-</span></span><br /><br /> `group … by … into …`<br /><br /> <span data-ttu-id="36bf5-113">(詳しくは、「[group 句](../../../../csharp/language-reference/keywords/group-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-113">(For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> <span data-ttu-id="36bf5-114">(詳しくは、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-114">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> <span data-ttu-id="36bf5-115">(詳しくは、「[join 句](../../../../csharp/language-reference/keywords/join-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-115">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> <span data-ttu-id="36bf5-116">(詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-116">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> <span data-ttu-id="36bf5-117">(詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-117">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> <span data-ttu-id="36bf5-118">(詳しくは、「[select 句](../../../../csharp/language-reference/keywords/select-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-118">(For more information, see [select clause](../../../../csharp/language-reference/keywords/select-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<span data-ttu-id="36bf5-119">複数の `from` 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="36bf5-119">Multiple `from` clauses.</span></span><br /><br /> <span data-ttu-id="36bf5-120">(詳しくは、「[from 句](../../../../csharp/language-reference/keywords/from-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-120">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> <span data-ttu-id="36bf5-121">(詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-121">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> <span data-ttu-id="36bf5-122">(詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-122">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> <span data-ttu-id="36bf5-123">(詳しくは、「[where 句](../../../../csharp/language-reference/keywords/where-clause.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="36bf5-123">(For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36bf5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="36bf5-124">See Also</span></span>  
 <span data-ttu-id="36bf5-125"><xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="36bf5-125"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="36bf5-126"><xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="36bf5-126"><xref:System.Linq.Queryable></span></span>   
 <span data-ttu-id="36bf5-127">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="36bf5-127">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="36bf5-128">実行方法による標準クエリ演算子の分類 (C#)</span><span class="sxs-lookup"><span data-stu-id="36bf5-128">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)

