---
title: "スレッド セーフなコレクションを使用する状況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0bfb5ef2679c4e20e99a10dcf82a251673811b41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-a-thread-safe-collection"></a>スレッド セーフなコレクションを使用する状況
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] は、マルチ スレッドの追加および削除の操作をサポートするために特別に設計されている、5 つの新しいコレクション型です。 スレッド セーフを確保するために、これらの新しい型では、さまざまな種類の効率的なロック同期機構とロック制御の不要な同期機構が使用されます。 同期を行うと、操作にオーバーヘッドが追加されます。 オーバーヘッドの量は、使用する同期の種類、実行する操作の種類、およびその他の要因 (コレクションに同時にアクセスしようとするスレッドの数など) によって異なります。  
  
 一部のシナリオでは、同期のオーバーヘッドがほとんどなく、外部ロックで保護されるスレッド セーフでない同等の型よりもマルチスレッド型の方が、パフォーマンスとスケーラビリティが大幅に向上することがあります。 その他のシナリオでは、オーバーヘッドが原因で、スレッド セーフな型のパフォーマンスとスケーラビリティが、外部からロックされるスレッド セーフでないバージョンの型と同等かそれ以下になることもあります。  
  
 以下のセクションでは、スレッド セーフなコレクションと、読み取り操作および書き込み操作でユーザー指定のロックを使用するスレッド セーフでない同等のコレクションの使い分けに関する一般的なガイダンスを示します。 パフォーマンスはさまざまな要因に左右されるため、このガイダンスは特定の状況には沿っておらず、すべての状況で有効であるとは限りません。 パフォーマンスが重要な場合、使用するコレクション型を判断する最適な方法は、代表的なコンピューター構成および負荷に基づいてパフォーマンスを計測することです。 このドキュメントでは、次の用語が使用されています。  
  
 *純粋プロデューサー/コンシューマー シナリオ*  
 任意のスレッドで、要素の追加または削除のいずれかが実行されますが、両方は実行されません。  
  
 *混合プロデューサー/コンシューマー シナリオ*  
 任意のスレッドで、要素の追加および削除の両方が実行されます。  
  
 *高速化*  
 同じシナリオで別の型と比較してアルゴリズムのパフォーマンスが向上することです。  
  
 *スケーラビリティ*  
 コンピューターのコア数に比例したパフォーマンスの向上。 スケーリングするアルゴリズムのパフォーマンスは、コア数が 2 の場合よりも 8 の場合の方が向上します。  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) 対 Queue(T)  
 純粋プロデューサー/コンシューマー シナリオで、各要素の処理時間がとても短い (命令が少ない) 場合には、外部ロックを使用する <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> よりも <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> の方が若干優れたパフォーマンスを得られます。 このシナリオでは、キューへの配置とキューからの取り出しをそれぞれ専用のスレッドが実行している場合に、<xref:System.Collections.Concurrent.ConcurrentQueue%601> のパフォーマンスが最大限に引き出されます。 この規則を強制していない場合、<xref:System.Collections.Generic.Queue%601> は、複数のコアを持つコンピューター上の <xref:System.Collections.Concurrent.ConcurrentQueue%601> よりも若干向上する場合があります。  
  
 処理時間が 500 FLOPS (浮動小数点演算) 以上の場合、2 つのスレッドを使用する規則は <xref:System.Collections.Concurrent.ConcurrentQueue%601> に適用されません。この型でとても優れたスケーラビリティが実現します。 <xref:System.Collections.Generic.Queue%601> は、このシナリオではスケーラビリティの点で劣ります。  
  
 混合プロデューサー/コンシューマー シナリオでは、処理時間がとても短い場合、外部ロックを使用する <xref:System.Collections.Generic.Queue%601> のスケーラビリティは <xref:System.Collections.Concurrent.ConcurrentQueue%601> よりも優れています。 ただし、処理時間が約 500 FLOPS 以上の場合、<xref:System.Collections.Concurrent.ConcurrentQueue%601> の方がスケーラビリティに優れます。  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack 対 Stack  
 純粋プロデューサー/コンシューマー シナリオで処理時間が非常に短い場合には、プッシュとポップをそれぞれ専用のスレッドで実行しているのであれば、<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> と外部ロックを使用する <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> のパフォーマンスはほぼ同じになると考えられます。 ただし、スレッド数が増えると、競合が増えることで両方の型のパフォーマンスが低下し、<xref:System.Collections.Generic.Stack%601> の方が <xref:System.Collections.Concurrent.ConcurrentStack%601> よりも優れたパフォーマンスを示すことがあります。 処理時間が約 500 FLOPS 以上の場合は、両方の型がほぼ同じスケーラビリティを示します。  
  
 混合プロデューサー/コンシューマー シナリオでは、ワークロードの大小にかかわらず、<xref:System.Collections.Concurrent.ConcurrentStack%601> の方が高速です。  
  
 <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> と <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> を使用すると、アクセス時間が大幅に短縮される可能性があります。  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary 対 Dictionary  
 一般に、複数のスレッドから同時にキーまたは値を追加および更新するシナリオであれば、<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> を使用します。 更新を頻繁に行い、読み取りは比較的少ないシナリオでは、通常、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> には大きな利点はありません。 読み取りも更新も多いシナリオでは、通常、コンピューターに任意の数のコアを備えられる場合は <xref:System.Collections.Concurrent.ConcurrentDictionary%602> の方が大幅に高速です。  
  
 更新を頻繁に行うシナリオでは、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> で同時実行の程度を上げて、コンピューターのコア数が多いほどパフォーマンスが向上するかどうかを計測できます。 同時実行レベルを変更する場合、グローバル操作はできるだけ避けてください。  
  
 キーまたは値の読み取りのみを行う場合、ディクショナリがスレッドによって変更されないのであれば同期は不要なため、<xref:System.Collections.Generic.Dictionary%602> の方が高速です。  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 純粋プロデューサー/コンシューマー シナリオでは、<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> は、その他の同時実行コレクション型よりもパフォーマンスの点で劣ると考えられます。  
  
 混合プロデューサー/コンシューマー シナリオでは、通常、ワークロードの大小にかかわらず、<xref:System.Collections.Concurrent.ConcurrentBag%601> は他の同時実行コレクション型よりもはるかに高速でスケーラビリティに優れます。  
  
## <a name="blockingcollection"></a>BlockingCollection  
 境界ブロッキング セマンティクスが必要な場合は、<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> の方がカスタム実装よりもパフォーマンスの点で優れると考えられます。 この型では、高度なキャンセル、列挙、および例外処理もサポートされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [スレッドセーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)  
 [並列プログラミング](../../../../docs/standard/parallel-programming/index.md)
