---
title: "エンドポイント : 1 秒あたりの呼び出し回数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480e0758df7e3062f9bd2b0b089c7a9b75e1c012
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="e79bd-102">エンドポイント : 1 秒あたりの呼び出し回数</span><span class="sxs-lookup"><span data-stu-id="e79bd-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="e79bd-103">カウンター名 : 1 秒あたりの呼び出し</span><span class="sxs-lookup"><span data-stu-id="e79bd-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e79bd-104">説明</span><span class="sxs-lookup"><span data-stu-id="e79bd-104">Description</span></span>  
 <span data-ttu-id="e79bd-105">このエンドポイントが 1 秒あたりに呼び出される回数です。</span><span class="sxs-lookup"><span data-stu-id="e79bd-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="e79bd-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="e79bd-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e79bd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e79bd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
