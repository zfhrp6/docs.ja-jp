---
title: "OperationBehaviorAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## 構文  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## メソッド  
 OperationBehaviorAttribute クラスで定義されるメソッドはありません。  
  
## プロパティ  
 OperationBehaviorAttribute クラスには、次のプロパティがあります。  
  
### AutoDisposeParameters  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 パラメーターの自動破棄機能の状態です。  
  
### Impersonation  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 操作がサポートする、呼び出し元の偽装レベルを示します。  
  
### ReleaseInstanceMode  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 操作の呼び出し過程のどの時点でオブジェクトをリサイクルするかを示します。  
  
### TransactionAutoComplete  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを示します。  
  
### TransactionScopeRequired  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 操作がトランザクションを必要とするかどうかを示します。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.OperationBehaviorAttribute>