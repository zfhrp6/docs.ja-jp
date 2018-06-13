---
title: '方法 : クエリで複合キーを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 26c281445b84d3b3f85980de6ae4076411bb4fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354240"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>方法 : クエリで複合キーを処理する
演算子によっては、引数を 1 つしか受け取らないものがあります。 1 つの演算子にデータベースの複数の列を含めるには、その組み合わせを表す匿名型を作成する必要があります。  
  
## <a name="example"></a>例  
 `GroupBy` 演算子を使用するクエリを次の例に示します。この演算子は、1 つの `key` 引数だけを受け取ることができます。  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>例  
 次の例に示すように、結合の場合も同様です。  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
