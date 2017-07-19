---
title: "4208 - RetryingSqlCommandDueToSqlError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4208 - RetryingSqlCommandDueToSqlError
## プロパティ  
  
|||  
|-|-|  
|ID|4208|  
|キーワード|WFInstanceStore|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。  
  
## メッセージ  
 SQL エラー番号 %1 のため、SQL コマンドを再試行します。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|ErrorNumber|xs:string|SQL エラー番号。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|