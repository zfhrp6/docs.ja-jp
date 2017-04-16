---
title: "3550 - BufferOutOfOrderMessageNoInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3550 - BufferOutOfOrderMessageNoInstance
## プロパティ  
  
|||  
|-|-|  
|ID|3550|  
|キーワード|WFServices|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 バッファーされた受信機能が失敗したことを示します。  サービス インスタンスがこの特定の操作を処理する準備が整った場合、操作が再試行されます。  
  
## メッセージ  
 操作 '%1' は現時点では実行できません。  サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|OperationName|xs:string|操作の名前。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|