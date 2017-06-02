---
title: "コントラクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# コントラクト
Contract  
  
## 構文  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## メソッド  
 Contract クラスで定義されているメソッドはありません。  
  
## プロパティ  
 Contract クラスには、次のプロパティがあります。  
  
### AppDomainId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトをホストする appdomain の appdomain ID。  
  
### Behaviors  
 データ型 : Behavior 配列  
  
 アクセスの種類 : 読み取り専用  
  
 このコントラクトに関連付けられている動作。  
  
### Name  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 WSDL でのコントラクトの名前。  
  
### Namespace  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 WSDL での `portType` 要素の名前空間。  
  
### Operations  
 データ型 : Operation 配列  
  
 アクセスの種類 : 読み取り専用  
  
 このコントラクトの操作。  
  
### ProcessId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトをホストするプロセスのプロセス ID。  
  
### ref  
 データ型 : Contract  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトが双方向コントラクトのときのコールバックの型。  
  
### SessionMode  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトでチャネル セッションを使用するために、このコントラクトに関連付けられたバインディングが必要かどうかを示します。  
  
### Type  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 コントラクトの型。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.ContractDescription>