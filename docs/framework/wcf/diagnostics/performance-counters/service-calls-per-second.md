---
title: "サービス : 1 秒あたりの呼び出し数 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# サービス : 1 秒あたりの呼び出し数
カウンター名 : 1 秒あたりの呼び出し。  
  
## 説明  
 このサービスが 1 秒あたりに呼び出される回数です。  
  
 このカウンターは、パフォーマンス カウンター型 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) であり、その値は次の式を使用して計算されます。  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)。ここで、分子 \(N\) は最後のサンプル間隔中に実行された操作の数を表し、分母 \(D\) は最後のサンプル間隔中に経過したタイマー刻み数を表し、F はタイマー刻みの頻度を表します。