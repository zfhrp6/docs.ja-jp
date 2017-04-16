---
title: "PrivacyNoticeBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## 構文  
  
```  
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## メソッド  
 PrivacyNoticeBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 PrivacyNoticeBindingElement クラスには、次のプロパティがあります。  
  
### PrivacyNoticeVersion  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 プライバシーに関する声明のバージョンです。  
  
### Url  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 プライバシーに関する声明がある URL です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>