---
title: "方法: 単純な Parallel.ForEach ループを記述する"
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
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8cd3c3c01c2f9d83786e78f0eb1c45a38a49b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>方法: 単純な Parallel.ForEach ループを記述する
この例を使用する方法を示しています、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>を任意にデータの並列化を有効にするループ<xref:System.Collections.IEnumerable?displayProperty=nameWithType>または<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>データ ソース。  
  
> [!NOTE]
>  ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。 C# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL (PLINQ および TPL のラムダ式)](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 A<xref:System.Threading.Tasks.Parallel.ForEach%2A>ループの動作と同様に、<xref:System.Threading.Tasks.Parallel.For%2A>ループします。 ソース コレクションがパーティション分割し、システム環境に基づく複数のスレッドで作業をスケジュールします。 システムのより多くのプロセッサが速ければ速いほど、並列メソッドが実行されます。 一部のソース コレクションでは、順次ループが、ソース、および実行されている作業の種類のサイズによっては、高速な可能性があります。 パフォーマンスの詳細については、次を参照してください[データとタスクの並列化における注意点。](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 並列ループの詳細については、次を参照してください。[する方法: 単純な Parallel.For ループを記述](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)です。  
  
 使用する<xref:System.Threading.Tasks.Parallel.ForEach%2A>非ジェネリック コレクションを使用することができますを使用して、<xref:System.Linq.Enumerable.Cast%2A>次の例のように、ジェネリック コレクションにコレクションを変換する拡張メソッド。  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 処理を並列化する、Parallel LINQ (PLINQ) を使用することもできます。<xref:System.Collections.Generic.IEnumerable%601>データ ソース。 PLINQ では、宣言型のクエリ構文を使用してループを再現することができます。 詳細については、「[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   このコードをコピーして、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010年コンソール アプリケーション プロジェクト。  
  
-   System.Drawing.dll への参照を追加します。  
  
-   F5 キーを押して  
  
## <a name="see-also"></a>関連項目  
 [データの並列化](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [並列プログラミング](../../../docs/standard/parallel-programming/index.md)  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
