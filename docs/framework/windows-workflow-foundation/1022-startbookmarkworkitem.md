---
title: "1022 - StartBookmarkWorkItem | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1022 - StartBookmarkWorkItem
## プロパティ  
  
|||  
|-|-|  
|ID|1022|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 BookmarkWorkItem が実行を開始していることを示します。  
  
## メッセージ  
 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の BookmarkWorkItem の実行を開始しています。BookmarkName: %4、BookmarkScope: %5。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|BookmarkName|xs:string|ブックマークの名前。|  
|BookmarkScope|xs:string|ブックマークのスコープ。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|