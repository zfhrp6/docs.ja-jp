---
title: "1 秒あたりのコミットされたトランザクション操作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 1 秒あたりのコミットされたトランザクション操作
カウンター名 : 1 秒あたりのコミットされたトランザクション操作。  
  
## 説明  
 1 秒あたりに、このサービスでコミットされたトランザクション操作の数です。  
  
 このカウンターは、パフォーマンス カウンター型 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) であり、その値は次の式を使用して計算されます。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)