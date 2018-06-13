---
title: 1 秒あたりのキューに置かれた有害メッセージ
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473260"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="cbf67-102">1 秒あたりのキューに置かれた有害メッセージ</span><span class="sxs-lookup"><span data-stu-id="cbf67-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="cbf67-103">カウンター名 : 1 秒あたりのキューに置かれた有害メッセージ</span><span class="sxs-lookup"><span data-stu-id="cbf67-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cbf67-104">説明</span><span class="sxs-lookup"><span data-stu-id="cbf67-104">Description</span></span>  
 <span data-ttu-id="cbf67-105">このサービスでキューに置かれたトランスポートによって 1 秒あたりに有害とマークされたメッセージの数です。</span><span class="sxs-lookup"><span data-stu-id="cbf67-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="cbf67-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="cbf67-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cbf67-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cbf67-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
