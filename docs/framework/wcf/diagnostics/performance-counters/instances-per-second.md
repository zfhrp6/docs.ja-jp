---
title: "1 秒あたりのインスタンス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 1 秒あたりのインスタンス
カウンター名 : 1 秒あたりに作成されたインスタンス。  
  
## 説明  
 1 秒あたりに作成されたサービス インスタンスの合計数です。  
  
 このカウンターは、パフォーマンス カウンター型 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) であり、その値は次の式を使用して計算されます。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)