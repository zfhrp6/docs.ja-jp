---
title: "How to: Use SpinLock for Low-Level Synchronization | Microsoft Docs"
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
  - "SpinLock, how to use"
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# How to: Use SpinLock for Low-Level Synchronization
<xref:System.Threading.SpinLock> の使用方法を次の例に示します。  
  
## 使用例  
 この例では、クリティカル セクションが実行する作業量は最小限であるため、<xref:System.Threading.SpinLock> に適しています。  作業量が少し増えると、<xref:System.Threading.SpinLock> のパフォーマンスは標準的なロックよりも高くなります。  ただし、特定の時点から、標準的なロックよりも SpinLock の方が負荷が高くなります。  プロファイリング ツールの同時実行プロファイリング機能では、どの種類のロックを使用するとプログラムのパフォーマンスがより高くなるかを確認できます。  詳細については、「[同時実行ビジュアライザー](../Topic/Concurrency%20Visualizer.md)」を参照してください。  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> は、共有リソースに対するロックの保持が長時間にはならない場合に便利です。  このような場合、マルチコア コンピューターでは、ロックが解放されるまで数サイクルの間、ブロックされたスレッドをスピンさせると効率的です。  スピンにより、スレッドはブロックされなくなりますが、これは CPU 負荷の高いプロセスです。  ハイパースレッディングに対応したシステムでは、<xref:System.Threading.SpinLock> は特定の状況でスピンを停止して、論理プロセッサ リソースの不足や優先順位の逆転が発生するのを防ぎます。  
  
 この例では <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> クラスを使用しているため、マルチスレッド アクセスにはユーザーによる同期が必要となります。  .NET Framework Version 4 を対象とするアプリケーションでは、ユーザー ロックを必要としない <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> を使用する方法もあります。  
  
 <xref:System.Threading.SpinLock.Exit%2A> の呼び出しでは `false` \(Visual Basic では `False`\) を使用していることに注意してください。  これにより、最適なパフォーマンスが得られます。  メモリ フェンスを使用するには、IA64 アーキテクチャで `true` \(`True`\) を指定します。これにより、書き込みバッファーがフラッシュされるので、ロックを使用して他のスレッドを終了できるようになります。  
  
## 参照  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)