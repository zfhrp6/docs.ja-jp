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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bce99f11ba5a18e80c24fc51e65b66de97f9e7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="8d4d7-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="8d4d7-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="8d4d7-103">処理されない実行例外が発生したため、指定された操作の指定されたトランザクションが完了しました。</span><span class="sxs-lookup"><span data-stu-id="8d4d7-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8d4d7-104">説明</span><span class="sxs-lookup"><span data-stu-id="8d4d7-104">Description</span></span>  
 <span data-ttu-id="8d4d7-105">現在のトランザクションを完了しようとしているときにエラーが発生した場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="8d4d7-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="8d4d7-106">これは、応答またはエラーが呼び出し元に送信される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="8d4d7-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8d4d7-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8d4d7-107">Troubleshooting</span></span>  
 <span data-ttu-id="8d4d7-108">トレース メッセージを調べて、例外メッセージとアクション可能な項目を確認してください。</span><span class="sxs-lookup"><span data-stu-id="8d4d7-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4d7-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d4d7-109">See Also</span></span>  
 [<span data-ttu-id="8d4d7-110">トレース</span><span class="sxs-lookup"><span data-stu-id="8d4d7-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8d4d7-111">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8d4d7-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8d4d7-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="8d4d7-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
