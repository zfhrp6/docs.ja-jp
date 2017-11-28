---
title: "方法: ConcurrentBag を使用してオブジェクト プールを作成する"
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
helpviewer_keywords: object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f7cb18157122d8bc053f34b21f623f3ab1e14305
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>方法: ConcurrentBag を使用してオブジェクト プールを作成する
この例では、ConcurrentBag を使用してオブジェクト プールを実装する方法を示します。 オブジェクト プールは、クラスの複数のインスタンスが必要であり、クラスの作成または破棄に大きなコストがかかる状況で、アプリケーションのパフォーマンスを向上させることができます。 クライアント プログラムが新しいオブジェクトを要求すると、オブジェクト プールは最初に既に作成されてプールに返されているオブジェクトを提供しようとします。 使用できるオブジェクトがない場合にのみ、新しいオブジェクトが作成されます。  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> は、高速の挿入と削除をサポートし、同じスレッドが項目の追加と削除の両方を行うときは特に高速であるため、オブジェクトの格納に使用されます。 この例は、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601> を中心に構築するようにさらに拡張できます。これは、<xref:System.Collections.Concurrent.ConcurrentQueue%601> や <xref:System.Collections.Concurrent.ConcurrentStack%601> と同じようにバッグ データの構造を実装します。  
  
## <a name="example"></a>例  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>関連項目  
 [スレッドセーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)
