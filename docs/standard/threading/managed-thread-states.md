---
title: "マネージ スレッドの状態 | Microsoft Docs"
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
  - "スレッド [.NET Framework]、状態"
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# マネージ スレッドの状態
プロパティ <xref:System.Threading.Thread.ThreadState%2A?displayProperty=fullName> には、スレッドの現在の状態を示すビット マスクが用意されています。 スレッドは、<xref:System.Threading.ThreadState> 列挙型に含まれる状態のうち、常に少なくとも 1 つの状態となり、同時に複数の状態になることもあります。  
  
> [!IMPORTANT]
>  スレッドの状態は、いくつかのデバッグ シナリオでのみ必要になります。 スレッドの動作を同期化する目的でコード内でスレッドの状態を使用しないでください。  
  
 マネージ スレッドを作成すると、そのスレッドは <xref:System.Threading.ThreadState> 状態になります。 スレッドは、オペレーティング システムによって起動状態にされるまで、<xref:System.Threading.ThreadState> 状態のままです。<xref:System.Threading.Thread.Start%2A> を呼び出すと、スレッドを開始できることをオペレーティング システムに通知できますが、スレッドの状態は変化しません。  
  
 マネージ環境に入ってくるアンマネージ スレッドは、既に起動状態になっています。 スレッドがいったん起動状態になると、さまざまなアクションによってスレッドの状態が変更される可能性があります。 状態が変更される原因となるアクションと、対応する新しい状態を次の表に示します。  
  
|アクション|変更後の新しい状態|  
|-----------|---------------|  
|<xref:System.Threading.Thread> クラスのコンストラクターが呼び出される。|<xref:System.Threading.ThreadState>|  
|別のスレッドが <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> を呼び出す。|<xref:System.Threading.ThreadState>|  
|スレッドが <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> に応答して実行を開始する。|<xref:System.Threading.ThreadState>|  
|スレッドが <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> を呼び出す。|<xref:System.Threading.ThreadState>|  
|スレッドが別のオブジェクトで <xref:System.Threading.Monitor.Wait%2A?displayProperty=fullName> を呼び出す。|<xref:System.Threading.ThreadState>|  
|スレッドが別のスレッドで <xref:System.Threading.Thread.Join%2A?displayProperty=fullName> を呼び出す。|<xref:System.Threading.ThreadState>|  
|別のスレッドが <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> を呼び出す。|<xref:System.Threading.ThreadState>|  
|スレッドが <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> 要求に応答する。|<xref:System.Threading.ThreadState>|  
|別のスレッドが <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> を呼び出す。|<xref:System.Threading.ThreadState>|  
|別のスレッドが <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> を呼び出す。|<xref:System.Threading.ThreadState>|  
|スレッドが <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> に応答する。|<xref:System.Threading.ThreadState> の後 <xref:System.Threading.ThreadState>|  
  
 <xref:System.Threading.ThreadState> 状態の値は 0 のため、ビット テストを実行しても、この状態を検出できません。 代わりに、擬似コードによる次のテストを実行できます。  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 スレッドは、どの時点でも複数の状態にあることがよくあります。 たとえば、<xref:System.Threading.Monitor.Wait%2A?displayProperty=fullName> 呼び出しでスレッドがブロックされ、別のスレッドが同じスレッドに対して <xref:System.Threading.Thread.Abort%2A> を呼び出した場合、スレッドは同時に <xref:System.Threading.ThreadState> 状態と <xref:System.Threading.ThreadState> 状態になります。 この場合、スレッドは、<xref:System.Threading.Monitor.Wait%2A> への呼び出しから戻るか中断されるとすぐに、<xref:System.Threading.ThreadAbortException> を受け取ります。  
  
 スレッドは、<xref:System.Threading.Thread.Start%2A> への呼び出しの結果として <xref:System.Threading.ThreadState> 状態から出ると、<xref:System.Threading.ThreadState> 状態に戻ることはできません。 また、スレッドは <xref:System.Threading.ThreadState> 状態から出ることはできません。  
  
## 参照  
 <xref:System.Threading.ThreadAbortException>   
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadState>   
 [Threading](../../../docs/standard/threading/index.md)