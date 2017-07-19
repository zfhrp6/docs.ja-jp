---
title: "exceptionSwallowedOnCallFromCom MDA | Microsoft Docs"
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
  - "messages, informational"
  - "informational messages"
  - "managed debugging assistants (MDAs), exceptions"
  - "exception handling, managed debugging assistants"
  - "MDAs (managed debugging assistants), exceptions"
  - "ExceptionSwallowedOnCallFromCOM MDA"
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# exceptionSwallowedOnCallFromCom MDA
アンマネージ HRESULT 戻り値型を持たないメソッドを介して COM から呼び出された 共通言語ランタイム \(CLR\) コードから、例外がスローされると、`exceptionSwallowedOnCallFromCOM` マネージ デバッグ アシスタント \(MDA\) がアクティブ化されます。  
  
## 症状  
 COM からマネージ コンポーネントを呼び出すと、値 FALSE または 0 が返されます。  あるいは、メソッドの戻り値の型が void の場合、メソッド実行中に例外がスローされたという通知がない可能性があります。  この場合、例外は自動的にキャッチされ、COM 呼び出し元に実行が戻ります。  
  
## 原因  
 例外がスローされましたが、それを報告する有効な方法がありません。  
  
## 解決策  
 情報提供専用です。必ずしもバグを示すものではありません。  
  
## ランタイムへの影響  
 この MDA は CLR に影響しません。  自動的にキャッチされた例外を報告するだけです。  
  
## 出力  
 メソッド名、型名、例外メッセージが含まれている情報メッセージ。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)