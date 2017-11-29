---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b497231326c640b93b96500df39732104e0f0c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="f24e6-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="f24e6-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="f24e6-103">WS-AT プロトコル サービスは、認識されない不安定な参加要素からの準備メッセージまたはリプレイ メッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="f24e6-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="f24e6-104">参加要素にエラーが返されました。この結果、トランザクションの結果が不明であると宣言します。</span><span class="sxs-lookup"><span data-stu-id="f24e6-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f24e6-105">説明</span><span class="sxs-lookup"><span data-stu-id="f24e6-105">Description</span></span>  
 <span data-ttu-id="f24e6-106">ローカル トランザクション マネージャーが、既に認識していない揮発性参加リストからの準備メッセージまたはリプレイ メッセージを受信するとトレースされます。</span><span class="sxs-lookup"><span data-stu-id="f24e6-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f24e6-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f24e6-107">Troubleshooting</span></span>  
 <span data-ttu-id="f24e6-108">不安定な参加要素からメッセージが遅れて届く原因を調査してください。</span><span class="sxs-lookup"><span data-stu-id="f24e6-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24e6-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="f24e6-109">See Also</span></span>  
 [<span data-ttu-id="f24e6-110">トレース</span><span class="sxs-lookup"><span data-stu-id="f24e6-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f24e6-111">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f24e6-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f24e6-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="f24e6-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
