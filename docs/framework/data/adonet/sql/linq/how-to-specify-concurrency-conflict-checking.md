---
title: "方法 : 同時実行の競合のチェックを指定する"
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
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6e69b97de78c469bd252319c49d362fe96af6833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="db960-102">方法 : 同時実行の競合のチェックを指定する</span><span class="sxs-lookup"><span data-stu-id="db960-102">How to: Specify Concurrency-Conflict Checking</span></span>
<span data-ttu-id="db960-103"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> を呼び出すときに同時実行の競合をチェックするデータベース列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="db960-103">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="db960-104">詳細については、次を参照してください。[する方法: 同時実行の競合があるテストを指定するメンバー](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)です。</span><span class="sxs-lookup"><span data-stu-id="db960-104">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db960-105">例</span><span class="sxs-lookup"><span data-stu-id="db960-105">Example</span></span>  
 <span data-ttu-id="db960-106">次のコード例では、更新の確認時に `HomePage` メンバーを検査しないことを指定しています。</span><span class="sxs-lookup"><span data-stu-id="db960-106">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="db960-107">詳細については、「<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db960-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="db960-108">参照</span><span class="sxs-lookup"><span data-stu-id="db960-108">See Also</span></span>  
 [<span data-ttu-id="db960-109">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="db960-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="db960-110">方法 : コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="db960-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
