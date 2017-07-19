---
title: "エンドポイント : 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# エンドポイント : 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
カウンター名 : 1 秒あたりに破棄された信頼できるメッセージ セッション  
  
## 説明  
 このエンドポイントで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。  
  
 このカウンターは、パフォーマンス カウンター型 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) であり、その値は次の式を使用して計算されます。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)