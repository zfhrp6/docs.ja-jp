---
title: "2577 - TryCatchExceptionDuringCancelation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 2577 - TryCatchExceptionDuringCancelation
## プロパティ  
  
|||  
|-|-|  
|ID|2577|  
|キーワード|WFActivities|  
|レベル|警告|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 TryCatch アクティビティの子アクティビティが取り消し中に例外をスローしたことを示します。  
  
## メッセージ  
 TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|DisplayName|xs:string|アクティビティの表示名。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|