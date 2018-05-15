---
title: 'エンドポイント : 1 秒あたりのトランザクション フロー'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: ff3d76025bbae0759dba005adbd62609701c5a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="ae113-102">エンドポイント : 1 秒あたりのトランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="ae113-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="ae113-103">カウンター名 : 1 秒あたりのトランザクション フロー。</span><span class="sxs-lookup"><span data-stu-id="ae113-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ae113-104">説明</span><span class="sxs-lookup"><span data-stu-id="ae113-104">Description</span></span>  
 <span data-ttu-id="ae113-105">このエンドポイントでの操作に対して実行された 1 秒あたりのトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="ae113-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="ae113-106">このカウンターは、エンドポイントに送信されたメッセージにトランザクション ID が付与されている場合は常にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="ae113-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="ae113-107">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="ae113-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ae113-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="ae113-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
