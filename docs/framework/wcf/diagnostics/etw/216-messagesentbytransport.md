---
title: 216 - MessageSentByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad2b32b8d1386f6cc0754070cba2b1a556219b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|216|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、TCP ベースのトランスポートがメッセージを送信するときに発生します。 トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。 これはインフラストラクチャの動作によるもので、セキュリティがその一例です。 そのため、数**MessageSentByTransport**が生成されるイベント、サービスのバインディングとその構成に基づき、異なります。  
  
## <a name="message"></a>メッセージ  
 トランスポートが '%1' にメッセージを送信しました。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|要求メッセージが送信されたアドレス。|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
