---
title: "1 秒あたりのキューに置かれた有害メッセージ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 1 秒あたりのキューに置かれた有害メッセージ
カウンター名 : 1 秒あたりのキューに置かれた有害メッセージ  
  
## 説明  
 このサービスでキューに置かれたトランスポートによって 1 秒あたりに有害とマークされたメッセージの数です。  
  
 このカウンターは、パフォーマンス カウンター型 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) であり、その値は次の式を使用して計算されます。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)