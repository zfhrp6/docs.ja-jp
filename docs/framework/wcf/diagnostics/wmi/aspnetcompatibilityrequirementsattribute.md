---
title: "AspNetCompatibilityRequirementsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00908a39-a21b-4029-bbb9-33e5a6ed25a7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# AspNetCompatibilityRequirementsAttribute
AspNetCompatibilityRequirementsAttribute  
  
## 構文  
  
```  
class AspNetCompatibilityRequirementsAttribute : Behavior  
{  
  string RequirementsMode;  
};  
```  
  
## メソッド  
 AspNetCompatibilityRequirementsAttribute クラスは、メソッドをすべて定義しません。  
  
## プロパティ  
 AspNetCompatibilityRequirementsAttribute クラスには、次のプロパティがあります。  
  
### RequirementsMode  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 Asp.Net 互換モードがアクティブであるかどうかを示します。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.ServiceHostingEnvironment.AspNetCompatibilityEnabled%2A>