---
title: "1146 - FlowchartSwitchCase | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 274e9209-1720-4512-a615-e742f00895f4
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1146 - FlowchartSwitchCase
## プロパティ  
  
|||  
|-|-|  
|ID|1146|  
|キーワード|WFActivities|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 フローチャート スイッチで、どの例が選択されたかを示します。  
  
## メッセージ  
 フローチャート '%1'\/FlowSwitch \- Case '%2' が選択されました。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|FlowChart|xs:string|FlowChart の表示名。|  
|Case|xs:string|選択したスイッチに示します。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|