---
title: "join 句の結果の順序指定"
description: "join 句の結果の順序を指定する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="ca63e-104">join 句の結果の順序指定</span><span class="sxs-lookup"><span data-stu-id="ca63e-104">Order the results of a join clause</span></span>
<span data-ttu-id="ca63e-105">この例では、結合操作の結果の順序を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ca63e-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="ca63e-106">順序付けは結合後に実行されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ca63e-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="ca63e-107">結合の前に 1 つ以上のソース シーケンスを指定した `orderby` 句を使用することもできますが、一般にこの方法は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="ca63e-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="ca63e-108">LINQ プロバイダーによっては、結合後にその順序付けを維持しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca63e-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca63e-109">例</span><span class="sxs-lookup"><span data-stu-id="ca63e-109">Example</span></span>  
 <span data-ttu-id="ca63e-110">このクエリは、グループ結合を作成した後、スコープ内に残っているカテゴリ要素に基づいてグループを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="ca63e-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="ca63e-111">匿名型初期化子の内部では、結果のシーケンス内の一致するすべての要素がサブクエリによって順序付けられます。</span><span class="sxs-lookup"><span data-stu-id="ca63e-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="ca63e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca63e-112">See also</span></span>  
 [<span data-ttu-id="ca63e-113">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="ca63e-113">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="ca63e-114">orderby 句</span><span class="sxs-lookup"><span data-stu-id="ca63e-114">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="ca63e-115">join 句</span><span class="sxs-lookup"><span data-stu-id="ca63e-115">join clause</span></span>](../language-reference/keywords/join-clause.md) 
