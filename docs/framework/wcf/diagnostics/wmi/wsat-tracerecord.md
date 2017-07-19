---
title: "WSAT_TraceRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# WSAT_TraceRecord
WSAT\_TraceRecord  
  
## 構文  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## メソッド  
 WSAT\_TraceRecord クラスで定義されるメソッドはありません。  
  
## プロパティ  
 WSAT\_TraceRecord クラスには、次のプロパティがあります。  
  
### ActivityID  
 データ型: object  
アクセスの種類 : 読み取り専用  
  
 トレース レコードのアクティビティ ID です。  
  
### EventID  
 データ型 : sint32  
アクセスの種類 : 読み取り専用  
  
 トレース レコードのイベント ID です。  
  
### TraceRecord  
 データ型: string  
アクセスの種類 : 読み取り専用  
  
 トレース レコード  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|