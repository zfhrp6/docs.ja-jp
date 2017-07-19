---
title: "ConnectionOrientedTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## 構文  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## メソッド  
 ConnectionOrientedTransportBindingElement クラスで定義されているメソッドはありません。  
  
## プロパティ  
 ConnectionOrientedTransportBindingElement クラスには、次のプロパティがあります。  
  
### ChannelInitializationTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 チャネルの初期化が開始されてからタイムアウトになるまでの時間の長さを示す期間。  
  
### ConnectionBufferSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズ。  
  
### HostNameComparisonMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 URI の照合時にサービスに到達するため、ホスト名が使用されたかどうかを示す値。  
  
### MaxBufferSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 使用するバッファーの最大サイズ。  
  
### MaxOutputDelay  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間。  
  
### MaxPendingAccepts  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 サービスでの着信接続処理に使用できる保留中の非同期受け入れスレッドの最大数。  
  
### MaxPendingConnections  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 保留状態の接続の最大数。  
  
### TransferMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 接続指向トランスポートを使用して、メッセージをバッファーするかまたはストリームするかを指定する値。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>