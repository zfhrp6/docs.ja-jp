---
title: "PeerTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# PeerTransportBindingElement
PeerTransportBindingElement  
  
## 構文  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## メソッド  
 PeerTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 PeerTransportBindingElement クラスには、次のプロパティがあります。  
  
### ListenIPAddress  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 ピア ノードがメッセージをリッスンする IP アドレスです。  
  
### Port  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングがピア チャネル メッセージを処理するネットワーク インターフェイス ポートです。  
  
### Security  
 データ型 : PeerSecuritySettings  
  
 アクセスの種類 : 読み取り専用  
  
 ピア トランスポートのセキュリティ設定です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>