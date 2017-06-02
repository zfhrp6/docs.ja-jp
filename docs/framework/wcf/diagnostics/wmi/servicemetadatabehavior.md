---
title: "ServiceMetadataBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## 構文  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## メソッド  
 ServiceMetadataBehavior クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ServiceMetadataBehavior クラスには、次のプロパティがあります。  
  
### ExternalMetadataLocation  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスがメタデータ要求をリダイレクトする場所を設定します。  
  
### HttpGetEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 `HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。  
  
### HttpGetUrl  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
### HttpsGetEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 `HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。  
  
### HttpsGetUrl  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>