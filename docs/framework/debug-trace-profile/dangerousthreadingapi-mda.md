---
title: "dangerousThreadingAPI MDA | Microsoft Docs"
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
  - "suspending threads"
  - "DangerousThreadingAPI MDA"
  - "managed debugging assistants (MDAs), dangerous threading operations"
  - "threading [.NET Framework], suspending"
  - "MDAs (managed debugging assistants), dangerous threading operations"
  - "Suspend method"
  - "threading [.NET Framework], managed debugging assistants"
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# dangerousThreadingAPI MDA
`dangerousThreadingAPI` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、現在のスレッド以外のスレッドで <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> メソッドが呼び出されるとアクティブになります。  
  
## 症状  
 アプリケーションがいつまでも応答しないかハングアップしています。  システムまたはアプリケーションのデータが一時的に、またはアプリケーションのシャットダウン後も、予期しない状態のままになっている可能性があります。  一部の操作が予期したとおりに完了していません。  
  
 問題には偶然性が伴うため、症状は非常に多岐にわたります。  
  
## 原因  
 スレッドは、<xref:System.Threading.Thread.Suspend%2A> メソッドを使用する別のスレッドによって、非同期に中断されています。  別のスレッドが操作中である可能性があるときに、そのスレッドを中断するタイミングを判断する方法はありません。  スレッドを中断すると、データの破損やインバリアントの中断が発生することがあります。  スレッドが中断状態になっていて、<xref:System.Threading.Thread.Resume%2A> メソッドで再開されないと、アプリケーションのハングアップ状態がいつまでも続き、アプリケーション データが損害を受けることがあります。  これらのメソッドは、互換性のために残されています。  
  
 同期プリミティブがターゲット スレッドによって保持されている場合は、中断の間も保持されたままになります。  これにより、<xref:System.Threading.Thread.Suspend%2A> を実行するスレッドのように別のスレッドがプリミティブのロックを取得しようとすると、デッドロックが発生することがあります。  この場合、問題自体がデッドロックとして現れます。  
  
## 解決策  
 <xref:System.Threading.Thread.Suspend%2A> および <xref:System.Threading.Thread.Resume%2A> を使用する必要のある設計を避けます。  スレッド間の協調では、<xref:System.Threading.Monitor>、<xref:System.Threading.ReaderWriterLock>、<xref:System.Threading.Mutex> などの同期プリミティブや、C\# の `lock` ステートメントを使用します。  これらのメソッドを使用する必要がある場合は、時間を短くし、スレッドが中断状態にある間に実行されるコードの量を最小限に留めます。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  危険なスレッド処理操作に関するデータを報告するだけです。  
  
## 出力  
 MDA は、アクティブになった原因である危険なスレッド処理メソッドを示します。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 `dangerousThreadingAPI` のアクティブ化の原因となる <xref:System.Threading.Thread.Suspend%2A> メソッド呼び出しのコード例を次に示します。  
  
```  
using System.Threading;  
void FireMda()  
{  
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();   
    t.Resume();  
    t.Join();  
}  
```  
  
## 参照  
 <xref:System.Threading.Thread>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [lock ステートメント](../Topic/lock%20Statement%20\(C%23%20Reference\).md)