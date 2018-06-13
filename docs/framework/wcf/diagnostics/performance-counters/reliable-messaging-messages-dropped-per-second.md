---
title: 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 9a87ec509b19f0c566b50ae3672a6c3d2940ee12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474195"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="23c45-102">信頼できるメッセージの 1 秒あたりの破棄されたメッセージ</span><span class="sxs-lookup"><span data-stu-id="23c45-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="23c45-103">カウンター名 : 1 秒あたりに破棄された信頼できるメッセージ セッション</span><span class="sxs-lookup"><span data-stu-id="23c45-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="23c45-104">説明</span><span class="sxs-lookup"><span data-stu-id="23c45-104">Description</span></span>  
 <span data-ttu-id="23c45-105">このサービスで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。</span><span class="sxs-lookup"><span data-stu-id="23c45-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="23c45-106">このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。</span><span class="sxs-lookup"><span data-stu-id="23c45-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="23c45-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="23c45-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
