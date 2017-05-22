---
title: "ガベージ コレクション | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
caps.latest.revision: 36
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 11ea4186a77a600d1645fe334ba9fd704fe728b4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="garbage-collection"></a>ガベージ コレクション
.NET のガベージ コレクターは、アプリケーションのメモリの割り当てと解放を管理します。 新しいオブジェクトを生成するたびに、共通言語ランタイムは、マネージ ヒープからオブジェクトにメモリを割り当てます。 マネージ ヒープに使用可能なアドレス空間がある限り、ランタイムは新しいオブジェクト用に領域の割り当てを続けます。 しかし、メモリの大きさは無限ではありません。 最終的には、ガベージ コレクターが、一部のメモリを解放するためにガベージ コレクションを実行する必要があります。 コレクションの実行に最適な時期は、ガベージ コレクターの最適化エンジンが、割り当てられるオブジェクトの状況に応じて決定します。 コレクションを実行する場合、ガベージ コレクターは、アプリケーションによって使用されなくなったオブジェクトがマネージ ヒープにあるかどうかをチェックし、使われていないオブジェクトのメモリを再利用するために必要な操作を実行します。  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[ガベージ コレクションの基礎](../../../docs/standard/garbage-collection/fundamentals.md)|ガベージ コレクションの動作、マネージ ヒープに対するオブジェクトの割り当て方法、およびその他の主要な概念について説明します。|  
|[ガベージ コレクションとパフォーマンス](../../../docs/standard/garbage-collection/performance.md)|ガベージ コレクションとパフォーマンスの問題を診断するために使用できるパフォーマンス チェックについて説明します。|  
|[発生したコレクション](../../../docs/standard/garbage-collection/induced.md)|ガベージ コレクションがどのように行われるかについて説明します。|  
|[待機モード](../../../docs/standard/garbage-collection/latency.md)|ガベージ コレクションの割り込みの動作を決定するモードについて説明します。|  
|[共有 Web ホストの最適化](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|複数の小規模な Web サイトで共有されているサーバーで、ガベージ コレクションを最適化する方法について説明します。|  
|[ガベージ コレクションの通知](../../../docs/standard/garbage-collection/notifications.md)|フル ガベージ コレクションが近づいたときと完了したときを検出する方法について説明します。|  
|[アプリケーション ドメインのリソース監視](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|アプリケーション ドメインによる CPU とメモリの使用状況を監視する方法について説明します。|  
|[弱い参照](../../../docs/standard/garbage-collection/weak-references.md)|アプリケーションからオブジェクトへのアクセスを許容したまま、そのオブジェクトをガベージ コレクターが収集できるようにする機能について説明します。|  
  
## <a name="reference"></a>参照  
 <xref:System.GC?displayProperty=fullName>  
  
 <xref:System.GCCollectionMode?displayProperty=fullName>  
  
 <xref:System.GCNotificationStatus?displayProperty=fullName>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings?displayProperty=fullName>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName>  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName>  
  
 <xref:System.IDisposable?displayProperty=fullName>  
  
## <a name="see-also"></a>関連項目  
 [アンマネージ リソースのクリーンアップ](../../../docs/standard/garbage-collection/unmanaged.md)
