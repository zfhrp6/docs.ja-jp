---
title: "AppDomainInfo | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# AppDomainInfo
アプリケーション ドメイン情報  
  
## 構文  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## メソッド  
 AppDomainInfo クラスは、メソッドを一切定義しません。  
  
## プロパティ  
 AppDomainInfo クラスには、次のプロパティがあります。  
  
### AppDomainId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain の ID です。  
  
### IsDefault  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain が既定の AppDomain かどうかを示します。  
  
### LogMalformedMessages  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り\/書き込み  
  
 非整形式メッセージをログに記録するかどうかを指定する値です。  
  
### LogMessagesAtServiceLevel  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り\/書き込み  
  
 メッセージをサービス レベルでトレースするかどうかを指定する値です \(暗号化およびトランスポート関連の変換前\)。  
  
### LogMessagesAtTransportLevel  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り\/書き込み  
  
 メッセージをトランスポート レベルでトレースするかどうかを指定する値です。  
  
### MessageLoggingTraceListeners  
 データ型 : TraceListener 配列  
  
 アクセスの種類 : 読み取り専用  
  
 System.Wmi.MessageLogging トレース ソースをリッスンするコレクション トレース リスナーです。  
  
### Name  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain の名前です。  
  
### PerformanceCounters  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 AppDomain におけるアクティブなパフォーマンス カウンターのスコープです。  
  
### ProcessId  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 プロセス ID です。  
  
### ServiceConfigPath  
 データ型 : string  
  
 アクセスの種類 : 読み取り専用  
  
 サービスの構成へのパスです。  
  
### TraceLevel  
 データ型 : string  
  
 アクセスの種類 : 読み取り\/書き込み  
  
 System.Wmi トレース ソースのトレース レベル。  
  
### ServiceModelTraceListeners  
 データ型 : TraceListener 配列  
  
 アクセスの種類 : 読み取り専用  
  
 System.ServiceModel トレース ソースのリスナーのコレクション。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|