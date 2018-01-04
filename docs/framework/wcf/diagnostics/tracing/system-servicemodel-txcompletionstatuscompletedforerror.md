---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25106bffe6d541a89c786035db3d3266d861fd5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="b6ad6-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="b6ad6-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="b6ad6-103">処理されない実行例外が発生したため、指定された操作の指定されたトランザクションが完了しました。</span><span class="sxs-lookup"><span data-stu-id="b6ad6-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b6ad6-104">説明</span><span class="sxs-lookup"><span data-stu-id="b6ad6-104">Description</span></span>  
 <span data-ttu-id="b6ad6-105">現在のトランザクションを完了しようとしているときにエラーが発生した場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="b6ad6-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="b6ad6-106">これは、応答またはエラーが呼び出し元に送信される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="b6ad6-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b6ad6-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b6ad6-107">Troubleshooting</span></span>  
 <span data-ttu-id="b6ad6-108">トレース メッセージを調べて、例外メッセージとアクション可能な項目を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b6ad6-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ad6-109">参照</span><span class="sxs-lookup"><span data-stu-id="b6ad6-109">See Also</span></span>  
 [<span data-ttu-id="b6ad6-110">トレース</span><span class="sxs-lookup"><span data-stu-id="b6ad6-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b6ad6-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b6ad6-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b6ad6-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="b6ad6-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
