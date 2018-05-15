---
title: 1 秒あたりのキューに置かれた拒否メッセージ
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 31091c6c9dd04ecd7294f69f9611f25e401df724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="ada5b-102">1 秒あたりのキューに置かれた拒否メッセージ</span><span class="sxs-lookup"><span data-stu-id="ada5b-102">Queued Rejected Messages Per Second</span></span>
<span data-ttu-id="ada5b-103">カウンター名 : 1 秒あたりに拒否されたキューに置かれたメッセージ。</span><span class="sxs-lookup"><span data-stu-id="ada5b-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ada5b-104">説明</span><span class="sxs-lookup"><span data-stu-id="ada5b-104">Description</span></span>  
 <span data-ttu-id="ada5b-105">このサービスでキューに置かれたトランスポートによって 1 秒あたりに拒否されたメッセージの数です。</span><span class="sxs-lookup"><span data-stu-id="ada5b-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="ada5b-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="ada5b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ada5b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="ada5b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
