---
title: "225 - TraceCorrelationKeys | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 225 - TraceCorrelationKeys
## プロパティ  
  
|||  
|-|-|  
|ID|225|  
|キーワード|Troubleshooting、ServiceModel|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 このイベントは、ワークフロー サービスでコンテンツ ベースの相関関係が使用されるときに生成されます。これには、メッセージとインスタンスの相関関係を定義するために適用されている相関関係キーが含まれます。  
  
## メッセージ  
 親スコープ '%3' の値 '%2' を使用して相関関係キー '%1' が計算されました。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Instance Key|`xs:GUID`|相関関係値から生成されたキー。|  
|Values|`xs:string`|相関関係インスタンス キーの計算に使用された値。|  
|Parent Scope|`xs:string`||  
|HostReference|`xs:string`|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。その形式は、'Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;サービス名' と定義されます。例: 'Default Web Site\/CalculatorApplication&#124;\/CalculatorService.svc&#124;CalculatorService'。|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|