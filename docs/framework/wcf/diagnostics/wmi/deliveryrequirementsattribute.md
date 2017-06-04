---
title: "DeliveryRequirementsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## 構文  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## メソッド  
 DeliveryRequirementsAttribute クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 DeliveryRequirementsAttribute クラスには、次のプロパティがあります。  
  
### QueuedDeliveryRequirements  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスのバインドがコントラクトをサポートするかどうかを指定します。  
  
### RequireOrderedDelivery  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングが順序付きメッセージをサポートするかどうかを指定します。  
  
### TargetContract  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 適用先となるコントラクトです。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>