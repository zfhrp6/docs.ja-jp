---
title: "ServiceSecurityAuditBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## 構文  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## メソッド  
 ServiceSecurityAuditBehavior クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ServiceSecurityAuditBehavior クラスには、次のプロパティがあります。  
  
### AuditLogLocation  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 監査ログの場所。  
  
### MessageAuthenticationAuditLevel  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 監査イベントをログに記録するために使用されるメッセージ認証レベルの種類。  
  
### ServiceAuthorizationAuditLevel  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 監査ログに記録される承認イベントの種類。  
  
### SuppressAuditFailure  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 監査ログへの書き込みエラーを非表示にする動作を指定するブール型の値。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>