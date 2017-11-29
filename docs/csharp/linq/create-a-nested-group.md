---
title: "入れ子になったグループの作成"
description: "入れ子になったグループを作成する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a><span data-ttu-id="5014d-104">入れ子になったグループの作成</span><span class="sxs-lookup"><span data-stu-id="5014d-104">Create a nested group</span></span>

<span data-ttu-id="5014d-105">LINQ クエリ式で入れ子になったグループを作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5014d-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="5014d-106">学年レベルに基づいて作成した各グループを、さらに個人の名前に基づくグループに分割します。</span><span class="sxs-lookup"><span data-stu-id="5014d-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5014d-107">例</span><span class="sxs-lookup"><span data-stu-id="5014d-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="5014d-108">この例には、「[オブジェクトのコレクションの照会](query-a-collection-of-objects.md)」のサンプル コードで定義されているオブジェクトへの参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5014d-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="5014d-109">入れ子になったグループの内部要素に対して反復処理を実行するために、入れ子になった `foreach` ループが 3 つ必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5014d-109">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5014d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5014d-110">See also</span></span>  
 [<span data-ttu-id="5014d-111">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="5014d-111">LINQ Query Expressions</span></span>](index.md)
