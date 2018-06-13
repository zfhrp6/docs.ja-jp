---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: e1cb43a9336c2536a3b0372387fd956708be78a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475921"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="cee6d-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="cee6d-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="cee6d-103">WS-AT プロトコル サービスは、Register メッセージへの応答として、コーディネーターからエラーを受信しました。</span><span class="sxs-lookup"><span data-stu-id="cee6d-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cee6d-104">説明</span><span class="sxs-lookup"><span data-stu-id="cee6d-104">Description</span></span>  
 <span data-ttu-id="cee6d-105">エラーが返されたためにローカルの TransactionManager がその上位の TransactionManager に登録できない場合に、トレースされます。</span><span class="sxs-lookup"><span data-stu-id="cee6d-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="cee6d-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="cee6d-106">Troubleshooting</span></span>  
 <span data-ttu-id="cee6d-107">トレース メッセージを調べて、返されたエラーを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cee6d-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee6d-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="cee6d-108">See Also</span></span>  
 [<span data-ttu-id="cee6d-109">トレース</span><span class="sxs-lookup"><span data-stu-id="cee6d-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cee6d-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="cee6d-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cee6d-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="cee6d-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
