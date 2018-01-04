---
title: "1 秒あたりのキューに置かれた拒否メッセージ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b413c5076e41990a794b9aa33efd371480835353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="queued-rejected-messages-per-second"></a>1 秒あたりのキューに置かれた拒否メッセージ
カウンター名 : 1 秒あたりに拒否されたキューに置かれたメッセージ。  
  
## <a name="description"></a>説明  
 このサービスでキューに置かれたトランスポートによって 1 秒あたりに拒否されたメッセージの数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
