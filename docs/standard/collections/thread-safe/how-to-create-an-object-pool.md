---
title: "方法: ConcurrentBag を使用してオブジェクト プールを作成する | Microsoft Docs"
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
  - "オブジェクト プール、.NET Framework での"
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: ConcurrentBag を使用してオブジェクト プールを作成する
この例では、同時実行バッグを使用してオブジェクト プールを実装する方法を示します。  オブジェクト プールを実装すると、クラスの複数のインスタンスが必要で、クラスの作成時または破棄時の負荷が高い場合に、アプリケーションのパフォーマンスを向上できます。  クライアント プログラムによって新しいオブジェクトが要求されると、オブジェクト プールはまず、既に作成されてプールに返されているオブジェクトを提供しようとします。  オブジェクトが存在しない場合にのみ、新しいオブジェクトが作成されます。  
  
 <xref:System.Collections.Concurrent.ConcurrentBag%601> は高速な挿入と削除をサポートするので、オブジェクトの格納に使用されます。特に、同じスレッドが項目の追加と削除の両方を行っている場合に役立ちます。  この例は、<xref:System.Collections.Concurrent.ConcurrentQueue%601> および <xref:System.Collections.Concurrent.ConcurrentStack%601> と同様に、バッグ データ構造によって実装される <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> を中心に構築してさらに強化することができます。  
  
## 使用例  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## 参照  
 [スレッド セーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)