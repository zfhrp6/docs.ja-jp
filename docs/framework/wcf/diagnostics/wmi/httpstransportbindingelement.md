---
title: "HttpsTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e78aa8c6-b53b-4105-a900-d3e7a39670f2
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HttpsTransportBindingElement
HttpsTransportBindingElement  
  
## 構文  
  
```  
class HttpsTransportBindingElement : HttpTransportBindingElement  
{  
  boolean RequireClientCertificate;  
};  
```  
  
## メソッド  
 HttpsTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 HttpsTransportBindingElement クラスには、次のプロパティがあります。  
  
### RequireClientCertificate  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 SSL クライアント認証が必要かどうかを示す値。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>