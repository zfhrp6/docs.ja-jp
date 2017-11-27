---
title: "結合およびクロス積クエリの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 703823368f451839304ce02ff8b5f7259a44b935
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="formulate-joins-and-cross-product-queries"></a>結合およびクロス積クエリの作成
次の例は、複数のテーブルからの結果を組み合わせる方法を示しています。  
  
## <a name="example"></a>例  
 次の例で外部キー ナビゲーションを使用して、`From`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`from`句 (C#)) ロンドンの顧客のすべての注文を選択します。  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>例  
 外部キー ナビゲーションを使用する例を次、`Where`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`where`句 (C#)) を在庫切れのフィルター処理する`Products`が`Supplier`米国の州がします。  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>例  
 次の例は、`From` の [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 句 (C# の `from` 句) で外部キー ナビゲーションを使用して、シアトルの従業員をフィルター処理し、その担当区域を表示します。  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>例  
 次の例で外部キー ナビゲーションを使用して、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) を 1 人の従業員が、他のレポート、および、両方の従業員は同じ従業員の組み合わせをフィルター処理する`City`です。  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>例  
 次[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]例は、すべての顧客と注文を検索、顧客、注文が一致することを確認し、そのリスト内のすべての顧客の連絡先の名前が指定されていることを保証します。  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>例  
 次の例は、2 つのテーブルを明示的に結合し、両方のテーブルからの結果を投影します。  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>例  
 次の例は、3 つのテーブルを明示的に結合し、各テーブルからの結果を投影します。  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>例  
 次の例は、`LEFT OUTER JOIN` を使用して、`DefaultIfEmpty()` を実現する方法を示しています。 `DefaultIfEmpty()` に `Order` がない場合は、`Employee` メソッドから null が返されます。  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>例  
 次の例は、結合の結果の `let` 式を投影します。  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>例  
 次の例は、複合キーを使用する `join` を示しています。  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>例  
 次の例は、一方が null 許容で他方がそうでない `join` の作成方法を示しています。  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>関連項目  
 [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
