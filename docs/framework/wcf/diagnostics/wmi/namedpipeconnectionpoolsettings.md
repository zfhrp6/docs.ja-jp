---
title: "NamedPipeConnectionPoolSettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# NamedPipeConnectionPoolSettings
NamedPipeConnectionPoolSettings  
  
## 構文  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## メソッド  
 NamedPipeConnectionPoolSettings クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 NamedPipeConnectionPoolSettings クラスには、次のプロパティがあります。  
  
### GroupName  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 バインド要素により使用される接続プールのグループ名。  
  
### IdleTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 接続が切断されるまでの最大アイドル時間。  
  
### MaxOutboundConnectionsPerEndpoint  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 クライアント上の各エンドポイントでの発信接続の最大数。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>