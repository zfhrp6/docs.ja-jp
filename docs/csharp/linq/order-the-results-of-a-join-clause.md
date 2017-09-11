---
title: "join 句の結果の順序指定"
description: "join 句の結果の順序を指定する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6272181647bb200c18231c5fc836e3dd1a2d6d55
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="328a4-104">join 句の結果の順序指定</span><span class="sxs-lookup"><span data-stu-id="328a4-104">Order the results of a join clause</span></span>
<span data-ttu-id="328a4-105">この例では、結合操作の結果の順序を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="328a4-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="328a4-106">順序付けは結合後に実行されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="328a4-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="328a4-107">結合の前に 1 つ以上のソース シーケンスを指定した `orderby` 句を使用することもできますが、一般にこの方法は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="328a4-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="328a4-108">LINQ プロバイダーによっては、結合後にその順序付けを維持しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="328a4-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="328a4-109">例</span><span class="sxs-lookup"><span data-stu-id="328a4-109">Example</span></span>  
 <span data-ttu-id="328a4-110">このクエリは、グループ結合を作成した後、スコープ内に残っているカテゴリ要素に基づいてグループを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="328a4-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="328a4-111">匿名型初期化子の内部では、結果のシーケンス内の一致するすべての要素がサブクエリによって順序付けられます。</span><span class="sxs-lookup"><span data-stu-id="328a4-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 <span data-ttu-id="328a4-112">[!code-cs[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="328a4-112">[!code-cs[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="328a4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="328a4-113">See also</span></span>  
 <span data-ttu-id="328a4-114">[LINQ クエリ式](index.md) </span><span class="sxs-lookup"><span data-stu-id="328a4-114">[LINQ query expressions](index.md) </span></span>  
 <span data-ttu-id="328a4-115">[orderby 句](../language-reference/keywords/orderby-clause.md) </span><span class="sxs-lookup"><span data-stu-id="328a4-115">[orderby clause](../language-reference/keywords/orderby-clause.md) </span></span>  
 [<span data-ttu-id="328a4-116">join 句</span><span class="sxs-lookup"><span data-stu-id="328a4-116">join clause</span></span>](../language-reference/keywords/join-clause.md) 

