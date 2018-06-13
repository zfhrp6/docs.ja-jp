---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 9dd2ba5a3e94ff794d4b8a8775944355b105f790
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33482009"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="e750e-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="e750e-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="e750e-103">WS-AT プロトコル サービスは、指定されたコーディネーション コンテキストを使用してトランザクションに参加することができませんでした。</span><span class="sxs-lookup"><span data-stu-id="e750e-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e750e-104">説明</span><span class="sxs-lookup"><span data-stu-id="e750e-104">Description</span></span>  
 <span data-ttu-id="e750e-105">指定された 2PC プロトコルのトランザクションに MSDTC が参加できない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="e750e-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="e750e-106">これは、トランザクションが存在しなくなった場合、参加が許可されなくなった場合、または既に参加が多すぎる場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e750e-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e750e-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e750e-107">Troubleshooting</span></span>  
 <span data-ttu-id="e750e-108">トレース メッセージ内のステータス文字列を調べて、アクション可能な項目が存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e750e-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e750e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e750e-109">See Also</span></span>  
 [<span data-ttu-id="e750e-110">トレース</span><span class="sxs-lookup"><span data-stu-id="e750e-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e750e-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e750e-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e750e-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="e750e-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
