---
title: 'エンドポイント : 1 秒あたりの呼び出し回数'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: 186d59d2f0255f0f964130659a2053fc8f440dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474507"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="4301f-102">エンドポイント : 1 秒あたりの呼び出し回数</span><span class="sxs-lookup"><span data-stu-id="4301f-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="4301f-103">カウンター名 : 1 秒あたりの呼び出し</span><span class="sxs-lookup"><span data-stu-id="4301f-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4301f-104">説明</span><span class="sxs-lookup"><span data-stu-id="4301f-104">Description</span></span>  
 <span data-ttu-id="4301f-105">このエンドポイントが 1 秒あたりに呼び出される回数です。</span><span class="sxs-lookup"><span data-stu-id="4301f-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="4301f-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="4301f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4301f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="4301f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
