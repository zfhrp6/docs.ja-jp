---
title: "方法: 境界ブロッキング機能をコレクションに追加する | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: df159b1ab3f7c16564ce493a585246c4c461a8f9
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>方法: 境界ブロッキング機能をコレクションに追加する
この例では、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> インターフェイスをクラスに実装し、クラス インスタンスを <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> の内部記憶域メカニズムとして使用することで、制限機能およびブロック機能をカスタム コレクション クラスに追加する方法を示しています。 境界ブロッキングの詳細については、「[BlockingCollection の概要](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)」を参照してください。  
  
## <a name="example"></a>例  
 カスタム コレクション クラスは基本的な優先度のキューであり、優先度は <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> オブジェクトの配列として表されます。 各キュー内で他の順序付けは行われません。  
  
 クライアント コードでは、3 つのタスクが開始されます。 1 番目のタスクはキーボード入力のポーリングだけを行い、実行中にいつでもキャンセルできるようにします。 2 番目のタスクはプロデューサー スレッドであり、ブロッキング コレクションに新しい項目を追加し、ランダムな値に基づく優先度を各項目に割り当てます。 3 番目のタスクは、利用可能になった項目をコレクションから削除します。  
  
 1 つのスレッドが他より速く実行されるようにすることで、アプリケーションの動作を調整できます。 プロデューサーが高速に実行されると、コンストラクターで指定されている数の項目がコレクションに既に含まれる場合はブロッキング コレクションが項目の追加を防ぐので、境界機能が目立つようになります。 コンシューマーが高速に実行されると、コンシューマーは新しい項目が追加されるのを待機するので、ブロッキング機能が目立つようになります。  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 既定で、<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> の記憶域は <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> です。  
  
## <a name="see-also"></a>関連項目  
 [スレッドセーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)
