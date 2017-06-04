---
title: "214 - OperationCompleted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 214 - OperationCompleted
## プロパティ  
  
|||  
|-|-|  
|ID|214|  
|キーワード|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|レベル|Information \(情報\)|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、サービス モデルの既定の `OperationInvoker` が、メソッドから例外がスローされることなく、メソッドへの呼び出しを完了したときに生成されます。  
  
## メッセージ  
 OperationInvoker がメソッド '%1' への呼び出しを完了しました。メソッド呼び出し時間は '%2' ミリ秒でした。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Method Name|`xs:string`|`OperationInvoker` によって呼び出されたメソッドの CLR 名。|  
|Duration|`xs:long`|`OperationInvoker` でメソッドを呼び出すのにかかった時間 \(ミリ秒単位\)。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、'Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名' と定義されます。例: 'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|