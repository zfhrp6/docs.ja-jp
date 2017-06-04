---
title: "ChannelPoolSettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ChannelPoolSettings
ChannelPoolSettings  
  
## 構文  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## メソッド  
 ChannelPoolSettings クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ChannelPoolSettings クラスには、次のプロパティがあります。  
  
### IdleTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 接続が切断されるまでの最大アイドル時間。  
  
### LeaseTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 リース操作の完了がタイムアウトするまでの最大時間。  
  
### MaxOutboundChannelsPerEndpoint  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 各エンドポイントでの送信チャネルの最大数。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>