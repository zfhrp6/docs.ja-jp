---
title: "219 - ServiceException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 219 - ServiceException
## プロパティ  
  
|||  
|-|-|  
|ID|219|  
|キーワード|EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel|  
|レベル|Error \(エラー\)|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、WCF サービスがハンドルされない例外を検出した場合に生成されます。これには、アクティベーション中のハンドルされない例外、メッセージ処理中のハンドルされない例外、およびユーザー コード内でのハンドルされない例外が含まれます。  
  
## メッセージ  
 メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。完全な例外 ToString: %1。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|ExceptionToString|`xs:string`|CLR 例外に対して `ToString`\(\) を呼び出した結果。|  
|ExceptionTypeName|`xs:string`|例外の型の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、'Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名' と定義されます。例: 'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|