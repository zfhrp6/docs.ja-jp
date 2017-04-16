---
title: "3551 - BufferOutOfOrderMessageNoBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3551 - BufferOutOfOrderMessageNoBookmark
## プロパティ  
  
|||  
|-|-|  
|ID|3551|  
|キーワード|WFServices|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 ブックマークの再開が失敗したことを示します。  サービス インスタンスがこの特定の操作を処理する準備が整ったら、バッファーされた受信操作が再試行されます。  
  
## メッセージ  
 サービス インスタンス '%1' での操作 '%2' は現時点では実行できません。  サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|OperationName|xs:string|操作の名前。|  
|ServiceInstanceId|xs:string|サービス インスタンスの ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|