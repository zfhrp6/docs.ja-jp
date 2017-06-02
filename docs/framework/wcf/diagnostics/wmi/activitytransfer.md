---
title: "ActivityTransfer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ActivityTransfer
アクティビティ転送イベント  
  
## 構文  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## メソッド  
 ActivityTransfer クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ActivityTransfer クラスには次のプロパティがあります。  
  
### ActivityID  
  
-   データ型: object                   
     アクセスの種類 : 読み取り専用  
  
-   アクティビティ ID  
  
### RelatedActivityID  
  
-   データ型: object                   
     アクセスの種類 : 読み取り専用  
  
-   関連アクティビティ ID  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|