---
title: "エンドポイントのパフォーマンス カウンター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc5fa1b3600489cb2d5f31c263019ae5006edf65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-performance-counters"></a>エンドポイントのパフォーマンス カウンター
エンドポイントのパフォーマンス カウンターは、エンドポイントがどのようにメッセージを受信しているかを示すデータをキャプチャします。 パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelEndpoint 4.0.0.0` パフォーマンス オブジェクトの下にあります。 インスタンスの名前には次のパターンが使用されます。  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 このデータは、個々の操作で収集されるデータに似ていますが、そのエンドポイントだけで集約されたデータです。  
  
> [!CAUTION]
>  パフォーマンス カウンターのインスタンス名の長さには制限があります。 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] カウンターのインスタンス名の長さが最大長を超えると、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によってインスタンス名の一部はハッシュ値に置き換えられます。  
  
## <a name="see-also"></a>参照  
 [パフォーマンス カウンター](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
