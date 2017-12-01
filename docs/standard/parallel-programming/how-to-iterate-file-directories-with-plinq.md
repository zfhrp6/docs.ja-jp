---
title: "方法: PLINQ を使用してファイル ディレクトリを反復処理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>方法: PLINQ を使用してファイル ディレクトリを反復処理する
この例では、ファイルのディレクトリでの操作を並列化する 2 つの簡単な方法を示します。 最初のクエリを使用して、<xref:System.IO.Directory.GetFiles%2A>ディレクトリとすべてのサブディレクトリ内のファイル名の配列に挿入する方法です。 このメソッドは、配列全体を設定すると、され、そのため、操作の開始時の待機時間が生じることになるまでには返されません。 ただし、配列を作成すると、後に PLINQ ことができます、並列処理非常に短時間です。  
  
 2 番目のクエリは、静的な<xref:System.IO.Directory.EnumerateDirectories%2A>と<xref:System.IO.DirectoryInfo.EnumerateFiles%2A>すぐに結果を返すを開始するメソッド。 このアプローチは短縮されます大規模なディレクトリ ツリーを繰り返し処理するときと比較する最初の例と処理時間が、さまざまな要因に依存できます。  
  
> [!WARNING]
>  これらの例は、使用法を説明するものでし、可能性がありますいないほど高速で、同等の連続した LINQ to Objects クエリ。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。  
  
## <a name="example"></a>例  
 次の例と、ツリー内のすべてのディレクトリへのアクセスがある、ファイルのサイズが非常に大きなアクセス時間が重要ではありませんは、単純なシナリオでのファイル ディレクトリを反復処理する方法を示します。 この方法には、ファイル名の配列が構築されるときに、先頭の待機時間の期間が含まれます。  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>例  
 次の例と、ツリー内のすべてのディレクトリへのアクセスがある、ファイルのサイズが非常に大きなアクセス時間が重要ではありませんは、単純なシナリオでのファイル ディレクトリを反復処理する方法を示します。 この方法は、前の例よりも高速に結果を生成を開始します。  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 使用する場合<xref:System.IO.Directory.GetFiles%2A>ツリー内のすべてのディレクトリに十分なアクセス許可があることを確認します。 それ以外の場合、例外がスローし、結果は返されません。 使用する場合、 <xref:System.IO.Directory.EnumerateDirectories%2A> PLINQ クエリでは例外を処理する I/O の反復処理を続行することができます、正常な方法で問題が発生します。 かどうかは、コードは、I/O または不正アクセス例外を処理する必要がありますで説明されているアプローチを検討する必要があります[する方法: Parallel クラスの使用してファイル ディレクトリを反復処理する](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)です。  
  
 I/O 待機時間が問題の場合は、たとえば、ネットワーク経由でのファイル I/O の使用を検討してで説明されている非同期 I/O の手法のいずれかの[TPL と従来の .NET Framework 非同期プログラミング](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)とこの[ブログの投稿](http://go.microsoft.com/fwlink/?LinkID=186458).  
  
## <a name="see-also"></a>関連項目  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
