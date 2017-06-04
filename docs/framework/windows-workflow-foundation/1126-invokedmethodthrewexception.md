---
title: "1126 - InvokedMethodThrewException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 1126 - InvokedMethodThrewException
## プロパティ  
  
|||  
|-|-|  
|ID|1126|  
|キーワード|WFRuntime|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 説明  
 InvokeMethod アクティビティによって呼び出されたメソッドにより、例外がスローされたことを示します。  
  
## メッセージ  
 アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。  %2  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|InvokeMethod|xs:string|InvokeMethod アクティビティの表示名。|  
|例外|xs:string|例外の詳細|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|