---
title: "方法: パイプラインでブロッキング コレクションの配列を使用する | Microsoft Docs"
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
  - "スレッドセーフなコレクション、ブロッキング コレクション (パイプラインの)"
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法: パイプラインでブロッキング コレクションの配列を使用する
次の例は、<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> オブジェクトの配列を <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> や <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> などの静的メソッドと共に使用して、コンポーネント間の高速で柔軟性のあるデータ転送を実装する方法を示しています。  
  
## 使用例  
 次の例は、各オブジェクトが入力コレクションからデータを同時に取得して変換し、出力コレクションに渡す基本的なパイプラインの実装を示しています。  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## 参照  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [スレッド セーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)