---
title: "スレッド セーフなコレクションを使用する状況 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
caps.latest.revision: 9
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 87898a4a6ba3d3ef4c53fd1c6b8f94ff353f10e4
ms.lasthandoff: 04/18/2017

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
 純粋プロデューサー/コンシューマー シナリオでは、各要素の処理時間がとても短い (命令が少ない) 場合、<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> は、外部ロックを使用する <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> よりも若干優れたパフォーマンスを提供します。 このシナリオでは、キューへの配置とキューからの取り出しをそれぞれ専用のスレッドが実行している場合に、<xref:System.Collections.Concurrent.ConcurrentQueue%601> のパフォーマンスが最大限に引き出されます。 この規則を適用しない場合でも、<xref:System.Collections.Generic.Queue%601> は複数コアを含むコンピューターの <xref:System.Collections.Concurrent.ConcurrentQueue%601> よりもわずかに優れたパフォーマンスを提供します。  
  
 処理時間が 500 FLOPS (浮動小数点演算) 以上の場合、2 つのスレッドを使用する規則は <xref:System.Collections.Concurrent.ConcurrentQueue%601> に適用されません。この型でとても優れたスケーラビリティが実現します。 <xref:System.Collections.Generic.Queue%601> は、このシナリオではスケーラビリティの点で劣ります。  
  
 混合プロデューサー/コンシューマー シナリオでは、処理時間がとても短い場合、外部ロックを使用する <xref:System.Collections.Generic.Queue%601> の方が <xref:System.Collections.Concurrent.ConcurrentQueue%601> よりもスケーラビリティに優れています。 ただし、処理時間が約 500 FLOPS 以上の場合、<xref:System.Collections.Concurrent.ConcurrentQueue%601> の方がスケーラビリティに優れています。  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack 対 Stack  
 純粋プロデューサー/コンシューマー シナリオでは、処理時間が非常に短い場合、プッシュとポップをそれぞれ専用のスレッドが実行しているときは、<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName> および外部ロックを使用する <xref:System.Collections.Generic.Stack%601?displayProperty=fullName> のパフォーマンスはほぼ同じであると考えられます。 ただし、スレッドが増えるほど競合の数が増えるため、両方の型で速度が落ちていき、<xref:System.Collections.Concurrent.ConcurrentStack%601> よりも <xref:System.Collections.Generic.Stack%601> の方がパフォーマンスが良くなります。 処理時間が約 500 FLOPS 以上の場合は、両方の型がほぼ同じスケーラビリティを示します。  
  
 混合プロデューサー/コンシューマー シナリオでは、ワークロードの大小にかかわらず、<xref:System.Collections.Concurrent.ConcurrentStack%601> の方が高速です。  
  
 <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> および <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> を使用することで、アクセス時間が大幅に短縮する場合があります。  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary 対 Dictionary  
 一般に、複数のスレッドから同時にキーまたは値を追加および更新しているシナリオでは、<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> を使用します。 更新を頻繁に行い、読み取りは比較的少ないシナリオでは、通常、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> には大きな利点はありません。 読み取りも更新も多いシナリオでは、通常、コンピューターに任意の数のコアを備えられる場合は <xref:System.Collections.Concurrent.ConcurrentDictionary%602> の方が大幅に高速です。  
  
 更新を頻繁に行うシナリオでは、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> で同時実行の程度を上げて、コンピューターのコア数が多いほどパフォーマンスが向上するかどうかを計測できます。 同時実行レベルを変更する場合、グローバル操作はできるだけ避けてください。  
  
 キーまたは値の読み取りのみを行う場合、ディクショナリがスレッドによって変更されないときは同期が不要なため、<xref:System.Collections.Generic.Dictionary%602> の方が高速です。  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 純粋プロデューサー/コンシューマー シナリオでは、<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName> は、その他の同時実行コレクション型よりもパフォーマンスの点で劣ると考えられます。  
  
 混合プロデューサー/コンシューマー シナリオでは、通常、ワークロードの大小にかかわらず、<xref:System.Collections.Concurrent.ConcurrentBag%601> は他の同時実行コレクション型よりもはるかに高速でスケーラブルです。  
  
## <a name="blockingcollection"></a>BlockingCollection  
 境界ブロッキング セマンティクスが必要な場合は、<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> の方がカスタム実装よりもパフォーマンスの点で優れると考えられます。 この型では、高度なキャンセル、列挙、および例外処理もサポートされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [スレッド セーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)   
 [並列プログラミング](../../../../docs/standard/parallel-programming/index.md)
