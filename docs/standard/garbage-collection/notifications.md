---
title: "ガベージ コレクションの通知"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41a2ed9c5d239f1570955e87bb5b749e29830bc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-notifications"></a>ガベージ コレクションの通知
パフォーマンスは、共通言語ランタイムによるフル ガベージ コレクション (つまり、ジェネレーション 2 のコレクション) に悪影響を及ぼす場合があります。 これが特に大量の要求を処理するサーバーで問題になります。この例では、長時間のガベージ コレクションには、要求のタイムアウトを可能性があります。重要な期間中に発生するを防ぐためには、通知が可能フル ガベージ コレクションが近づいていると、ワークロードを別のサーバー インスタンスにリダイレクトするアクションを実行します。 できますも強制的に実行するコレクション、自分で提供する現在のサーバー インスタンスが要求を処理する必要はありません。  
  
 <xref:System.GC.RegisterForFullGCNotification%2A>メソッドは、ランタイムは、フル ガベージ コレクションが近づいていることを検出するときに発生の通知を登録します。 この通知に 2 つの部分があります: フル ガベージ コレクションが近づいているときに、フル ガベージ コレクションが完了するとします。  
  
> [!WARNING]
>  唯一のブロッキング ガベージ コレクションは、通知を発生させます。 ときに、 [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)構成要素が有効になっている、バック グラウンド ガベージ コレクションでは、通知は発生しません。  
  
 調べるには、通知が発生したときに、使用、<xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドです。 通常、これらのメソッドを使用して、`while`を継続的に取得するループ、<xref:System.GCNotificationStatus>通知の状態を列挙します。 その値が場合<xref:System.GCNotificationStatus.Succeeded>次を行うことができます。  
  
-   取得された通知に応答、<xref:System.GC.WaitForFullGCApproach%2A>メソッド、ワークロードをリダイレクトしたり、場合によって引き起こされるコレクション自分でします。  
  
-   取得された通知に応答、<xref:System.GC.WaitForFullGCComplete%2A>方法、もう一度要求を処理に使用できる現在のサーバー インスタンスをすることができます。 情報を収集することもできます。 たとえば、使用することができます、<xref:System.GC.CollectionCount%2A>メソッドのコレクションの数を記録します。  
  
 <xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドは連携して動作するように設計されています。 せず、他のいずれかを使用すると、不確定な結果が生成することができます。  
  
## <a name="full-garbage-collection"></a>フル ガベージ コレクション  
 ランタイムでは、次のシナリオのいずれかに当てはまる場合にフル ガベージ コレクションが発生します。  
  
-   十分なメモリが次のジェネレーション 2 のコレクションが発生する第 2 世代に昇格されました。  
  
-   十分なメモリが、次のジェネレーション 2 のコレクションが発生する大きなオブジェクト ヒープに昇格されました。  
  
-   ジェネレーション 1 のガベージ コレクションは、その他の要因により第 2 世代のコレクションにエスカレートされます。  
  
 指定したしきい値、<xref:System.GC.RegisterForFullGCNotification%2A>メソッドが最初の 2 つのシナリオに適用します。 ただし、最初のシナリオでしていない常に、通知を受け取る 2 つの理由を指定するしきい値の値に比例した時に。  
  
-   ランタイムは、パフォーマンス上の理由により) 各小さなオブジェクトの割り当てをチェックしません。  
  
-   のみジェネレーション 1 のガベージ コレクションのプロモート メモリ ジェネレーション 2 にします。  
  
 3 番目のシナリオは、通知を受信するときの不確実性にも作用します。 これではありませんが、保証は、この期間中に、要求をリダイレクトするか、ガベージ コレクション自分で、都合の良いときに、不適切なフル ガベージ コレクションの影響を軽減するために便利な方法である証明は。  
  
## <a name="notification-threshold-parameters"></a>通知のしきい値のパラメーター  
 <xref:System.GC.RegisterForFullGCNotification%2A>メソッドが 2 つのパラメーターの第 2 世代のオブジェクトと、大きなオブジェクト ヒープのしきい値を指定します。 これらの値を満たしたときに、ガベージ コレクションの通知が発生する必要があります。 次の表では、これらのパラメーターについて説明します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`maxGenerationThreshold`|通知を発行するタイミングを指定する、1 ~ 99 の数値は、ジェネレーション 2 に昇格されたオブジェクトに基づいています。|  
|`largeObjectHeapThreshold`|通知を発行するタイミングを指定する、1 ~ 99 の数値は、大きなオブジェクト ヒープに割り当てられているオブジェクトに基づいています。|  
  
 大きすぎる値を指定する場合は、確率が高い、通知を受け取りますが、実行時にコレクションが発生する前に待機する長期間がある可能性があります。 強制的に実行するコレクション自分で、ランタイムでガベージ コレクションが解放は複数のオブジェクトを回収することがあります。  
  
 小さすぎる値を指定するに通知するための十分な時間をかけてする前に、ランタイムは、コレクションをおそれがあります。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、サーバーのグループは受信 Web 要求をサービスします。 バイト配列を追加する要求の処理のワークロードをシミュレートする、<xref:System.Collections.Generic.List%601>コレクション。 各サーバーのガベージ コレクションの通知を登録およびでスレッドを開始し、`WaitForFullGCProc`を継続的に監視するユーザーのメソッド、<xref:System.GCNotificationStatus>によって返される列挙型、<xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドです。  
  
 <xref:System.GC.WaitForFullGCApproach%2A>と<xref:System.GC.WaitForFullGCComplete%2A>メソッドは、通知が発生したときに、それぞれのイベント処理ユーザー メソッドを呼び出します。  
  
-   `OnFullGCApproachNotify`  
  
     このメソッドは、`RedirectRequests`サーバーへの要求をユーザーのメソッドは、要求キュー サーバの送信を中断するように指示します。 これは、クラス レベルの変数を設定してシミュレート`bAllocate`に`false`オブジェクトが割り当てられるようにします。  
  
     次に、`FinishExistingRequests`ユーザー メソッドが呼び出され、保留中のサーバー要求の処理を完了します。 これは、シミュレートをオフにして、<xref:System.Collections.Generic.List%601>コレクション。  
  
     最後に、ワークロードが薄いあるため、ガベージ コレクションが誘発されます。  
  
-   `OnFullGCCompleteNotify`  
  
     このメソッドは、ユーザー`AcceptRequests`サーバーは、フル ガベージ コレクションを受けやすくなりますが不要になったために、要求の受け入れを再開します。 設定してこの操作をシミュレートした、`bAllocate`変数を`true`に追加されているオブジェクトを再開できるように、<xref:System.Collections.Generic.List%601>コレクション。  
  
 次のコードが含まれています、`Main`例のメソッドです。  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 次のコードが含まれています、`WaitForFullGCProc`ガベージ コレクションの通知をチェックするループの中に継続的なを含む、ユーザー メソッドです。  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 次のコードが含まれています、`OnFullGCApproachNotify`メソッドから呼び出されると、  
  
 `WaitForFullGCProc` メソッド  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 次のコードが含まれています、`OnFullGCApproachComplete`メソッドから呼び出されると、  
  
 `WaitForFullGCProc` メソッド  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 次のコードにはから呼び出されるユーザー メソッドが含まれています、`OnFullGCApproachNotify`と`OnFullGCCompleteNotify`メソッドです。 ユーザー メソッドは、要求をリダイレクト、既存の要求を完了し、フル ガベージ コレクションが発生した後に要求を再開します。  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 完全なコード例は次のとおりです。  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)
