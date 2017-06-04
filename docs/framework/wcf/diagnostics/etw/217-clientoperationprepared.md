---
title: "217 - ClientOperationPrepared | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 217 - ClientOperationPrepared
## プロパティ  
  
|||  
|-|-|  
|ID|217|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、操作がサービスに送信される直前に、クライアントによって生成されます。  
  
## メッセージ  
 クライアントは '%2' コントラクトと関連付けられている Action '%1' を実行しています。メッセージは '%3' に送信されます。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Action|`xs:string`|送信メッセージの SOAP アクション ヘッダー。|  
|Contract Name|`xs:string`|コントラクトの名前。例: ICalculator。|  
|Destination|`xs:string`|メッセージの送信先となるサービス エンドポイントのアドレス。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、'Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名' と定義されます。例: 'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|