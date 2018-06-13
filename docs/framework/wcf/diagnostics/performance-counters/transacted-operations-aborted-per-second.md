---
title: 1 秒あたりの中止されたトランザクション操作
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: dacdf93f4610df9161134a41ece19fd2a18637c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474533"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="bd1a5-102">1 秒あたりの中止されたトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="bd1a5-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="bd1a5-103">カウンター名 : 1 秒あたりの中止されたトランザクション処理数。</span><span class="sxs-lookup"><span data-stu-id="bd1a5-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bd1a5-104">説明</span><span class="sxs-lookup"><span data-stu-id="bd1a5-104">Description</span></span>  
 <span data-ttu-id="bd1a5-105">1 秒あたりに、このサービスで中止されたトランザクション処理の数です。</span><span class="sxs-lookup"><span data-stu-id="bd1a5-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="bd1a5-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="bd1a5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="bd1a5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="bd1a5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
