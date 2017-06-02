---
title: "ServiceAuthorizationBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## 構文  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## メソッド  
 ServiceAuthorizationBehavior クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ServiceAuthorizationBehavior クラスには、次のプロパティがあります。  
  
### impersonateCallerForAllOperations  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 受信メッセージによって提供される資格情報を使用してサービスが偽装を試みるかどうかを制御する値。  
  
### PrincipalPermissionMode  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サーバーでの操作を実行するために使用されるプリンシパル。  
  
### RoleProvider  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 ASP.NET ロール プロバイダーの名前。  
  
### ServiceAuthorizationManager  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 カスタム承認で使用される承認マネージャー。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>