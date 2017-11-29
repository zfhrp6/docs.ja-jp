---
title: "方法 : 送信の競合を検出および解決する"
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
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8eb2e27ab034d464ba6978d9ddc063e623812619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="18dba-102">方法 : 送信の競合を検出および解決する</span><span class="sxs-lookup"><span data-stu-id="18dba-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="18dba-103"> には、複数のユーザーがデータベースを変更するために生じる競合を、検出および解決するための多くのリソースが用意されています。</span><span class="sxs-lookup"><span data-stu-id="18dba-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="18dba-104">詳細については、次を参照してください。[する方法: 変更の競合を管理](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)です。</span><span class="sxs-lookup"><span data-stu-id="18dba-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18dba-105">例</span><span class="sxs-lookup"><span data-stu-id="18dba-105">Example</span></span>  
 <span data-ttu-id="18dba-106">次の例は、 `try` / `catch`キャッチ ブロック、<xref:System.Data.Linq.ChangeConflictException>例外。</span><span class="sxs-lookup"><span data-stu-id="18dba-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="18dba-107">各競合のエンティティおよびメンバー情報が、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="18dba-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18dba-108">情報の取得をサポートするには、`using System.Reflection` ディレクティブ (Visual Basic の場合は `Imports System.Reflection`) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="18dba-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="18dba-109">詳細については、「<xref:System.Reflection>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18dba-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="18dba-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="18dba-110">See Also</span></span>  
 [<span data-ttu-id="18dba-111">作成方法とデータの変更の送信</span><span class="sxs-lookup"><span data-stu-id="18dba-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="18dba-112">方法: 変更の競合の管理</span><span class="sxs-lookup"><span data-stu-id="18dba-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
