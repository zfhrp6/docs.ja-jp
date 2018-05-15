---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 7f376244343a75c16d5d2355642d626f666e42bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="784e5-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="784e5-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="784e5-103">指定されたコーディネーション コンテキストのための OleTransactions プロトコル ネゴシエーションに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="784e5-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="784e5-104">説明</span><span class="sxs-lookup"><span data-stu-id="784e5-104">Description</span></span>  
 <span data-ttu-id="784e5-105">OleTx 情報が添付された受信トランザクションがその OleTx 情報を使用できず、代わりに WS-AT 使用した場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="784e5-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="784e5-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="784e5-106">Troubleshooting</span></span>  
 <span data-ttu-id="784e5-107">コンピューター間の MSDTC RPC 通信に潜在的な問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="784e5-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="784e5-108">これらのトレースが多数ログに記録されている場合は、大幅なパフォーマンス低下が発生している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="784e5-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="784e5-109">OleTx が必要ない場合は、WS-AT のレジストリ構成で `OleTxUpgradeEnabled` を 0 に設定してください。</span><span class="sxs-lookup"><span data-stu-id="784e5-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="784e5-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="784e5-110">See Also</span></span>  
 [<span data-ttu-id="784e5-111">トレース</span><span class="sxs-lookup"><span data-stu-id="784e5-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="784e5-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="784e5-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="784e5-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="784e5-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
