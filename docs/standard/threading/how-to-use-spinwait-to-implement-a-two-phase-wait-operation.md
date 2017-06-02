---
title: "How to: Use SpinWait to Implement a Two-Phase Wait Operation | Microsoft Docs"
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
  - "SpinWait, how to synchronize two-phase wait"
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Use SpinWait to Implement a Two-Phase Wait Operation
<xref:System.Threading.SpinWait?displayProperty=fullName> オブジェクトを使用して 2 フェーズ待機操作を実装する方法を次の例に示します。  最初のフェーズでは、同期オブジェクト `Latch` は、ロックが使用可能になったかどうかをチェックしながら数サイクルの間スピンします。  2 番目のフェーズでは、ロックが使用可能になると、<xref:System.Threading.ManualResetEvent?displayProperty=fullName> を使用して待機を実行することなく、`Wait` メソッドから制御が戻ります。それ以外の場合は、`Wait` は待機を実行します。  
  
## 使用例  
 この例は、Latch 同期プリミティブの非常に基本的な実装を示しています。  このデータ構造体は、待機時間が非常に短くなると予測される場合に使用できます。  この例は、デモンストレーションのためだけに作成されています。  ラッチ タイプの機能がプログラムに必要な場合は、<xref:System.Threading.ManualResetEventSlim?displayProperty=fullName> の使用を検討してください。  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 このラッチでは、`SpinOnce` を次に呼び出して <xref:System.Threading.SpinWait> がスレッドのタイム スライスを譲渡することになるまでの間だけ、<xref:System.Threading.SpinWait> オブジェクトを使用してその場でスピンします。  その時点で、<xref:System.Threading.ManualResetEvent> で <xref:System.Threading.WaitHandle.WaitOne%2A> を呼び出し、タイムアウト値の残りを渡すことによって、ラッチのコンテキスト スイッチが行われます。  
  
 ログ出力から、Latch が <xref:System.Threading.ManualResetEvent> を使用せずにロックを取得することでどの程度パフォーマンスを向上させることができたかがわかります。  
  
## 参照  
 [SpinWait](../../../docs/standard/threading/spinwait.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)