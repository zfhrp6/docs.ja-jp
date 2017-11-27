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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3595b98ca8c78fb6bdf86a08dcd56b37a4770405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="66a94-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="66a94-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="66a94-103">非同期中止が実行されたため、指定された操作の指定のトランザクションは完了されました。</span><span class="sxs-lookup"><span data-stu-id="66a94-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="66a94-104">説明</span><span class="sxs-lookup"><span data-stu-id="66a94-104">Description</span></span>  
 <span data-ttu-id="66a94-105">別の参加要素による中止、タイムアウト、またはトランザクションの参加要素内での別のエラーが発生したため、現在のトランザクションが中止されました。</span><span class="sxs-lookup"><span data-stu-id="66a94-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="66a94-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="66a94-106">Troubleshooting</span></span>  
 <span data-ttu-id="66a94-107">予期された中止ではない場合は、すべてのシステム ログを調べて中止の原因を確認してください。</span><span class="sxs-lookup"><span data-stu-id="66a94-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a94-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="66a94-108">See Also</span></span>  
 [<span data-ttu-id="66a94-109">トレース</span><span class="sxs-lookup"><span data-stu-id="66a94-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="66a94-110">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="66a94-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="66a94-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="66a94-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
