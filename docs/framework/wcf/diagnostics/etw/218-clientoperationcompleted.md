---
title: "218 - ClientOperationCompleted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 218 - ClientOperationCompleted
## プロパティ  
  
|||  
|-|-|  
|ID|218|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、ある操作が完了した直後にクライアントによって生成されます。一方向の操作の場合は、メッセージが正常に送信された直後に生成されます。要求 \- 応答の操作の場合は、応答の受信後に生成されます。  
  
## メッセージ  
 クライアントは '%2' コントラクトと関連付けられている Action '%1' の実行を完了しました。メッセージは '%3' に送信されました。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Action|xs:string|送信メッセージの SOAP アクション ヘッダー。|  
|Contract Name|`xs:string`|コントラクトの名前。例: ICalculator。|  
|Destination|`xs:string`|メッセージの送信先のサービス エンドポイントのアドレス。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、'Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名' と定義されます。例: 'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|