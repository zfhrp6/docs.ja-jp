---
title: 207 - FaultProviderInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9035739f8625a07e8bf2b9bce2fe109880676405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="207---faultproviderinvoked"></a>207 - FaultProviderInvoked
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|207|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、`FaultProvider` が呼び出された後に生成されます。  
  
## <a name="message"></a>メッセージ  
 ディスパッチャーが型 '%1' の FaultProvider を呼び出し、種類 '%2' の例外がスローされました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|呼び出された `FaultProvider` の型の CLR FullName。|  
|ExceptionTypeName|`xs:string`|`FaultProvider` の操作対象である例外の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
