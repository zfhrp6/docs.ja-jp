---
title: "4211 - QueuingSqlRetry | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4211 - QueuingSqlRetry
## プロパティ  
  
|||  
|-|-|  
|ID|4211|  
|キーワード|WFInstanceStore|  
|レベル|警告|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 SQL の再試行をキューに登録していることを示します。  
  
## メッセージ  
 %1 ミリ秒の遅延で SQL の再試行をキューに登録しています。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Delay|xs:string|再試行の遅延。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|