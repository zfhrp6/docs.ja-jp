---
title: "競合 ETW イベント | Microsoft Docs"
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
  - "競合イベント [.NET Framework]"
  - "ETW, 競合イベント (CLR)"
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 競合 ETW イベント
競合イベントは、ランタイムによって使用される <xref:System.Threading.Monitor?displayProperty=fullName> ロックまたはネイティブ ロックの競合が発生するたびに発生します。  競合は、別のスレッドが保持しているロックをスレッドが待機しているときに発生します。  
  
 競合イベントが発生するキーワードとイベントのレベルを次の表に示します \(詳細については、「[CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください\)。  
  
|イベントを発生させるキーワード|Level|  
|---------------------|-----------|  
|`ContentionKeyword` \(0x4000\)|情報提供 \(4\)|  
  
 イベント情報を次の表に示します。  
  
|イベント|イベント ID|いつ発生するか|  
|----------|-------------|-------------|  
|`ContentionStart_V1`|81|競合が開始されたとき。  このイベントには、スレッドがロックの取得を待機する前のスピン時間は含まれません。このイベントが発生するのは、スレッドがロックの取得を待機するときだけです。|  
|`ContentionStop`|81|競合が終了したとき。|  
  
 イベント データを次の表に示します。  
  
|フィールド名|データ型|説明|  
|------------|----------|--------|  
|フラグ|win:UInt8|0 \(マネージ\) または 1 \(ネイティブ\)。|  
|ClrInstanceID|win:UInt16|CLR のインスタンスの一意の ID。|  
  
## 参照  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)