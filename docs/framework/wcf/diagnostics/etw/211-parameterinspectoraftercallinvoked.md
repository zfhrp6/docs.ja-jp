---
title: "211 - ParameterInspectorAfterCallInvoked | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 211 - ParameterInspectorAfterCallInvoked
## プロパティ  
  
|||  
|-|-|  
|ID|211|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、Service Model が `AfterCall` メソッドを `ParameterInspector` で呼び出した後に生成されます。  
  
## メッセージ  
 ディスパッチャーが型 '%1' の ParameterInspector で 'AfterCall' を呼び出しました。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|型の名前|`xs:string`|呼び出された `ParameterInspector` の型の CLR FullName。|  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  その形式は、'Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名' と定義されます。  例: 'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|