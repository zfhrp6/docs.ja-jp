---
title: "1 秒あたりのキューに置かれた有害メッセージ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8f22d200834927204918324ced70ac02c3c669f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="queued-poison-messages-per-second"></a>1 秒あたりのキューに置かれた有害メッセージ
カウンター名 : 1 秒あたりのキューに置かれた有害メッセージ  
  
## <a name="description"></a>説明  
 このサービスでキューに置かれたトランスポートによって 1 秒あたりに有害とマークされたメッセージの数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
