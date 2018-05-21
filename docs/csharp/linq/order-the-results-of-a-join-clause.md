---
title: join 句の結果の順序指定
description: join 句の結果の順序を指定する方法。
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f426152e614ed9a9c4aa41d7ba7cb8ddf1cd3063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="b10c7-103">join 句の結果の順序指定</span><span class="sxs-lookup"><span data-stu-id="b10c7-103">Order the results of a join clause</span></span>
<span data-ttu-id="b10c7-104">この例では、結合操作の結果の順序を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b10c7-104">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="b10c7-105">順序付けは結合後に実行されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b10c7-105">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="b10c7-106">結合の前に 1 つ以上のソース シーケンスを指定した `orderby` 句を使用することもできますが、一般にこの方法は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="b10c7-106">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="b10c7-107">LINQ プロバイダーによっては、結合後にその順序付けを維持しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b10c7-107">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b10c7-108">例</span><span class="sxs-lookup"><span data-stu-id="b10c7-108">Example</span></span>  
 <span data-ttu-id="b10c7-109">このクエリは、グループ結合を作成した後、スコープ内に残っているカテゴリ要素に基づいてグループを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="b10c7-109">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="b10c7-110">匿名型初期化子の内部では、結果のシーケンス内の一致するすべての要素がサブクエリによって順序付けられます。</span><span class="sxs-lookup"><span data-stu-id="b10c7-110">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="b10c7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b10c7-111">See also</span></span>  
 [<span data-ttu-id="b10c7-112">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="b10c7-112">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="b10c7-113">orderby 句</span><span class="sxs-lookup"><span data-stu-id="b10c7-113">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="b10c7-114">join 句</span><span class="sxs-lookup"><span data-stu-id="b10c7-114">join clause</span></span>](../language-reference/keywords/join-clause.md) 
