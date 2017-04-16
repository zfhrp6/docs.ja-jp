---
title: "方法: ConcurrentDictionary の項目を追加および削除する | Microsoft Docs"
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
  - "スレッドセーフなコレクション、同時実行ディクショナリ"
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法: ConcurrentDictionary の項目を追加および削除する
この例では、<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> の項目を追加、取得、更新、および削除する方法を示します。  このコレクション クラスはスレッド セーフな実装です。  複数のスレッドが要素に同時にアクセスしようとする可能性がある場合は、このクラスを使用することをお勧めします。  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> には、コードでデータの追加または削除を試行する前に、まずキーが存在するかどうかをチェックする必要がなくなる便利なメソッドがいくつか用意されています。  これらの便利なメソッドとそのメソッドを使用する状況を次の表に示します。  
  
|方法|使用する状況|  
|--------|------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|指定したキーの新しい値を追加する。キーが既に存在する場合は、その値を置き換える。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|指定したキーの既存の値を取得する。キーが存在しない場合は、キーと値のペアを指定する。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|キーと値のペアを追加、取得、更新、または削除する。キーが既に存在する場合、または他の何らかの理由で試行が失敗した場合は、代わりの操作を実行する。|  
  
## 使用例  
 次の例では、2 つの <xref:System.Threading.Tasks.Task> インスタンスを使用していくつかの要素を <xref:System.Collections.Concurrent.ConcurrentDictionary%602> に同時に追加し、すべての内容を出力して要素が正常に追加されたことを示します。  この例では、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>とコレクションの項目を追加、更新したり、取得するために <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> のメソッドを使用する方法を示します。  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> は、マルチスレッドのシナリオ用に設計されています。  コレクションの項目を追加または削除するためにコードでロックを使用する必要はありません。  ただし、あるスレッドが値を取得し、別のスレッドが同じキーに新しい値を指定してコレクションをすぐに更新できます。  
  
 また、<xref:System.Collections.Concurrent.ConcurrentDictionary%602> のメソッドはすべてスレッド セーフですが、すべてのメソッドが分割不可能というわけではありません。具体的には、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> と <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> は分割できます。  それらのメソッドに渡されるユーザー デリゲートは、ディクショナリの内部ロックの外で呼び出されます \(不明なコードによってすべてのスレッドがブロックされるのを防止するためです\)。そのため、次の一連のイベントが発生する可能性があります。  
  
 1\) threadA が <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> を呼び出します。項目が見つからないため、valueFactory デリゲートを呼び出して、追加する新しい項目を作成します。  
  
 2\) 同時に threadB も <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> を呼び出します。valueFactory デリゲートが呼び出され、threadA よりも先に内部ロックに到達するため、新しいキーと値のペアがディクショナリに追加されます。  
  
 3\) threadA のユーザー デリゲートが完了し、スレッドがロックに到達しますが、この時点で既に項目は存在しています。  
  
 4\) threadA は "Get" を実行し、threadB で先に作成されたデータを返します。  
  
 したがって、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> から返されるデータが、スレッドの valueFactory によって作成されたデータと同じになるとは限りません。  <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> を呼び出す場合にも、これと同様の一連のイベントが発生する可能性があります。  
  
## 参照  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [スレッド セーフなコレクション](../../../../docs/standard/collections/thread-safe/index.md)