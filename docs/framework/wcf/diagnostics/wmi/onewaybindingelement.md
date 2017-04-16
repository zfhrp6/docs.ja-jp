---
title: "OneWayBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# OneWayBindingElement
OneWayBindingElement  
  
## 構文  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## メソッド  
 OneWayBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 OneWayBindingElement クラスには、次のプロパティがあります。  
  
### ChannelPoolSettings  
 データ型 : ChannelPoolSettings  
  
 アクセスの種類 : 読み取り専用  
  
 チャネル プールの設定。  
  
### MaxAcceptedChannels  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 許可されるチャネルの最大数。  
  
### PacketRoutable  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 パケットがルーティング可能かどうかを示す値。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>