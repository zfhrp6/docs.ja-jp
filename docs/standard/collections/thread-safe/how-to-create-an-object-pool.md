---
title: "方法: ConcurrentBag を使用してオブジェクト プールを作成する | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 5
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bfe61501586deed112d6a94bf90fd83e84f2639f
ms.lasthandoff: 04/18/2017

---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a>方法: ConcurrentBag を使用してオブジェクト プールを作成する
この例では、ConcurrentBag を使用してオブジェクト プールを実装する方法を示します。 オブジェクト プールは、クラスの複数のインスタンスが必要であり、クラスの作成または破棄に大きなコストがかかる状況で、アプリケーションのパフォーマンスを向上させることができます。 クライアント プログラムが新しいオブジェクトを要求すると、オブジェクト プールは最初に既に作成されてプールに返されているオブジェクトを提供しようとします。 使用できるオブジェクトがない場合にのみ、新しいオブジェクトが作成されます。  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> は、高速の挿入と削除をサポートし、同じスレッドが項目の追加と削除の両方を行うときは特に高速であるため、オブジェクトの格納に使用されます。 この例は、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601> を中心に構築してさらに拡張できます。これは、<xref:System.Collections.Concurrent.ConcurrentQueue%601> や <xref:System.Collections.Concurrent.ConcurrentStack%601> と同じようにバッグ データの構造を実装します。  
  
## <a name="example"></a>例  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a>関連項目  
 [スレッドセーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)
