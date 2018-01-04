---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf6c70bdcfc402322dd1f20bbff2be74c111798a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="2eeba-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="2eeba-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="2eeba-103">非同期中止が実行されたため、指定された操作の指定のトランザクションは完了されました。</span><span class="sxs-lookup"><span data-stu-id="2eeba-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2eeba-104">説明</span><span class="sxs-lookup"><span data-stu-id="2eeba-104">Description</span></span>  
 <span data-ttu-id="2eeba-105">別の参加要素による中止、タイムアウト、またはトランザクションの参加要素内での別のエラーが発生したため、現在のトランザクションが中止されました。</span><span class="sxs-lookup"><span data-stu-id="2eeba-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2eeba-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2eeba-106">Troubleshooting</span></span>  
 <span data-ttu-id="2eeba-107">予期された中止ではない場合は、すべてのシステム ログを調べて中止の原因を確認してください。</span><span class="sxs-lookup"><span data-stu-id="2eeba-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eeba-108">参照</span><span class="sxs-lookup"><span data-stu-id="2eeba-108">See Also</span></span>  
 [<span data-ttu-id="2eeba-109">トレース</span><span class="sxs-lookup"><span data-stu-id="2eeba-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2eeba-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2eeba-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2eeba-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="2eeba-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
