---
title: LocalServiceSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f4cc5d0676ef397f67bd9d16b2b19c6f3ee2d57e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="methods"></a>メソッド  
 LocalServiceSecuritySettings クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 LocalServiceSecuritySettings クラスには、次のプロパティがあります。  
  
### <a name="detectreplays"></a>DetectReplays  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 チャネルに対するリプレイ攻撃を検出し、自動的に処理するかどうかを指定するブール値です。  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 サービスがサポートする保留状態のセキュリティ セッションの最大数。  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 すべての新しいセキュリティ クッキーに対して発行する有効期間を指定する TimeSpan です。  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 キャッシュできるクッキーの最大数。  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 通信している双方の 2 つのシステム クロックのずれの最長時間を指定する TimeSpan です。  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 サービスにおける保留状態の接続の最大数です。  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 同時にアクティブにできるセキュリティ ネゴシエーションの数。  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 サーバーとクライアント間のセキュリティ ネゴシエーション フェーズの最大継続時間を指定する TimeSpan です。  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 WS-ReliableMessaging を使用した接続が、トランスポート エラーの後再接続を試みるかどうかを指定するブール値です。  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 リプレイ検証で使用されるキャッシュ済みの nonce の数。  
  
### <a name="replaywindow"></a>ReplayWindow  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 個別のメッセージの nonce の有効期間を指定する TimeSpan です。  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 イニシエーターがセキュリティ セッションのキーを更新するまでの期間を指定する TimeSpan です。  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 キーの更新中に、前のセッション キーが受信メッセージで有効な時間間隔を指定する TimeSpan です。  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 データ型 : datetime  
  
 アクセスの種類 : 読み取り専用  
  
 タイムスタンプの有効期間を指定する TimeSpan です。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
