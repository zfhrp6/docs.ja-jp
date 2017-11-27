---
title: 218 - ClientOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea826aa99e847f74c5a44113f2ae16d7322873f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="218---clientoperationcompleted"></a>218 - ClientOperationCompleted
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|218|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>説明  
 このイベントは、ある操作が完了した直後にクライアントによって生成されます。 一方向の操作の場合は、メッセージが正常に送信された直後に生成されます。 要求 - 応答の操作の場合は、応答の受信後に生成されます。  
  
## <a name="message"></a>メッセージ  
 クライアントは '%2' コントラクトと関連付けられている Action '%1' の実行を完了しました。 メッセージは '%3' に送信されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|アクション|xs:string|送信メッセージの SOAP アクション ヘッダー。|  
|Contract Name|`xs:string`|コントラクトの名前。 例: ICalculator。|  
|保存先|`xs:string`|メッセージの送信先のサービス エンドポイントのアドレス。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。 その形式とは見なさ ' Web サイト名アプリケーション仮想パス &#124;です。サービス仮想パス &#124;です。ServiceName' です。 例: ' 既定の Web サイト/CalculatorApplication &#124;/CalculatorService.svc &#124;です。CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
