---
title: "LocalServiceSecuritySettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## 構文  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## メソッド  
 LocalServiceSecuritySettings クラスで定義されるメソッドはありません。  
  
## プロパティ  
 LocalServiceSecuritySettings クラスには、次のプロパティがあります。  
  
### DetectReplays  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。  
  
### InactivityTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 サービスがサポートする保留状態のセキュリティ セッションの最大数。  
  
### IssuedCookieLifetime  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 すべての新しいセキュリティ クッキーに対して発行する有効期間を指定する TimeSpan です。  
  
### MaxCachedCookies  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 キャッシュできるクッキーの最大数。  
  
### MaxClockSkew  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 通信している双方の 2 つのシステム クロックのずれの最長時間を指定する TimeSpan です。  
  
### MaxPendingSessions  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 サービスにおける保留状態の接続の最大数です。  
  
### MaxStatefulNegotiations  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 同時にアクティブにできるセキュリティ ネゴシエーションの数。  
  
### NegotiationTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 サーバーとクライアント間のセキュリティ ネゴシエーション フェーズの最大継続時間を指定する TimeSpan です。  
  
### ReconnectTransportOnFailure  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 WS\-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。  
  
### ReplayCacheSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 リプレイ検証で使用されるキャッシュ済みの nonce の数。  
  
### ReplayWindow  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 個別のメッセージの nonce の有効期間を指定する TimeSpan です。  
  
### SessionKeyRenewalInterval  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する TimeSpan です。  
  
### SessionKeyRolloverInterval  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する TimeSpan です。  
  
### TimestampValidityDuration  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 タイムスタンプの有効期間を指定する TimeSpan です。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み|  
|---------|-----------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>