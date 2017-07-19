---
title: "発生したコレクション | Microsoft Docs"
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
  - "ガベージ コレクション、強制"
ms.assetid: 019008fe-4708-4e65-bebf-04fd9941e149
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# 発生したコレクション
ほとんどの場合、コレクションの実行に最適なタイミングはガベージ コレクターが判断できるので、ガベージ コレクターに任せるのが良い方法です。  ただし、ごくまれに、強制的にコレクションを実行するとアプリケーションのパフォーマンスが向上する場合があります。  このような場合は、<xref:System.GC.Collect%2A?displayProperty=fullName> メソッドを使用してガベージ コレクションを強制的に実行できます。  
  
 アプリケーションのコードの特定の位置で、使用しているメモリ量が大きく減少する場合は、<xref:System.GC.Collect%2A?displayProperty=fullName> メソッドを使用します。  たとえば、複数のコントロールのある複雑なダイアログ ボックスを使用するアプリケーションでは、ダイアログ ボックスを閉じるときに <xref:System.GC.Collect%2A> を呼び出すと、ダイアログ ボックスの使用メモリが直ちに再利用されてパフォーマンスが向上する可能性があります。  適切でない回数でガベージ コレクターがオブジェクトの再利用を試みるとパフォーマンスが低下する場合があるので、アプリケーションではあまり頻繁にガベージ コレクションを強制しないでください。  次のセクションで説明するように、コレクションの効果がある場合にのみ、<xref:System.GC.Collect%2A> のメソッドに対して収集する <xref:System.GCCollectionMode?displayProperty=fullName> の列挙値を指定できます。  
  
## GC コレクション モード  
 <xref:System.GCCollectionMode> 値を含む <xref:System.GC.Collect%2A?displayProperty=fullName> メソッド オーバーロードの 1 つを使用して、強制的コレクションの動作を次のように指定できます。  
  
|`GCCollectionMode` の値|説明|  
|---------------------------|--------|  
|<xref:System.GCCollectionMode>|実行中のバージョンの .NET Framework の既定のガベージ コレクション設定を使用します。|  
|<xref:System.GCCollectionMode>|直ちにガベージ コレクションを強制的に実行します。  これは、<xref:System.GC.Collect?displayProperty=fullName> オーバーロードを呼び出すのと同じです。  結果として、すべてのジェネレーションのフル ブロッキング コレクションになります。<br /><br /> また、直ちにフル ブロッキング ガベージ コレクションを強制的に実行する前に、<xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName> プロパティを <xref:System.Runtime.GCLargeObjectHeapCompactionMode?displayProperty=fullName> に設定して、大きなオブジェクト ヒープを圧縮することもできます。|  
|<xref:System.GCCollectionMode>|オブジェクトを再利用するのに現在が最適なときかどうかをガベージ コレクターが判断できるようにします。<br /><br /> ガベージ コレクターは、コレクションの実行を正当化できるほど効果がないと判断して、オブジェクトを再利用せずに戻る場合があります。|  
  
## バックグラウンドまたはブロッキング コレクション  
 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29?displayProperty=fullName> メソッド オーバーロードを呼び出して、発生するコレクションがブロッキング コレクションであるかどうかを指定できます。  実行されるコレクションの型は、メソッドの `mode` と `blocking` のパラメーターの組み合わせによって異なります。  `mode` は <xref:System.GCCollectionMode> 列挙体のメンバーです。`blocking` は <xref:System.Boolean> 値です。  `mode` と `blocking` 引数の相互作用を次の表にまとめます。  
  
|`mode`|`blocking` \= `true`|`blocking` \= `false`|  
|------------|--------------------------|---------------------------|  
|<xref:System.GCCollectionMode> または <xref:System.GCCollectionMode>|ブロッキング コレクションはできるだけ早く実行されます。  バックグラウンド コレクションが実行中でジェネレーションが 0 または 1 の場合、<xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> メソッドは直ちにブロッキング コレクションをトリガーし、コレクションが終了すると制御を戻します。  バックグラウンド コレクションが実行中で `generation` パラメーターが 2 の場合、メソッドはバックグラウンド コレクションの終了を待機し、ジェネレーション 2 のブロッキング コレクションをトリガーして、制御を戻します。|コレクションはできるだけ早く実行されます。  <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> メソッドはバックグラウンド コレクションを要求しますが、それは保証されず、状況によってはブロッキング コレクションが実行される場合もあります。  バックグラウンド コレクションが既に実行中の場合、メソッドはすぐに制御を返します。|  
|<xref:System.GCCollectionMode>|ガベージ コレクターおよび `generation` パラメーターの状態によっては、ブロッキング コレクションが実行される場合があります。  ガベージ コレクターは最適なパフォーマンスを提供しようとします。|ガベージ コレクターの状態によっては、コレクションが実行される場合があります。  <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%29> メソッドはバックグラウンド コレクションを要求しますが、それは保証されず、状況によってはブロッキング コレクションが実行される場合もあります。  ガベージ コレクターは最適なパフォーマンスを提供しようとします。  バックグラウンド コレクションが既に実行中の場合、メソッドはすぐに制御を返します。|  
  
## 参照  
 [Latency Modes](../../../docs/standard/garbage-collection/latency.md)   
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)