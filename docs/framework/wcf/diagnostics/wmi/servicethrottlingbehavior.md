---
title: "ServiceThrottlingBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## 構文  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## メソッド  
 ServiceThrottlingBehavior クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ServiceThrottlingBehavior クラスには、次のプロパティがあります。  
  
### MaxConcurrentCalls  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 ServiceHost 内のすべてのディスパッチャー オブジェクトでアクティブに処理中のメッセージの最大数。  
  
### MaxConcurrentInstances  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 一度に実行可能なサービス オブジェクトの最大数。  
  
### MaxConcurrentSessions  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 ホストが一度に受け入れ可能なセッションの最大数。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|Namespace|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>