---
title: "TransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransportBindingElement
TransportBindingElement  
  
## 構文  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## メソッド  
 TransportBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 TransportBindingElement クラスには、次のプロパティがあります。  
  
### ManualAddressing  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 メッセージのアドレス指定をユーザーが制御するかどうかを指定するブール値。  
  
### MaxBufferPoolSize  
 データ型 : sint64  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングに使用するバッファー プールの最大サイズ。  
  
### MaxReceivedMessageSize  
 データ型 : sint64  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングで処理されるメッセージの最大サイズ。  
  
### Scheme  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 トランスポートの URI スキーム。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.TransportBindingElement>