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
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87517687b486cc6cf3d2984623a502e3f5ecfa6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-faulted-per-second"></a>サービス : 1 秒あたりの失敗した呼び出し
カウンター名 : 1 秒あたりの失敗した呼び出し。  
  
## <a name="description"></a>説明  
 このサービスの呼び出しのうち、エラーを返したものの 1 秒あたりの回数です。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションでは、サービス メソッドは SOAP エラー メッセージを使用して操作エラー情報を通知します。 SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。 SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。  
  
## <a name="see-also"></a>参照  
 [コントラクトおよびサービスのエラーの指定と処理](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
