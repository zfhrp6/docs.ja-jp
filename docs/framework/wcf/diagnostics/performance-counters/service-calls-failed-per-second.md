---
title: "サービス : 1 秒あたりの失敗した呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 632c81b6ffd84202b7609dccb89887af01ae706e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-failed-per-second"></a>サービス : 1 秒あたりの失敗した呼び出し
カウンター名 : 1 秒あたりの失敗した呼び出し。  
  
## <a name="description"></a>説明  
 このサービスが 1 秒間に受信した未処理の例外を含む呼び出しの回数。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 マネージ コードでは、エラー条件が発生すると例外がスローされます。  
  
 マネージ コードでは、エラー条件が発生すると例外がスローされます。  
  
 このカウンターは、このサービスで未処理の例外が発生するたびにインクリメントされます。  
  
## <a name="see-also"></a>参照  
 [コントラクトおよびサービスのエラーの指定と処理](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
