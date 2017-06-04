---
title: "セキュリティ ETW イベント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW, セキュリティ イベント (CLR)"
  - "セキュリティ イベント [.NET Framework]"
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# セキュリティ ETW イベント
<a name="top"></a> セキュリティ イベントは、厳密な名前の検証時と Authenticode の検証時に発生します。  
  
 このカテゴリは、次のイベントで構成されます。  
  
-   [StrongNameVerificationStart\_V1 イベントと StrongNameVerificationStop\_V1 イベント](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [AuthenticodeVerificationStart\_V1 イベントと AuthenticodeVerificationStop\_V1 イベント](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## StrongNameVerificationStart\_V1 イベントと StrongNameVerificationStop\_V1 イベント  
 次の表に、キーワードとレベルを示します。 \(詳細については、「[CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください\)。  
  
|イベントを発生させるキーワード|レベル|  
|---------------------|---------|  
|`SecurityKeyword` \(0x400\)|情報通知 \(4\)|  
  
 次の表に、イベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|----------|-------------|-------------|  
|`StrongNameVerificationStart_V1`|181|厳密な名前の検証の開始。|  
|`StrongNameVerificationStop_V1`|182|厳密な名前の検証の終了。|  
  
 次の表に、イベント データを示します。  
  
|フィールド名|データ型|説明|  
|------------|----------|--------|  
|VerificationFlags|win:UInt32|検証フラグ。|  
|ErrorCode|win:UInt32|HResult エラー コード。|  
|FullyQualifiedAssemblyName|win:UnicodeString|完全修飾アセンブリ名。|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
 [ページのトップへ](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## AuthenticodeVerificationStart\_V1 イベントと AuthenticodeVerificationStop\_V1 イベント  
 次の表に、キーワードとレベルを示します。  
  
|イベントを発生させるキーワード|レベル|  
|---------------------|---------|  
|`SecurityKeyword` \(0x400\)|情報通知 \(4\)|  
  
 次の表に、イベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|----------|-------------|-------------|  
|`AuthenticodeVerificationStart_V1`|183|Authenticode 検証の開始。|  
|`AuthenticodeVerificationStop_V1`|184|Authenticode 検証の終了。|  
  
 次の表に、イベント データを示します。  
  
|フィールド名|データ型|説明|  
|------------|----------|--------|  
|VerificationFlags|win:UInt32|検証フラグ。|  
|ErrorCode|win:UInt32|HResult エラー コード。|  
|ModulePath|win:UnicodeString|モジュール パス|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
## 参照  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)