---
title: "raceOnRCWCleanup MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "RCW"
  - "managed debugging assistants (MDAs), RCWs"
  - "race on RCW cleanup"
  - "MDAs (managed debugging assistants), RCWs"
  - "RaceOnRCWCleanup MDA"
  - "runtime callable wrappers"
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# raceOnRCWCleanup MDA
<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=fullName> メソッドなどのコマンドを使用して [ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW: Runtime Callable Wrapper\) を解放する呼び出しがなされた時点でその RCW が使用中であることを共通言語ランタイム \(CLR: Common Language Runtime\) が検出すると、`raceOnRCWCleanup` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) がアクティブ化されます。  
  
## 症状  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> メソッド、または類似メソッドを使用して RCW が解放中または解放後に、アクセス違反またはメモリ破損が発生します。  
  
## 原因  
 別のスレッドまたは解放中のスレッド スタックで、RCW が使用中です。  使用中の RCW は解放できません。  
  
## 解像度  
 現在のスレッドまたは他のスレッドで使用中の可能性がある RCW は、解放しないでください。  
  
## ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## 出力  
 エラーを説明するメッセージです。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)