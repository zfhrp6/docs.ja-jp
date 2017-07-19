---
title: "TransactionFlowAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a9c8674-29f7-4f14-aa1f-dc2644ca57e4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# TransactionFlowAttribute
TransactionFlowAttribute  
  
## 構文  
  
```  
class TransactionFlowAttribute : Behavior  
{  
  string TransactionFlowOption;  
};  
```  
  
## メソッド  
 TransactionFlowAttribute クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 TransactionFlowAttribute クラスには、次のプロパティがあります。  
  
### TransactionFlowOption  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 トランザクションがフローするかどうかを示します。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.TransactionFlowAttribute>