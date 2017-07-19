---
title: "4207 - MaximumRetriesExceededForSqlCommand | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 4207 - MaximumRetriesExceededForSqlCommand
## プロパティ  
  
|||  
|-|-|  
|ID|4207|  
|キーワード|クオータ、WFInstanceStore|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 再試行が最大実行回数実行されたので、SQL プロバイダーは SQL コマンドの再試行を停止しようとしていることを示します。  
  
## メッセージ  
 SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|