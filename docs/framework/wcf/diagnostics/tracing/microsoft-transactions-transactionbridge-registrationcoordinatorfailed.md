---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: dec86141a19c3e5edf5d13ed1ef8d2e8f2b38fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475655"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="33479-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="33479-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="33479-103">WS-AT プロトコル サービスは、Register メッセージをコーディネーターに送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="33479-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="33479-104">説明</span><span class="sxs-lookup"><span data-stu-id="33479-104">Description</span></span>  
 <span data-ttu-id="33479-105">メッセージを送信できないために、ローカルの TransactionManager がその上位の TransactionManager に登録できない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="33479-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="33479-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="33479-106">Troubleshooting</span></span>  
 <span data-ttu-id="33479-107">トレース メッセージを調べて、メッセージの送信エラーの原因となった例外を確認してください。</span><span class="sxs-lookup"><span data-stu-id="33479-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33479-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="33479-108">See Also</span></span>  
 [<span data-ttu-id="33479-109">トレース</span><span class="sxs-lookup"><span data-stu-id="33479-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="33479-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="33479-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="33479-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="33479-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
