---
title: "Exception Thrown_V1 ETW イベント | Microsoft Docs"
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
  - "ETW, ExceptionThrown_V1 イベント (CLR)"
  - "ExceptionThrown_V1 イベント [.NET Framework]"
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: 6
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# Exception Thrown_V1 ETW イベント
このイベントは、スローされた例外に関する情報をキャプチャします。  
  
 このイベントが発生するキーワードとイベントのレベルを次の表に示します \(詳細については、「[CLR ETW キーワードおよびレベル](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください\)。  
  
|イベントを発生させるキーワード|Level|  
|---------------------|-----------|  
|`ExceptionKeyword` \(0x8000\)|警告 \(2\)|  
  
 イベント情報を次の表に示します。  
  
|イベント|イベント ID|いつ発生するか|  
|----------|-------------|-------------|  
|`ExceptionThrown_V1`|80|マネージ例外がスローされました。|  
  
 イベント データを次の表に示します。  
  
|フィールド名|データ型|説明|  
|------------|----------|--------|  
|例外の種類|win:UnicodeString|例外の型 \(`System.NullReferenceException` など\)。|  
|Exception Message|win:UnicodeString|実際の例外メッセージ。|  
|EIPCodeThrow|win:Pointer|例外が発生した命令ポインター。|  
|ExceptionHR|win:UInt32|例外 [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679)。|  
|ExceptionFlags|win:UInt16|0x01: HasInnerException \(Visual Basic のドキュメントの「[CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)」を参照してください\)。<br /><br /> 0x02: IsNestedException。<br /><br /> 0x04: IsRethrownException。<br /><br /> 0x08: プロセス状態が破損していることを示しています \(IsCorruptedStateException; MSDN [破損した状態の例外処理](http://go.microsoft.com/fwlink/?LinkId=179681) で参照してください。<br /><br /> 0x10: IsCLSCompliant \(<xref:System.Exception> から派生する例外は CLS 準拠です。それ以外の例外は CLS 準拠ではありません\)。|  
|ClrInstanceID|win:UInt16|CLR または CoreCLR のインスタンスの一意の ID。|  
  
## 参照  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)