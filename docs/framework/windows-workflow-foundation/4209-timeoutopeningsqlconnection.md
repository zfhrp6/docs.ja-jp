---
title: "4209 - TimeoutOpeningSqlConnection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4209 - TimeoutOpeningSqlConnection
## プロパティ  
  
|||  
|-|-|  
|ID|4209|  
|キーワード|WFInstanceStore|  
|レベル|Error|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 SQL 接続を開こうとしてタイムアウトが発生したことを示します。  
  
## メッセージ  
 SQL 接続を開こうとしてタイムアウトしました。  割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。  この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|Timeout|xs:string|SQL 接続を開く場合のタイムアウト値。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|