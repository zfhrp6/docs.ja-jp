---
title: "SpinWait | Microsoft Docs"
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
  - "synchronization primitives, SpinWait"
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# SpinWait
<xref:System.Threading.SpinWait?displayProperty=fullName> は軽量な同期型で、負荷が高いコンテキスト スイッチやカーネル イベントに必要なカーネル遷移を避けるために下位レベルのシナリオで使用できます。  マルチコア コンピューターでは、リソースの保持時間が長くならないと予測される場合、待機中のスレッドを数十または数百サイクルの間ユーザー モードでスピンさせてから、リソースの取得を再試行した方が効率的です。  スピン後にリソースを使用できる場合は、数千サイクルを節約したことになります。  リソースをまだ使用できない場合でも、数サイクルを消費しただけであり、カーネル ベースの待機に移行できます。  スピン後に待機というこの組み合わせは、*2 フェーズ待機操作*と呼ばれることがあります。  
  
 <xref:System.Threading.SpinWait> は、<xref:System.Threading.ManualResetEvent> などのカーネル イベントをラップする .NET Framework 型と共に使用するように設計されています。  また、<xref:System.Threading.SpinWait> は、1 つのプログラムで基本的なスピン機能のために単独で使用することもできます。  
  
 <xref:System.Threading.SpinWait> は単なる空のループではありません。  一般的に、適切なスピン動作を提供するためには慎重に実装する必要があり、長時間 \(おおよそ、カーネル遷移に要する時間\) スピンすると、コンテキスト スイッチが開始されます。  たとえば、シングルコア コンピューターでは、スピンはすべてのスレッドの進行をブロックするので、<xref:System.Threading.SpinWait> はスレッドのタイム スライスを直ちに譲渡します。  マルチコア コンピューターでも、<xref:System.Threading.SpinWait> は、待機中のスレッドがより優先順位の高いスレッドやガベージ コレクターをブロックしないように譲渡します。  したがって、<xref:System.Threading.SpinWait> を 2 フェーズ待機操作で使用する場合は、<xref:System.Threading.SpinWait> 自体がコンテキスト スイッチを開始する前にカーネル待機を呼び出すことをお勧めします。  <xref:System.Threading.SpinWait> には <xref:System.Threading.SpinWait.NextSpinWillYield%2A> プロパティがあり、<xref:System.Threading.SpinWait.SpinOnce%2A> に対する毎回の呼び出しの前にこのプロパティをチェックできます。  このプロパティから `true` が返された場合、独自の待機操作が開始されます。  例については、「[How to: Use SpinWait to Implement a Two\-Phase Wait Operation](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)」を参照してください。  
  
 2 フェーズ待機操作は実行せずに、特定の条件が満たされるまでスピンを行うだけの場合は、Windows オペレーティング システム環境で問題を発生させることなく、<xref:System.Threading.SpinWait> を有効にしてコンテキスト スイッチを実行できます。  ロック制御の不要なスタックの <xref:System.Threading.SpinWait> を次の基本的な例に示します。  高パフォーマンスのスレッド セーフ スタックが必要な場合は、<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> の使用を検討してください。  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## 参照  
 <xref:System.Threading.Thread.SpinWait%2A>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)