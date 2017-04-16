---
title: "方法: 境界ブロッキング機能をコレクションに追加する | Microsoft Docs"
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
  - "スレッドセーフなコレクション、カスタム ブロッキング コレクション"
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法: 境界ブロッキング機能をコレクションに追加する
この例では、境界ブロッキング機能をカスタム コレクション クラスに追加する方法を示します。この機能を追加するには、<xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> インターフェイスをそのクラスで実装し、クラス インスタンスを <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> の内部ストレージ機構として使用します。  境界ブロッキングの詳細については、「[BlockingCollection の概要](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)」を参照してください。  
  
## 使用例  
 カスタム コレクション クラスは、優先順位が <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> オブジェクトの配列として表される基本の優先順位キューです。  各キュー内で追加の順序付けは実行されません。  
  
 クライアント コードで、3 つのタスクが開始されます。  最初のタスクは、キーボード入力をポーリングして、実行時にいつでも取り消すことができるようにします。  2 番目のタスクは producer スレッドです。新しい項目をブロッキング コレクションに追加し、乱数値に基づいて各項目の優先順位を指定します。  3 番目のタスクは、使用できるようになった項目をコレクションから削除します。  
  
 いずれかのスレッドの実行速度を他のスレッドよりも速くすることで、アプリケーションの動作を調整できます。  プロデューサーの実行速度が速い場合は、コンストラクターで指定された項目数が既に含まれているとブロッキング コレクションで項目が追加されなくなるので、境界機能になります。  コンシューマーの実行速度が速い場合は、コンシューマーが新しい項目の追加を待機するので、ブロッキング機能になります。  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 既定では、<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> のストレージは <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName> になります。  
  
## 参照  
 [スレッド セーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)