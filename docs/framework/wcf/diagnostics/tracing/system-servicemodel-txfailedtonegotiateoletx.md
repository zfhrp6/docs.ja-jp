---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61360eff4f2c403eea98bbc0a2eae36e516b3d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="e7272-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="e7272-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="e7272-103">指定されたコーディネーション コンテキストのための OleTransactions プロトコル ネゴシエーションに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="e7272-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e7272-104">説明</span><span class="sxs-lookup"><span data-stu-id="e7272-104">Description</span></span>  
 <span data-ttu-id="e7272-105">OleTx 情報が添付された受信トランザクションがその OleTx 情報を使用できず、代わりに WS-AT 使用した場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="e7272-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e7272-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e7272-106">Troubleshooting</span></span>  
 <span data-ttu-id="e7272-107">コンピューター間の MSDTC RPC 通信に潜在的な問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="e7272-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="e7272-108">これらのトレースが多数ログに記録されている場合は、大幅なパフォーマンス低下が発生している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7272-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="e7272-109">OleTx が必要ない場合は、WS-AT のレジストリ構成で `OleTxUpgradeEnabled` を 0 に設定してください。</span><span class="sxs-lookup"><span data-stu-id="e7272-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7272-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7272-110">See Also</span></span>  
 [<span data-ttu-id="e7272-111">トレース</span><span class="sxs-lookup"><span data-stu-id="e7272-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e7272-112">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e7272-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e7272-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="e7272-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
