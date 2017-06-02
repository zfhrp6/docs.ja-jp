---
title: "チャネル クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# チャネル クラス
チャネル  
  
## 構文  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## メソッド  
 チャネル クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 チャネル クラスには、次のプロパティがあります。  
  
### LocalAddress  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 チャネルのローカル エンドポイント。  
  
### ref  
 データ型 : Endpoint  
  
 アクセスの種類 : 読み取り専用  
  
 チャネルが接続するエンドポイントへの参照。  
  
### RemoteAddress  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 チャネルに関連するリモート アドレス。  
  
### SessionId  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 現在のセッション ID \(存在する場合\)。  
  
### 種類  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 チャネルの型。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.ChannelBase>