---
title: "Pausing and Resuming Threads | Microsoft Docs"
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
  - "resuming threads"
  - "threading [.NET Framework], pausing"
  - "pausing threads"
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Pausing and Resuming Threads
スレッドの活動を同期する最も一般的な方法は、スレッドのブロックと解放を行うか、コード領域またはオブジェクトをロックすることです。  ロックとブロックのしくみの詳細については、「[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
 また、スレッドそのものをスリープ状態にすることもできます。  スレッドがブロックされているかまたはスリープ状態の場合は、<xref:System.Threading.ThreadInterruptedException> を使用して待機状態を解除できます。  
  
## Thread.Sleep メソッド  
 <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> メソッドを呼び出すと、現在のスレッドはすぐに <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> に渡した何ミリ秒かの間ブロックされ、残りのタイム スライスはもう一方のスレッドに明け渡されます。  もう一方のスレッドが他方のスレッドに対して <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> を呼び出すことはできません。  
  
 <xref:System.Threading.Timeout.Infinite?displayProperty=fullName> を指定して <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> を呼び出すと、スレッドは、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> を呼び出す別のスレッドによって中断されるまで、または <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> によって中止されるまで、スリープ状態になります。  
  
## スレッドの中断  
 待機中のスレッドに割り込むには、ブロックされているスレッドに対して <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> を呼び出して <xref:System.Threading.ThreadInterruptedException> をスローさせることができます。これにより、待機中のスレッドは中断され、ブロックしている呼び出しから抜け出します。  スレッドは、<xref:System.Threading.ThreadInterruptedException> をキャッチし、操作を継続するために適切な処理を行う必要があります。  スレッドがこの例外を無視した場合は、ランタイムがこの例外をキャッチし、そのスレッドを停止します。  
  
> [!NOTE]
>  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> が呼び出されたときに対象となるスレッドがブロックされていない場合、スレッドはブロックされるまで中断されません。  スレッドがまったくブロックされない場合は、中断されることなく完了することがあります。  
  
 待機がマネージ待機である場合、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> と <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> はどちらもすぐにスレッドを起動します。  待機がアンマネージ待機の場合 \(プラットフォームが Win32 `WaitForSingleObject` 関数を呼び出した場合など\)、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> と <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> はどちらも、スレッドがマネージ コードに戻るか、またはマネージ コードを呼び出すまで、そのスレッドを制御できません。  マネージ コードの動作は次のとおりです。  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> はスレッドをどのような待機からも起動し、これによって起動先のスレッドで <xref:System.Threading.ThreadInterruptedException> がスローされます。  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> は、スレッドで <xref:System.Threading.ThreadAbortException> がスローされる点を除き、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> と同様です。  詳細については、「[スレッドの破棄](../../../docs/standard/threading/destroying-threads.md)」を参照してください。  
  
## 中断と再開 \(古い形式\)  
 <xref:System.Threading.Thread> クラスには、スレッドの一時停止と再開を行う 2 つのメソッドとして <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> と <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> が含まれています。  ただし、これらのメソッドの使用は推奨されません。  
  
> [!IMPORTANT]
>  .NET Framework version 2.0 以降で、<xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> メソッドと <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> メソッドは古い形式としてマークされており、今後のリリースで削除される予定です。  
>   
>  <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> メソッドと <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> メソッドは一般にアプリケーションに役立つことはなく、同期メカニズムと混同してはなりません。  <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> と <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> は、制御されているスレッドの連携に依存していないため、侵害性が高く、デッドロック \(別のスレッドが必要とするリソースを保持するスレッドを一時停止した場合など\) のような深刻なアプリケーション問題の原因となる可能性があります。  
  
 アプリケーションによっては、パフォーマンスを向上させるために、スレッドの優先順位を制御する必要があります。  スレッドの優先順位を制御するには、<xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> ではなく <xref:System.Threading.Thread.Priority%2A?displayProperty=fullName> プロパティを使用してください。  
  
## 参照  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadInterruptedException>   
 <xref:System.Threading.ThreadAbortException>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)   
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)