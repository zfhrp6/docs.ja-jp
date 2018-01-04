---
title: "1 秒あたりの失敗した呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0979fdb6746a563d263b24ffc2fd83363cc98e74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="calls-faulted-per-second"></a>1 秒あたりの失敗した呼び出し
カウンター名 : 1 秒あたりの失敗した呼び出し  
  
## <a name="description"></a>説明  
 この操作への呼び出しに失敗した回数です (1 秒あたり)。  
  
 このカウンターは、パフォーマンス カウンター型[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)、次の数式を使用してその値を計算します。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションでは、サービス メソッドは SOAP エラー メッセージを使用して操作エラー情報を通知します。 SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型であり、堅牢かつインタラクティブに実行できるようにクライアントが使用するエラー コントラクトを作成するために使用されます。 SOAP エラーは XML 形式でクライアントに渡されるので、相互運用性の面でも優れています。  
  
## <a name="see-also"></a>参照  
 [コントラクトおよびサービスのエラーの指定と処理](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
