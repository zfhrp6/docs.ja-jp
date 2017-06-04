---
title: "スタック ETW イベント | Microsoft Docs"
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
  - "ETW, スタック イベント (CLR)"
  - "スタック イベント [.NET Framework]"
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# スタック ETW イベント
スタック イベントは、イベントの発生後にスタック トレースを生成するために他のイベントと組み合わせて使用します。  このイベントは、ランタイム プロバイダーが有効になっている場合に記録されます。  他のランタイム イベントが発生するたびに発生するため、非常に発生頻度が高く、  使用する際には注意が必要です。  
  
 次の表に、キーワードとレベルを示します。\(詳細については、「[CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください\)。  
  
|イベントを発生させるキーワード|Level|  
|---------------------|-----------|  
|`StackKeyword` \(0x40000000\)|LogAlways\(0\)|  
  
 次の表に、イベント情報を示します。  
  
|イベント|イベント ID|いつ発生するか|  
|----------|-------------|-------------|  
|`CLRStackWalk`|82|他のイベントとの組み合わせによって発生し、イベントの発生後にスタック トレースを生成します。|  
  
 次の表に、イベント データを示します。  
  
|フィールド名|データ型|説明|  
|------------|----------|--------|  
|ClrInstanceID|win:Uint16|一意のランタイム識別子。|  
|Reserved1|win:UInt8|予約済み。|  
|Reserved2|win:UInt8|予約済み。|  
|FrameCount|win:UInt32|スタック トレース内のフレーム数。|  
|Stack|win:Pointer|命令ポインターの列。|  
  
## 参照  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)