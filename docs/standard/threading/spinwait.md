---
title: SpinWait
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
helpviewer_keywords: synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfaf85c0fe1de3be89618ae540e9c183b66a11eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>高価なコンテキストの切り替えとカーネル イベントに必要なカーネル遷移を避けるために低レベルのシナリオで使用できる軽量な同期型です。 マルチコア コンピューターは、長期間保持するリソースが予期されていない場合があります数十または数百サイクル、ユーザー モードで起動し、リソースの取得を再試行を待機中のスレッドの効率。 回転の後に、リソースが利用可能な場合は、数千サイクルを保存しました。 リソースがまだ使用できない場合は、いくつかのサイクルのみを費やしし、カーネル ベースの待機を入力できます。 この待機時間、回転の組み合わせとも呼ば、 *2 フェーズ待機操作*です。  
  
 <xref:System.Threading.SpinWait>などのカーネル イベントをラップする .NET Framework の型と組み合わせて使用するように設計された<xref:System.Threading.ManualResetEvent>です。 <xref:System.Threading.SpinWait>1 つだけのプログラムの基本的な回転機能を単独でも使用できます。  
  
 <xref:System.Threading.SpinWait>空のループだけがします。 動作を提供する適切なスピン一般的なケースでは、慎重に実装されているし、コンテキスト スイッチが開始場合は、回転する十分な時間 (ほぼカーネル遷移に必要な時間の長さ)。 たとえば、コンピューターでは単一コア、<xref:System.Threading.SpinWait>スレッドのタイム スライスの生成スピン ブロックのすべてのスレッドでの進行状況を転送するためにすぐにします。 <xref:System.Threading.SpinWait>またを待機中のスレッドが優先順位の高いスレッドや、ガベージ コレクターをブロックするを防ぐために、マルチコア コンピューター上であっても生成します。 そのためを使用している場合、 <xref:System.Threading.SpinWait> 2 フェーズ待機操作では、ことをお勧めする前に、カーネル待機が起動される、<xref:System.Threading.SpinWait>コンテキスト スイッチをそれ自体を開始します。 <xref:System.Threading.SpinWait>提供、<xref:System.Threading.SpinWait.NextSpinWillYield%2A>プロパティで、すべての呼び出しにする前に確認できる<xref:System.Threading.SpinWait.SpinOnce%2A>です。 プロパティが返されるときに`true`、独自の待機操作を開始します。 例については、次を参照してください。[する方法: 2 フェーズ待機操作を実装する使用 SpinWait](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)です。  
  
 有効にできますが、2 フェーズ待機操作を実行していないいくつかの条件が true になるまでだけ回転している場合は、<xref:System.Threading.SpinWait>をそのコンテキストを実行する Windows オペレーティング システムの環境での良き市民ようにを切り替えます。 基本的な例を次に、<xref:System.Threading.SpinWait>ロック制御不要のスタックにします。 高パフォーマンス、スレッド セーフであるスタックを必要とする場合は、使用を検討して<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>です。  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
