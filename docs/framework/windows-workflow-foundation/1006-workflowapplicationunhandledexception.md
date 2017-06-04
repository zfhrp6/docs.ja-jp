---
title: "1006 - WorkflowApplicationUnhandledException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 1006 - WorkflowApplicationUnhandledException
## プロパティ  
  
|||  
|-|-|  
|ID|1006|  
|キーワード|WFRuntime|  
|レベル|Error|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 ワークフロー アプリケーションでハンドルされない例外が検出されたことを示します。  
  
## メッセージ  
 WorkflowInstance ID: '%1' でハンドルされない例外が発生しました。例外は Activity '%2'、DisplayName: '%3' から発生しました。次の操作が実行されます: %4。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|WorkflowInstanceId|`xs:string`|ワークフローのインスタンス ID|  
|例外|`xs:string`|例外の詳細|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName で返される文字列。|