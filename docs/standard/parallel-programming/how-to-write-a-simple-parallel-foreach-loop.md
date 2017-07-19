---
title: "How to: Write a Simple Parallel.ForEach Loop | Microsoft Docs"
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
  - "foreach, parallel version"
  - "parallel programming, foreach"
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# How to: Write a Simple Parallel.ForEach Loop
この例では、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> ループを使用して <xref:System.Collections.IEnumerable?displayProperty=fullName> データ ソースまたは <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> データ ソースを対象にデータを並列化する方法を示します。  
  
> [!NOTE]
>  ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。  C\# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A> ループは <xref:System.Threading.Tasks.Parallel.For%2A> ループと同様に動作します。  ソース コレクションがパーティション分割され、システム環境に基づいて複数のスレッドに処理がスケジュールされます。  システム上のプロセッサの数が多いほど、並列メソッドの実行速度は速くなります。  ソース コレクションの中には、ソースのサイズおよび実行される作業の種類によっては、順次ループが早くなるものがあります。  パフォーマンスの詳細については、「[Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)」を参照してください。  
  
 並列ループの詳細については、「[How to: Write a Simple Parallel.For Loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)」を参照してください。  
  
 非ジェネリック コレクションで <xref:System.Threading.Tasks.Parallel.ForEach%2A> を使用するには、次の例に示すように、<xref:System.Linq.Enumerable.Cast%2A> 拡張メソッドを使用してコレクションをジェネリック コレクションに変換します。  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Parallel LINQ \(PLINQ\) を使用して、<xref:System.Collections.Generic.IEnumerable%601> データ ソースの処理を並列化することもできます。  PLINQ により、宣言型のクエリ構文を使用してループの動作を表現できます。  詳細については、「[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。  
  
## コードのコンパイル  
  
-   このコードをコピーして [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 コンソール アプリケーション プロジェクトに貼り付けます。  
  
-   System.Drawing.dll への参照を追加します。  
  
-   F5 キーを押します。  
  
## 参照  
 [Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)