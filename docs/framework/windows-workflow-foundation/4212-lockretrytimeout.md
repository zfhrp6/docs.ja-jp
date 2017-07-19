---
title: "4212 - LockRetryTimeout | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4212 - LockRetryTimeout
## プロパティ  
  
|||  
|-|-|  
|ID|4212|  
|キーワード|WFInstanceStore|  
|レベル|警告|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 SQL プロバイダーはインスタンス ロックを取得しようとしてタイムアウトを検出しました。  
  
## メッセージ  
 インスタンスのロックを取得しようとしてタイムアウトが発生しました。%1 の割り当てられたタイムアウト時間内に操作が完了しませんでした。  この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Delay|xs:string|再試行の遅延。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|