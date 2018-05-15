---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 85b8cc4e5044cc7c87ea784e09c160cc527dddaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="fd074-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="fd074-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="fd074-103">参加要素の登録リストのステート マシンは完了状態になりました。</span><span class="sxs-lookup"><span data-stu-id="fd074-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd074-104">説明</span><span class="sxs-lookup"><span data-stu-id="fd074-104">Description</span></span>  
 <span data-ttu-id="fd074-105">下位参加要素登録リストの 2PC 処理が完了したときにトレースされます。</span><span class="sxs-lookup"><span data-stu-id="fd074-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="fd074-106">登録リストの結果は、Committed または Aborted のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="fd074-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="fd074-107">準備中、すべての参加要素を読み取り専用にする場合にもトレースされます。</span><span class="sxs-lookup"><span data-stu-id="fd074-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd074-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd074-108">See Also</span></span>  
 [<span data-ttu-id="fd074-109">トレース</span><span class="sxs-lookup"><span data-stu-id="fd074-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fd074-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fd074-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="fd074-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="fd074-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
