---
title: "ServiceAppDomain | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceAppDomain
アプリケーション ドメインにサービスを割り当てます。  
  
## 構文  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## メソッド  
 ServiceAppDomain クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ServiceAppDomain クラスには、次のプロパティがあります。  
  
### ref  
 データ型 : Service               
 修飾子: キー  
  
 アクセスの種類 : 読み取り専用  
  
 このアプリケーション ドメインのサービスです。  
  
### ref  
 データ型: AppDomainInfo               
 修飾子: キー  
  
 アクセスの種類 : 読み取り専用  
  
 アプリケーション ドメインのプロパティが格納されています。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|