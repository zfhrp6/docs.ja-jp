---
title: "ServiceToEndpointAssociation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceToEndpointAssociation
エンドポイントにサービスを割り当てます。  
  
## 構文  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## メソッド  
 ServiceToEndpointAssociation クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ServiceToEndpointAssociation クラスには、次のプロパティがあります。  
  
### ref  
 データ型 : Service  
  
 アクセスの種類 : 読み取り専用  
修飾子: キー  
  
 エンドポイントに関連付けられるサービス。  
  
### ref  
 データ型 : Endpoint  
  
 アクセスの種類 : 読み取り専用  
修飾子: キー  
  
 サービスに関連付けられるエンドポイント。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|