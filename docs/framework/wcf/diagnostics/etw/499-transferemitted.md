---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469509"
---
# <a name="499---transferemitted"></a>499 - TransferEmitted
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|499|  
|キーワード|Troubleshooting、UserEvents、EndToEndMonitoring、ServiceModel、WFTracking、ServiceHost、WCFMessageLogging|  
|レベル|LogAlways (常にログ)|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、転送イベントが発生したときに生成されます。  
  
## <a name="message"></a>メッセージ  
 転送イベントが作成されました。  
  
## <a name="details"></a>説明  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。 例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
