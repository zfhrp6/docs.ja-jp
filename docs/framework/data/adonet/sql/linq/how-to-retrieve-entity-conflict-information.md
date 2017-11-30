---
title: "方法 : エンティティの競合情報を取得する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26f3ec3736b04eeffc1cd741e2c06a39ef7f1a0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="cb2ce-102">方法 : エンティティの競合情報を取得する</span><span class="sxs-lookup"><span data-stu-id="cb2ce-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="cb2ce-103"><xref:System.Data.Linq.ObjectChangeConflict> クラスのオブジェクトを使用して、<xref:System.Data.Linq.ChangeConflictException> 例外によって発生する競合に関する情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="cb2ce-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="cb2ce-104">詳細については、次を参照してください。[オプティミスティック同時実行制御: 概要](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb2ce-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb2ce-105">例</span><span class="sxs-lookup"><span data-stu-id="cb2ce-105">Example</span></span>  
 <span data-ttu-id="cb2ce-106">次の例では、累積した競合のリストを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="cb2ce-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cb2ce-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb2ce-107">See Also</span></span>  
 [<span data-ttu-id="cb2ce-108">方法: 変更の競合の管理</span><span class="sxs-lookup"><span data-stu-id="cb2ce-108">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
