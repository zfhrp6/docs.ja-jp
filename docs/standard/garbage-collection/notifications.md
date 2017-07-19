---
title: "Garbage Collection Notifications | Microsoft Docs"
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
  - "garbage collection, notifications"
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# Garbage Collection Notifications
共通言語ランタイムによるフル ガベージ コレクション \(つまり、ジェネレーション 2 のコレクション\) がパフォーマンスに悪影響を及ぼす可能性がある場合があります。  これは、特に大量の要求を処理するサーバーで問題になります。このような環境では、長時間のガベージ コレクションにより要求がタイムアウトします。  重要な処理を実行している最中にフル ガベージ コレクションが実行されないようにするために、フル ガベージ コレクションが近づいていることが通知されます。これを受けて、作業負荷を別のサーバー インスタンスにリダイレクトするためのアクションを実行できます。  現在のサーバー インスタンスが要求を処理する必要がなければ、ガベージ コレクションをユーザーが強制的に実行することもできます。  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> メソッドは、フル ガベージ コレクションが近づいていることをランタイムが検知したときに通知を発生するように登録します。  この通知には、フル ガベージ コレクションが近づいている場合と、フル ガベージ コレクションが完了した場合の 2 つがあります。  
  
> [!WARNING]
>  ガベージ コレクションをブロックのみ通知を発生させてします。  [\<gcConcurrent\>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 構成要素が有効になっている場合、バックグラウンド ガベージ コレクションが通知を発生させません。  
  
 通知が発生したことを判断するには、<xref:System.GC.WaitForFullGCApproach%2A> メソッドおよび <xref:System.GC.WaitForFullGCComplete%2A> メソッドを使用します。  一般に、これらのメソッドを `while` ループ内で使用し、通知の状態を表す <xref:System.GCNotificationStatus> 列挙型を継続的に取得します。  その値が <xref:System.GCNotificationStatus> であれば、以下のいずれかの処理を実行します。  
  
-   <xref:System.GC.WaitForFullGCApproach%2A> メソッドで取得した通知を受け、作業負荷をリダイレクトします。ガベージ コレクションを手動で強制的に実行することもできます。  
  
-   <xref:System.GC.WaitForFullGCComplete%2A> メソッドで取得した通知を受け、現在のサーバー インスタンスで再度要求を処理できるようにします。  情報を収集することもできます。  たとえば、<xref:System.GC.CollectionCount%2A> メソッドを使用して、ガベージ コレクションの回数を記録できます。  
  
 <xref:System.GC.WaitForFullGCApproach%2A> メソッドと <xref:System.GC.WaitForFullGCComplete%2A> メソッドは、連携して動作するように設計されています。  どちらか一方だけを使用すると、結果が不定になります。  
  
## フル ガベージ コレクション  
 ランタイムでフル ガベージ コレクションが発生するのは、以下に示すいくつかのシナリオに該当する場合です。  
  
-   十分なメモリがジェネレーション 2 に移動され、次のジェネレーション 2 のガベージ コレクションが発生する場合。  
  
-   十分なメモリが、大きいオブジェクトのヒープに移動され、次のジェネレーション 2 のガベージ コレクションが発生する場合。  
  
-   その他の要因により、ジェネレーション 1 のガベージ コレクションがジェネレーション 2 のガベージ コレクションに移行する場合。  
  
 <xref:System.GC.RegisterForFullGCNotification%2A> メソッドで指定するしきい値は、最初の 2 つのシナリオに該当します。  ただし、最初のシナリオでは、以下の 2 つの理由から、指定したしきい値に比例したタイミングで常に通知を受け取るとは限りません。  
  
-   ランタイムは、パフォーマンス上の理由から、小さなオブジェクトの割り当てをチェックしません。  
  
-   メモリがジェネレーション 2 に移動されるのは、ジェネレーション 1 のガベージ コレクションが実行された場合だけです。  
  
 3 番目のシナリオも、通知を受け取るタイミングに不確定性が生じる原因になります。  保証されるわけではないものの、この間要求をリダイレクトしたり、都合の良いときに自分でガベージ コレクションを強制的に実行したりして、タイミングの悪いフル ガベージ コレクションの影響を緩和することは有効な方法です。  
  
## 通知しきい値パラメーター  
 <xref:System.GC.RegisterForFullGCNotification%2A> メソッドには、ジェネレーション 2 のオブジェクトと大きなオブジェクトのヒープのしきい値を指定する 2 つのパラメーターがあります。  これらの値を超えると、ガベージ コレクションの通知が発行されます。  次の表でこれらのパラメーターについて説明します。  
  
|パラメーター|説明|  
|------------|--------|  
|`maxGenerationThreshold`|ジェネレーション 2 に移動されたオブジェクトに基づいて通知を発行するタイミングを指定する、1 ～ 99 の数値。|  
|`largeObjectHeapThreshold`|大きなオブジェクトのヒープに割り当てられたオブジェクトに基づいて通知を発行するタイミングを指定する、1 ～ 99 の数値。|  
  
 指定した値が大きすぎると、通知を受け取る可能性が高まりますが、ランタイムでガベージ コレクションが実行されるまでに長い時間待つことになります。  ガベージ コレクションを手動で強制的に実行すると、ランタイムでガベージ コレクションが実行される場合よりも多くのオブジェクトが解放されます。  
  
 指定した値が小さすぎると、通知を受け取るのに十分な時間がないうちにガベージ コレクションが実行される可能性があります。  
  
## 例  
  
### 説明  
 次の例では、サーバーのグループが受信した Web 要求を処理します。  要求の処理による作業負荷をシミュレートするため、バイト配列が <xref:System.Collections.Generic.List%601> コレクションに追加されています。  各サーバーはガベージ コレクションの通知を登録し、ユーザー メソッド `WaitForFullGCProc` でスレッドを開始して、<xref:System.GC.WaitForFullGCApproach%2A> メソッドと <xref:System.GC.WaitForFullGCComplete%2A> メソッドで返される <xref:System.GCNotificationStatus> 列挙型を継続的に監視します。  
  
 <xref:System.GC.WaitForFullGCApproach%2A> メソッドと <xref:System.GC.WaitForFullGCComplete%2A> メソッドは、通知が発行されると、それぞれのイベント処理用ユーザー メソッドを呼び出します。  
  
-   `OnFullGCApproachNotify`  
  
     このメソッドはユーザー メソッド `RedirectRequests` を呼び出し、要求をキューに格納するサーバーに対して、このサーバーへの要求の送信を一時停止するよう指示します。  この動作は、それ以上オブジェクトが割り当てられないように、クラスレベル変数 `bAllocate` に `false` を設定することでシミュレートされます。  
  
     次に、ユーザー メソッド `FinishExistingRequests` が呼び出され、保留中のサーバー要求の処理を終了します。  この動作は、<xref:System.Collections.Generic.List%601> コレクションをクリアすることでシミュレートされます。  
  
     最後に、作業負荷が軽いため、ガベージ コレクションが強制的に実行されます。  
  
-   `OnFullGCCompleteNotify`  
  
     サーバーがフル ガベージ コレクションの影響を受ける可能性が低くなったため、ユーザー メソッド `AcceptRequests` を呼び出し、要求の受付を再開します。  この動作は、`bAllocate` 変数に `true` を設定し、オブジェクトの <xref:System.Collections.Generic.List%601> コレクションへの追加を再開することでシミュレートされます。  
  
 この例の `Main` メソッドのコードを次に示します。  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 次のコードは、ユーザー メソッド `WaitForFullGCProc` のコードであり、ガベージ コレクションの通知を継続的にチェックする while ループが含まれています。  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 次のコードは、`OnFullGCApproachNotify` メソッドのコードです。  
  
 `WaitForFullGCProc` メソッド  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 次のコードは、`OnFullGCApproachComplete` メソッドのコードです。  
  
 `WaitForFullGCProc` メソッド  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 次のコードは、`OnFullGCApproachNotify` メソッドと `OnFullGCCompleteNotify` メソッドから呼び出されるユーザー メソッドです。  このユーザー メソッドは、要求のリダイレクト、既存の要求の終了、フル ガベージ コレクションの実行後の要求の受け付け再開を実行します。  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 コード例全体を次に示します。  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## 参照  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)