---
title: "1 秒あたりのコミットされたトランザクション操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0408bbc4bbe6e49bcd830a1de8563c02002f1b7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="43075-102">1 秒あたりのコミットされたトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="43075-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="43075-103">カウンター名 : 1 秒あたりのコミットされたトランザクション操作。</span><span class="sxs-lookup"><span data-stu-id="43075-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="43075-104">説明</span><span class="sxs-lookup"><span data-stu-id="43075-104">Description</span></span>  
 <span data-ttu-id="43075-105">1 秒あたりに、このサービスでコミットされたトランザクション操作の数です。</span><span class="sxs-lookup"><span data-stu-id="43075-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="43075-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="43075-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="43075-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="43075-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
