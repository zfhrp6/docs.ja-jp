---
title: "CustomBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df959dc5-1aef-4338-a123-6ff3e7bc37af
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# CustomBindingElement
CustomBindingElement  
  
## 構文  
  
```  
class CustomBindingElement : BindingElement  
{  
  string Name;  
};  
```  
  
## メソッド  
 CustomBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 CustomBindingElement クラスには、次のプロパティがあります。  
  
### 名前  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングの構成名を格納する文字列です。  この値は、カスタム バインディングの識別文字列として機能するユーザー定義文字列です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.CustomBinding>