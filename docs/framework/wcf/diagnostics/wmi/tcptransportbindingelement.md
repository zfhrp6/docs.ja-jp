---
title: "TcpTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TcpTransportBindingElement
TcpTransportBindingElement  
  
## 構文  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## メソッド  
 TcpTransportBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 TcpTransportBindingElement クラスには、次のプロパティがあります。  
  
### ConnectionPoolSettings  
 データ型 : TcpConnectionPoolSettings  
  
 アクセスの種類 : 読み取り専用  
  
 接続プールの設定。  
  
### ListenBacklog  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 保留可能なキュー内の接続要求の最大数です。  
  
### PortSharingEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 TCP ポート共有をこの接続で有効にするかどうかを指定するブール値です。  
  
### TeredoEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 Teredo \(ファイアウォールの内側にあるクライアントをアドレス指定するためのテクノロジ\) を有効にするかどうかを指定するブール値です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>