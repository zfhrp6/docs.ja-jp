---
title: "1004 - WorkflowInstanceAborted | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 1004 - WorkflowInstanceAborted
## プロパティ  
  
|||  
|-|-|  
|ID|1004|  
|キーワード|WFRuntime|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 ワークフロー インスタンスが例外で中断されたことを示します。  
  
## メッセージ  
 WorkflowInstance ID: '%1' は例外により中止されました。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|  
|例外|`xs:string`|例外の詳細|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|