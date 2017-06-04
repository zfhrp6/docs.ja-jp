---
title: "1 秒あたりの破棄されたメッセージのキュー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 1 秒あたりの破棄されたメッセージのキュー
カウンター名 : 1 秒あたりの破棄されたメッセージのキュー。  
  
## 説明  
 このサービスでキューに置かれたトランスポートによって 1 秒あたりに破棄されたメッセージの数です。  
  
 このカウンターは、パフォーマンス カウンター型 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) であり、その値は次の式を使用して計算されます。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)