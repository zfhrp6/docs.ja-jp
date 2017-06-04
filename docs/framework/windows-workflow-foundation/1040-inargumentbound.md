---
title: "1040 - InArgumentBound | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7dfaad1b-36c0-4575-84c1-31d63b0eaf5d
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1040 - InArgumentBound
## プロパティ  
  
|||  
|-|-|  
|ID|1040|  
|キーワード|WFActivities|  
|レベル|詳細|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 In 引数がバインドされたことを示します。  
  
## メッセージ  
 Activity '%2' の引数 '%1' で、DisplayName: '%3'、InstanceId: '%4' が値: %5 にバインドされています。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|InArgument|xs:string|InArgument の名前。|  
|アクティビティ|xs:string|アクティビティの型名。|  
|DisplayName|xs:string|アクティビティの表示名。|  
|InstanceId|xs:string|アクティビティのインスタンス ID。|  
|値|xs:string|InArgument にバインドされた値。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|