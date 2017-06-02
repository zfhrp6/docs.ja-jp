---
title: "ServiceCredentials | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceCredentials
ServiceCredentials  
  
## 構文  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## メソッド  
 ServiceCredentials クラスで定義されるメソッドはありません。  
  
## プロパティ  
 ServiceCredentials クラスには、次のプロパティがあります。  
  
### ClientCertificate  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスのための、クライアント証明認証および提供設定です。  
  
### IssuedTokenAuthentication  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスのための、現在発行されているトークンの認証設定です。  
  
### Peer  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 ピアのトランスポート エンドポイントによって使用される、現在の証明書の認証および提供の設定です。  
  
### SecureConversationAuthentication  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 現在のセキュリティで保護された通信の設定を指定します。  
  
### ServiceCertificate  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスに関連付けられている証明書です。  
  
### UserNameAuthentication  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスのユーザー名\/パスワードの設定です。  
  
### WindowsAuthentication  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 このサービスの Windows 認証の設定です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.ServiceCredentials>