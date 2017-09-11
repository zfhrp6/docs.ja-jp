---
title: "クエリ キーワード (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6dadce6d48e711032cca03a7f7c2ba02360e685f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="e1a65-102">クエリ キーワード (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e1a65-102">Query Keywords (C# Reference)</span></span>
<span data-ttu-id="e1a65-103">このセクションでは、クエリ式で使用するコンテキスト キーワードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-103">This section contains the contextual keywords used in query expressions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1a65-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e1a65-104">In This Section</span></span>  
  
|<span data-ttu-id="e1a65-105">句</span><span class="sxs-lookup"><span data-stu-id="e1a65-105">Clause</span></span>|<span data-ttu-id="e1a65-106">説明</span><span class="sxs-lookup"><span data-stu-id="e1a65-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1a65-107">from</span><span class="sxs-lookup"><span data-stu-id="e1a65-107">from</span></span>](../../../csharp/language-reference/keywords/from-clause.md)|<span data-ttu-id="e1a65-108">データ ソースおよび範囲変数 (反復変数に類似) を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|  
|[<span data-ttu-id="e1a65-109">where</span><span class="sxs-lookup"><span data-stu-id="e1a65-109">where</span></span>](../../../csharp/language-reference/keywords/where-clause.md)|<span data-ttu-id="e1a65-110">論理 AND 演算子 (`&&`) と論理 OR 演算子 (<code>&#124;&#124;</code>) で区切られた 1 つ以上のブール式に基づき、ソース要素をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|  
|[<span data-ttu-id="e1a65-111">select</span><span class="sxs-lookup"><span data-stu-id="e1a65-111">select</span></span>](../../../csharp/language-reference/keywords/select-clause.md)|<span data-ttu-id="e1a65-112">クエリ実行で返されるシーケンスに含まれる要素の型と形状を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|  
|[<span data-ttu-id="e1a65-113">group</span><span class="sxs-lookup"><span data-stu-id="e1a65-113">group</span></span>](../../../csharp/language-reference/keywords/group-clause.md)|<span data-ttu-id="e1a65-114">指定したキー値に基づき、クエリ結果をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-114">Groups query results according to a specified key value.</span></span>|  
|[<span data-ttu-id="e1a65-115">into</span><span class="sxs-lookup"><span data-stu-id="e1a65-115">into</span></span>](../../../csharp/language-reference/keywords/into.md)|<span data-ttu-id="e1a65-116">join 句、group 句、または select 句の結果への参照として機能する識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|  
|[<span data-ttu-id="e1a65-117">orderby</span><span class="sxs-lookup"><span data-stu-id="e1a65-117">orderby</span></span>](../../../csharp/language-reference/keywords/orderby-clause.md)|<span data-ttu-id="e1a65-118">要素型の既定の比較子に基づき、クエリ結果を昇順または降順で並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="e1a65-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|  
|[<span data-ttu-id="e1a65-119">join</span><span class="sxs-lookup"><span data-stu-id="e1a65-119">join</span></span>](../../../csharp/language-reference/keywords/join-clause.md)|<span data-ttu-id="e1a65-120">指定した 2 つの一致基準の等価比較に基づき、2 つのデータ ソースを結合します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|  
|[<span data-ttu-id="e1a65-121">let</span><span class="sxs-lookup"><span data-stu-id="e1a65-121">let</span></span>](../../../csharp/language-reference/keywords/let-clause.md)|<span data-ttu-id="e1a65-122">範囲変数を使用して、クエリ式のサブ式の結果を格納します。</span><span class="sxs-lookup"><span data-stu-id="e1a65-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|  
|[<span data-ttu-id="e1a65-123">in</span><span class="sxs-lookup"><span data-stu-id="e1a65-123">in</span></span>](../../../csharp/language-reference/keywords/in.md)|<span data-ttu-id="e1a65-124">[join](../../../csharp/language-reference/keywords/join-clause.md) 句のコンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="e1a65-124">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e1a65-125">on</span><span class="sxs-lookup"><span data-stu-id="e1a65-125">on</span></span>](../../../csharp/language-reference/keywords/on.md)|<span data-ttu-id="e1a65-126">[join](../../../csharp/language-reference/keywords/join-clause.md) 句のコンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="e1a65-126">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e1a65-127">equals</span><span class="sxs-lookup"><span data-stu-id="e1a65-127">equals</span></span>](../../../csharp/language-reference/keywords/equals.md)|<span data-ttu-id="e1a65-128">[join](../../../csharp/language-reference/keywords/join-clause.md) 句のコンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="e1a65-128">Contextual keyword in a [join](../../../csharp/language-reference/keywords/join-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e1a65-129">by</span><span class="sxs-lookup"><span data-stu-id="e1a65-129">by</span></span>](../../../csharp/language-reference/keywords/by.md)|<span data-ttu-id="e1a65-130">[group](../../../csharp/language-reference/keywords/group-clause.md) 句のコンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="e1a65-130">Contextual keyword in a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e1a65-131">ascending</span><span class="sxs-lookup"><span data-stu-id="e1a65-131">ascending</span></span>](../../../csharp/language-reference/keywords/ascending.md)|<span data-ttu-id="e1a65-132">[orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 句のコンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="e1a65-132">Contextual keyword in an [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clause.</span></span>|  
|[<span data-ttu-id="e1a65-133">descending</span><span class="sxs-lookup"><span data-stu-id="e1a65-133">descending</span></span>](../../../csharp/language-reference/keywords/descending.md)|<span data-ttu-id="e1a65-134">[orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 句のコンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="e1a65-134">Contextual keyword in an [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clause.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1a65-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1a65-135">See Also</span></span>  
 <span data-ttu-id="e1a65-136">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="e1a65-136">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="e1a65-137">[LINQ (統合言語クエリ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="e1a65-137">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="e1a65-138">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="e1a65-138">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="e1a65-139">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="e1a65-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

