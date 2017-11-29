---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="3cd20-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="3cd20-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="3cd20-103">PeerMaintainer モジュールは、特定の操作を実行しています (詳細はトレース メッセージの本文に含まれています)。</span><span class="sxs-lookup"><span data-stu-id="3cd20-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="3cd20-104">説明</span><span class="sxs-lookup"><span data-stu-id="3cd20-104">Description</span></span>  
 <span data-ttu-id="3cd20-105">このトレースは、各種の PeerMaintainer 操作中に行われます。</span><span class="sxs-lookup"><span data-stu-id="3cd20-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="3cd20-106">PeerMaintainer は PeerNode の内部コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="3cd20-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="3cd20-107">このコンポーネントは、毎分または 32 通のメッセージを受信するたびに近隣ノードに LinkUtility メッセージを送信します。このとき、交換されたメッセージ数と、有効な (重複および改ざんされていない) メッセージの数に関する統計が一緒に送信されます。</span><span class="sxs-lookup"><span data-stu-id="3cd20-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="3cd20-108">これは、特定の近隣ノードのリンク ユーティリティの特定に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3cd20-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="3cd20-109">約 5 分ごとに、保守管理者は近隣ノードの接続が正常かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3cd20-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="3cd20-110">近隣ノードへの接続数が適切な数を超えている場合、保守管理者は使用頻度が最も少ない接続を削除します。</span><span class="sxs-lookup"><span data-stu-id="3cd20-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="3cd20-111">接続数が十分でなければ、保守管理者は新しい接続を取得します。</span><span class="sxs-lookup"><span data-stu-id="3cd20-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd20-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cd20-112">See Also</span></span>  
 [<span data-ttu-id="3cd20-113">トレース</span><span class="sxs-lookup"><span data-stu-id="3cd20-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3cd20-114">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3cd20-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3cd20-115">管理と診断</span><span class="sxs-lookup"><span data-stu-id="3cd20-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
