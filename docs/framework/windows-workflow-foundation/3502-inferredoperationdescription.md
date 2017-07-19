---
title: "3502 - InferredOperationDescription | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3502 - InferredOperationDescription
## プロパティ  
  
|||  
|-|-|  
|ID|3502|  
|キーワード|WFServices|  
|レベル|情報|  
|チャネル|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 説明  
 OperationDescription が WorkflowService から推論されたことを示します。  
  
## メッセージ  
 コントラクト '%2' 内の Name\='%1' の OperationDescription が WorkflowService から推論されました。  IsOneWay\=%3。  
  
## 詳細  
  
|データ項目名|データ項目の型|説明|  
|------------|-------------|--------|  
|OperationName|xs:string|操作の名前。|  
|ContractName|xs:string|コントラクトの名前。|  
|IsOneWay|xs:string|True または False はコントラクトが一方向かどうかを示します。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|