---
title: "ReliableSessionBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## 構文  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## メソッド  
 ReliableSessionBindingElement クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 ReliableSessionBindingElement クラスには、次のプロパティがあります。  
  
### AcknowledgementInterval  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 ファクトリによって作成された信頼できるチャネルで、メッセージの送信元に受信確認を送信するまで送信先が待機する時間  
  
### FlowControlEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 フロー制御を有効にするかどうかを示すブール値  
  
### InactivityTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 他の通信相手がチャネルにメッセージを送信せずにいられる最長期間を指定します。他の通信相手がメッセージを送信しない期間がこの値を超えると、チャネルでエラーが発生します。  
  
### MaxPendingChannels  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 リスナーで受け入れを待機できるチャネルの最大数。  
  
### MaxRetryCount  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 基になるチャネルで `Send` を呼び出すことで、信頼できるチャネルが受信確認を受信していないメッセージの再転送を試みる最大回数  
  
### MaxTransferWindowSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 信頼できるセッションの転送ウィンドウの最大サイズ  
  
### 順序あり  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 メッセージが送信された順序で到着されることを保証するかどうかを指定するブール値です。  
  
### ReliableMessagingVersion  
 データ型 : integer  
  
 アクセスの種類 : 読み取り専用  
  
 信頼できるセッションで使用される WS\-ReliableMessaging プロトコルのバージョンを指定する整数。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|Namespace|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>