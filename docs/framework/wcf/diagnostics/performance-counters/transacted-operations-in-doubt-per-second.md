---
title: 1 秒あたりの不明なトランザクション操作
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: e165e934f17d599a9bb89f2702bb74d1ba0bf633
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474312"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="7c147-102">1 秒あたりの不明なトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="7c147-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="7c147-103">カウンター名 : 1 秒あたりの不明なトランザクション操作。</span><span class="sxs-lookup"><span data-stu-id="7c147-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7c147-104">説明</span><span class="sxs-lookup"><span data-stu-id="7c147-104">Description</span></span>  
 <span data-ttu-id="7c147-105">このサービスでの 1 秒あたりの結果が不明なトランザクション操作の数です。</span><span class="sxs-lookup"><span data-stu-id="7c147-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="7c147-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="7c147-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7c147-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="7c147-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
