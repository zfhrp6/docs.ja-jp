---
title: "1009 - ActivityScheduled | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1009 - ActivityScheduled
## プロパティ  
  
|||  
|-|-|  
|ID|1009|  
|キーワード|WFRuntime|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 アクティビティの実行がスケジュールされていることを示します。  
  
## メッセージ  
 Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|ParentActivity|xs:string|親アクティビティの型名。|  
|ParentDisplayName|xs:string|親アクティビティの表示名。|  
|ParentInstanceId|xs:string|親アクティビティのインスタンス ID。|  
|ChildActivity|xs:string|スケジュール済みの子アクティビティの型名。|  
|ChildDisplayName|xs:string|スケジュール済みの子アクティビティの表示名。|  
|ChildInstanceId|xs:string|スケジュール済み子アクティビティのインスタンス ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|