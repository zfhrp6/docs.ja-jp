---
title: '方法: 単純な Parallel.ForEach ループを記述する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e3fb5fd807971aed014ba98cbb207c4483b93f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581681"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>方法: 単純な Parallel.ForEach ループを記述する
この例は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ループを使用して、<xref:System.Collections.IEnumerable?displayProperty=nameWithType> または <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> データ ソースでのデータの並列処理を有効にする方法を示しています。  
  
> [!NOTE]
>  ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。 C# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL (PLINQ および TPL のラムダ式)](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 <xref:System.Threading.Tasks.Parallel.ForEach%2A> ループは <xref:System.Threading.Tasks.Parallel.For%2A> ループのように動作します。 ソース コレクションはパーティション分割され、作業はシステム環境に基づいて複数のスレッドでスケジューリングされます。 システムのプロセッサの数が多いほど、並列メソッドの実行が速くなります。 一部のソース コレクションでは、ソースのサイズや実行される作業の種類に応じて、順次ループがより高速になる可能性があります。 パフォーマンスの詳細については、「[データとタスクの並列化における注意点](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)」を参照してください。  
  
 並列ループの詳細については、「[方法: 単純な Parallel.For ループを記述する](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)」を参照してください。  
  
 非ジェネリック コレクションで <xref:System.Threading.Tasks.Parallel.ForEach%2A> を使用する場合は、次の例に示すように、<xref:System.Linq.Enumerable.Cast%2A> 拡張メソッドを使用して、コレクションをジェネリック コレクションに変換することができます。  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 また、Parallel LINQ (PLINQ) を使用して、<xref:System.Collections.Generic.IEnumerable%601> データ ソースの処理を並列化することもできます。 PLINQ では、宣言型のクエリ構文を使用して、ループの動作を表すことができます。 詳細については、「[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   このコードをコピーして、Visual Studio 2010 コンソール アプリケーション プロジェクトに貼り付けます。  
  
-   System.Drawing.dll への参照を追加します。  
  
-   F5 キーを押します。  
  
## <a name="see-also"></a>参照  
 [データの並列化](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [並列プログラミング](../../../docs/standard/parallel-programming/index.md)  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
