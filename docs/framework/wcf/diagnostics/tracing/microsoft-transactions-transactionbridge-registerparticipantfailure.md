---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e3cbe9443f32ec9752198646e96cc1012d7343c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="dcb3b-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="dcb3b-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="dcb3b-103">WS-AT プロトコル サービスは、制御プロトコルの参加要素の登録に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="dcb3b-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dcb3b-104">説明</span><span class="sxs-lookup"><span data-stu-id="dcb3b-104">Description</span></span>  
 <span data-ttu-id="dcb3b-105">MSDTC により無効な登録要求が検出された場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="dcb3b-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="dcb3b-106">これは、複数の完了登録要求や内部エラーによって発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="dcb3b-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="dcb3b-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="dcb3b-107">Troubleshooting</span></span>  
 <span data-ttu-id="dcb3b-108">完了を複数回登録しないでください。</span><span class="sxs-lookup"><span data-stu-id="dcb3b-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="dcb3b-109">また、トレース メッセージ内のステータス文字列を調べて、アクション可能な項目が存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dcb3b-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb3b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcb3b-110">See Also</span></span>  
 [<span data-ttu-id="dcb3b-111">トレース</span><span class="sxs-lookup"><span data-stu-id="dcb3b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="dcb3b-112">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="dcb3b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="dcb3b-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="dcb3b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
