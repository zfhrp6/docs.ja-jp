---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c9a456e668560cb2172de80295b731a6103aa7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="423b2-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="423b2-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="423b2-103">コーディネーターの登録リストのステート マシンが完了状態になりました。</span><span class="sxs-lookup"><span data-stu-id="423b2-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="423b2-104">説明</span><span class="sxs-lookup"><span data-stu-id="423b2-104">Description</span></span>  
 <span data-ttu-id="423b2-105">上位のコーディネーターの登録リストが 2PC 処理を完了したとローカル トランザクション マネージャーが判断したときに、トレースされます。</span><span class="sxs-lookup"><span data-stu-id="423b2-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="423b2-106">登録リストの結果は、Committed、Aborted、または Forgotten のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="423b2-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="423b2-107">ローカル トランザクション マネージャーが準備中に読み取り専用にする場合にもトレースされます。</span><span class="sxs-lookup"><span data-stu-id="423b2-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423b2-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="423b2-108">See Also</span></span>  
 [<span data-ttu-id="423b2-109">トレース</span><span class="sxs-lookup"><span data-stu-id="423b2-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="423b2-110">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="423b2-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="423b2-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="423b2-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
