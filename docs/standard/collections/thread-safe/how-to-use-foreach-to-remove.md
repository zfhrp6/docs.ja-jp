---
title: "方法: ForEach を使用して BlockingCollection 内の項目を削除する | Microsoft Docs"
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
  - "スレッドセーフなコレクション、方法 (ブロッキング コレクションを列挙する)"
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法: ForEach を使用して BlockingCollection 内の項目を削除する
<xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> メソッドおよび <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> メソッドを使用して <xref:System.Collections.Concurrent.BlockingCollection%601> からアイテムを取得するだけでなく、[foreach](../Topic/foreach,%20in%20\(C%23%20Reference\).md) \(Visual Basic では [For Each](../Topic/For%20Each...Next%20Statement%20\(Visual%20Basic\).md)\) を使用して、追加が完了してコレクションが空になるまで、アイテムを削除することもできます。  これは、*列挙の変更*または*列挙の消費*と呼ばれます。この列挙子は、通常の `foreach` \(`For Each`\) ループとは異なり、アイテムを削除することでソース コレクションを変更するためです。  
  
## 使用例  
 `foreach` \(`For Each`\) ループを使用して <xref:System.Collections.Concurrent.BlockingCollection%601> 内のすべてのアイテムを削除する方法を次の例に示します。  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 この例では、consumer スレッドの <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=fullName> メソッドで `foreach` ループを使用します。これにより、各アイテムは、列挙されるときにコレクションから削除されます。  <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName> では常に、コレクションに含まれるアイテムの最大数が制限されます。  この方法でコレクションを列挙すると、使用できるアイテムがない場合、またはコレクションが空の場合に、consumer スレッドがブロックされます。  この例では、producer スレッドによるアイテムの追加が、アイテムの使用よりも迅速に行われるため、ブロックは問題にはなりません。  
  
 producer スレッドによって追加されたときの順序と同じ順序でアイテムが列挙されるという保証はありません。  
  
 コレクションを変更せずに列挙するには、<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> メソッドを使用せずに `foreach` \(`For Each`\) を使用します。  ただし、この種の列挙が表しているのは、ある特定の時点のコレクションのスナップショットであることを理解する必要があります。  ループの実行中に他のスレッドがアイテムを同時に追加または削除した場合は、ループがコレクションの実際の状態を表していないことがあります。  
  
## 参照  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 [Parallel Programming](../../../../docs/standard/parallel-programming/index.md)