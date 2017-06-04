---
title: "4203 - RenewLockSystemError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4203 - RenewLockSystemError
## プロパティ  
  
|||  
|-|-|  
|ID|4203|  
|キーワード|WFInstanceStore|  
|レベル|Error|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 ロックの有効期限が既に過ぎているか、またはロック所有者が削除されたために、SQL プロバイダーはロックの有効期限を延長できなかったことを示します。  SqlWorkflowInstanceStore は中止されます。  
  
## メッセージ  
 ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。  SqlWorkflowInstanceStore を中止します。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|