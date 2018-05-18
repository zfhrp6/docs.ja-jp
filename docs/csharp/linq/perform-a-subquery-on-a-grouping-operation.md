---
title: グループ化操作でのサブクエリの実行
description: グループ化操作でサブクエリを実行する方法。
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>グループ化操作でのサブクエリの実行

このトピックでは、ソース データを複数のグループに整理し、各グループに対して個別にサブクエリを実行するクエリを作成する方法を 2 つ紹介します。 各例の基本的な手法として、ソース要素のグループ化には、`newGroup` という名前の "*継続*" を使用し、`newGroup` に対する新しいサブクエリを生成します。 このサブクエリは、外部クエリによって作成された新しい各グループに対して実行されます。 この例では、最終出力がグループではなく、匿名型のフラットなシーケンスであることに注意してください。  
  
 グループ化する方法の詳細については、「[group 句](../language-reference/keywords/group-clause.md)」を参照してください。  
  
 継続の詳細については、「[into](../language-reference/keywords/into.md)」を参照してください。 次の例では、インメモリ データ構造をデータ ソースとして使用していますが、どの種類の LINQ データ ソースにも同じ原則が当てはまります。  
  
## <a name="example"></a>例 

 > [!NOTE]
 > この例には、「[オブジェクトのコレクションの照会](query-a-collection-of-objects.md)」のサンプル コードで定義されているオブジェクトへの参照が含まれています。

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)
