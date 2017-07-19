---
title: "SpinLock | Microsoft Docs"
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
  - "synchronization primitives, SpinLock"
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# SpinLock
<xref:System.Threading.SpinLock> 構造体は、ロックの取得待機中にスピンする下位レベルの相互排他的な同期プリミティブです。  マルチコア コンピューターで、待機時間が短くなると予測され、競合が最小限に抑えられる場合、<xref:System.Threading.SpinLock> は他の種類のロックよりも優れたパフォーマンスを示すことがあります。  ただし、<xref:System.Threading.SpinLock> を使用するのは、<xref:System.Threading.Monitor?displayProperty=fullName> メソッドまたは <xref:System.Threading.Interlocked> メソッドによってプログラムのパフォーマンスが大幅に低下していることがプロファイリングにより判明している場合に限定することをお勧めします。  
  
 <xref:System.Threading.SpinLock> は、ロックをまだ取得していない場合でも、スレッドのタイム スライスを明け渡す可能性があります。  このようにすることで、スレッドの優先順位の逆転を防止し、ガベージ コレクターが処理を進められるようにします。  <xref:System.Threading.SpinLock> を使用する場合は、スレッドでロックが保持される期間を非常に短くし、ロックの保持中はブロックできないようにしてください。  
  
 SpinLock は値型であるため、2 つのコピーで同じロックを参照する場合は、参照渡しで明示的に渡す必要があります。  
  
 この型の使用方法の詳細については、「<xref:System.Threading.SpinLock?displayProperty=fullName>」を参照してください。  例については、「[How to: Use SpinLock for Low\-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)」を参照してください。  
  
 <xref:System.Threading.SpinLock> では、*スレッド* *追跡*モードがサポートされています。このモードは開発フェーズで使用でき、特定の時間にロックを保持しているスレッドを追跡するのに役立ちます。  スレッド追跡モードはデバッグに非常に有用ですが、パフォーマンスを低下させる可能性があるため、プログラムのリリース バージョンでは無効にすることをお勧めします。  詳細については、「[How to: Enable Thread\-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)」を参照してください。  
  
## 参照  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)