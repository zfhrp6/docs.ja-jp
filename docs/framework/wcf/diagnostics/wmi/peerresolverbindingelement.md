---
title: "PeerResolverBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36882183-13a3-443f-8aae-62a7825d5633
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# PeerResolverBindingElement
PeerResolverBindingElement  
  
## 構文  
  
```  
class PeerResolverBindingElement : BindingElement  
{  
  string ReferralPolicy;  
};  
```  
  
## メソッド  
 PeerResolverBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 PeerResolverBindingElement クラスには、次のプロパティがあります。  
  
### ReferralPolicy  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 ピア間で参照を共有する方法を指定します。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>