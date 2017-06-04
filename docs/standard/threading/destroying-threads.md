---
title: "Destroying Threads | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "destroying threads"
  - "threading [.NET Framework], destroying threads"
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Destroying Threads
マネージ スレッドを完全に停止するには、<xref:System.Threading.Thread.Abort%2A> メソッドを使用します。  <xref:System.Threading.Thread.Abort%2A> を呼び出すと、共通言語ランタイムが対象スレッドに <xref:System.Threading.ThreadAbortException> をスローします。対象スレッドはこの例外をキャッチできます。  詳細については、「<xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>」を参照してください。  
  
> [!NOTE]
>  スレッドがアンマネージ コードを実行しているときに、その <xref:System.Threading.Thread.Abort%2A> メソッドが呼び出された場合、ランタイムはスレッドを <xref:System.Threading.ThreadState?displayProperty=fullName> とマークします。  スレッドがマネージ コードに戻ると例外がスローされます。  
  
 スレッドは、一度アボートされると、再起動できません。  
  
 <xref:System.Threading.Thread.Abort%2A> メソッドを呼び出しても、対象スレッドは <xref:System.Threading.ThreadAbortException> をキャッチし、`finally` ブロック内の任意の量のコードを実行できるため、すぐには中止されません。  スレッドが終了するまで待機する必要がある場合は、<xref:System.Threading.Thread.Join%2A?displayProperty=fullName> を呼び出すことができます。  <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> はブロッキング呼び出しで、スレッドが実際に実行を停止するか、オプションのタイムアウト間隔が経過するまで制御が戻りません。  中止されたスレッドは、<xref:System.Threading.Thread.ResetAbort%2A> メソッドを呼び出したり、`finally` ブロックで非バインド処理を実行したりする可能性があります。そのため、タイムアウトを指定していない場合、待機の終了は保証されません。  
  
 <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> メソッドの呼び出しを待機しているスレッドは、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> を呼び出す他のスレッドによって中断される可能性があります。  
  
## ThreadAbortException の処理  
 独自のコードから <xref:System.Threading.Thread.Abort%2A> を呼び出した結果、またはスレッドが動作しているアプリケーション ドメインをアンロード \(<xref:System.AppDomain.Unload%2A?displayProperty=fullName> は <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> を使用してスレッドを終了します\) した結果としてスレッドが中止されるようにする場合、スレッドは、次のコードに示すように <xref:System.Threading.ThreadAbortException> を処理し、`finally` 句の最終処理を実行する必要があります。  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 `finally` 句の末尾、または `finally` 句が存在しない場合は `catch` 句の末尾で、<xref:System.Threading.ThreadAbortException> がシステムによって再スローされるため、`catch` 句または `finally` 句にクリーンアップ コードを配置する必要があります。  
  
 この例外をシステムが再スローしないようにするには、<xref:System.Threading.Thread.ResetAbort%2A?displayProperty=fullName> メソッドを呼び出します。  ただし、この操作は、独自のコードが原因で <xref:System.Threading.ThreadAbortException> が生成された場合に限定する必要があります。  
  
## 参照  
 <xref:System.Threading.ThreadAbortException>   
 <xref:System.Threading.Thread>   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)