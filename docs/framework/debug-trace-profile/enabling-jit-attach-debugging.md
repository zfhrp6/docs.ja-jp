---
title: "Enabling JIT-Attach Debugging | Microsoft Docs"
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
  - "JIT-attach debugging"
  - "debugging [.NET Framework], JIT-attach debugging"
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Enabling JIT-Attach Debugging
JIT アタッチ デバッグとは、エラーが発生したときにデバッガーをプロセスにアタッチすることを記述するために使用される用語です。特定のメソッドまたは関数によって開始することもできます。  
  
 JIT アタッチ デバッグは、次のエラー条件下で使用されます。  
  
-   \(ネイティブ コードとマネージ コードの両方での\) 未処理の例外。  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=fullName> の メソッドまたは [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) 関数 \(Windows 7 ファミリ\)。  
  
-   ランタイムの致命的エラー。  
  
 JIT アタッチ デバッグは、次のメソッドと関数を呼び出すことでも開始できます。  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=fullName> メソッド  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=fullName> メソッド  
  
-   [Debugbreak](http://go.microsoft.com/fwlink/?LinkId=182106) 関数 \(Win32\)。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以前は、.NET Framework では、ネイティブ デバッガーとマネージ デバッガーの動作を制御するのに別々のレジストリ キーを提供していました。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降、制御は、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\Current Version\\AeDebug という単一のレジストリ キーに統合されました。  このキーに設定する値によってデバッガーを呼び出すかどうかを決定できます。呼び出す場合は、ユーザーによる操作が必要なダイアログ ボックスを表示するかどうかを決定できます。  このレジストリ キーの設定に関する詳細については、[設定の自動デバッグ](http://go.microsoft.com/fwlink/?LinkId=181767) MSDN ライブラリを参照してください。  
  
## 参照  
 [Debugging, Tracing, and Profiling](../../../docs/framework/debug-trace-profile/index.md)   
 [イメージのデバッグの簡略化](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)   
 [Enabling Profiling](http://msdn.microsoft.com/ja-jp/3b669676-f0e0-4ebf-8674-68986dd2020d)