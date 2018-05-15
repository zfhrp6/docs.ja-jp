---
title: WF 内のエラー処理アクティビティ
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 51431e367f0ec8874588a52cb4dbd76d714768fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="93503-102">WF 内のエラー処理アクティビティ</span><span class="sxs-lookup"><span data-stu-id="93503-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="93503-103"> には、エラーの処理および回復を実装するためのシステム標準のアクティビティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="93503-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="93503-104">詳細については、次を参照してください。[例外](../../../docs/framework/windows-workflow-foundation/exceptions.md)です。</span><span class="sxs-lookup"><span data-stu-id="93503-104">For more information, see [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="93503-105">エラー処理アクティビティ</span><span class="sxs-lookup"><span data-stu-id="93503-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="93503-106">`TryCatch` アクティビティ内からスローされた最後の例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="93503-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="93503-107">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="93503-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="93503-108">例外処理を実装します。</span><span class="sxs-lookup"><span data-stu-id="93503-108">Implements exception handling.</span></span>|
