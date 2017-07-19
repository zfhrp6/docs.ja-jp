---
title: "4205 - FoundProcessingError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2235a15-dd87-439e-8cb9-8b1b89a3dacf
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4205 - FoundProcessingError
## プロパティ  
  
|||  
|-|-|  
|ID|4205|  
|キーワード|WFInstanceStore|  
|レベル|Error|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 SQL プロバイダー コマンドが失敗したことを示します。  
  
## メッセージ  
 コマンドが失敗しました: %1  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|ExceptionMessage|xs:string|SQL 例外からのメッセージ。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|