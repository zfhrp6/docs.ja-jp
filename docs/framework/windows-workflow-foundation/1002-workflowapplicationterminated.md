---
title: "1002 - WorkflowApplicationTerminated | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 1002 - WorkflowApplicationTerminated
## プロパティ  
  
|||  
|-|-|  
|ID|1002|  
|キーワード|WFRuntime|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 例外が発生し、ワークフロー アプリケーションが Faulted 状態で終了したことを示します。  
  
## メッセージ  
 WorkflowApplication ID: %1 は中止されました。  例外により Faulted 状態で完了しました。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|WorkflowApplicationId|`xs:string`|ワークフロー アプリケーション ID|  
|例外|`xs:string`|例外の詳細|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|