---
title: "39458 - TrackingRecordTruncated | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 39458 - TrackingRecordTruncated
## プロパティ  
  
|||  
|-|-|  
|ID|39458|  
|キーワード|WFTracking|  
|レベル|警告|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 追跡レコードが省略されたことを示します。  変数、注釈、ユーザー データは削除されています。  
  
## メッセージ  
 プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。  変数\/注釈\/ユーザー データは削除されました  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|RecordNumber|xs:string|追跡レコード番号。|  
|ProviderId|xs:string|ETW プロバイダー ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|