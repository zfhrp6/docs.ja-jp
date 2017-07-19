---
title: "ClientCredentials | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ClientCredentials
ClientCredentials  
  
## 構文  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## メソッド  
 ClientCredentials クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ClientCredentials クラスには、次のプロパティがあります。  
  
### ClientCertificate  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用する X.509 証明書です。  
  
### HttpDigest  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 現在の Http ダイジェスト資格情報です。  
  
### IssuedToken  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 ローカル セキュリティ トークン サービスにアクセスするために使用されるエンドポイント アドレスおよびバインディングです。  
  
### Peer  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報です。  
  
### ServiceCertificate  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスの X.509 証明書です。  
  
### SupportInteractive  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 資格情報が対話的なネゴシエーションをサポートしているかどうかを指定するブール値です。  
  
### UserName  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用するユーザー名とパスワードです。  
  
### Windows  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 クライアントがサービスに対して自身を認証するために使用する Windows 資格情報です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Description.ClientCredentials>