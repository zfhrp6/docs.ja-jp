---
title: 1 秒あたりのコミットされたトランザクション操作
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 3bec51a7be63c54a240b85032ecac09b87173393
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474273"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="1ba27-102">1 秒あたりのコミットされたトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="1ba27-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="1ba27-103">カウンター名 : 1 秒あたりのコミットされたトランザクション操作。</span><span class="sxs-lookup"><span data-stu-id="1ba27-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ba27-104">説明</span><span class="sxs-lookup"><span data-stu-id="1ba27-104">Description</span></span>  
 <span data-ttu-id="1ba27-105">1 秒あたりに、このサービスでコミットされたトランザクション操作の数です。</span><span class="sxs-lookup"><span data-stu-id="1ba27-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="1ba27-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="1ba27-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1ba27-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1ba27-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
