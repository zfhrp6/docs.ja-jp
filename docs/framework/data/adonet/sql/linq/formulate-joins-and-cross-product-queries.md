---
title: "Formulate Joins and Cross-Product Queries | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Formulate Joins and Cross-Product Queries
次の例は、複数のテーブルからの結果を組み合わせる方法を示しています。  
  
## 使用例  
 次の例は、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `From` 句 \(C\# の `from` 句\) で外部キー ナビゲーションを使用して、ロンドンの顧客の注文をすべて選択します。  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## 使用例  
 次の例は、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Where` 句 \(C\# の `where` 句\) で外部キー ナビゲーションを使用して、`Supplier` が米国にあり、在庫切れになっている `Products` をフィルター処理します。  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## 使用例  
 次の例は、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `From` 句 \(C\# の `from` 句\) で外部キー ナビゲーションを使用して、シアトルの従業員をフィルター処理し、その担当区域を表示します。  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## 使用例  
 次の例は、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) で外部キー ナビゲーションを使用して、上司と部下の関係にあり、同じ `City` 出身の 2 人の従業員の組み合わせをフィルター処理します。  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## 使用例  
 次の [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の例は、すべての顧客と注文を調べ、注文と顧客が一致すること、およびリスト内のすべての顧客に連絡先名が指定されていることを確認します。  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## 使用例  
 次の例は、2 つのテーブルを明示的に結合し、両方のテーブルからの結果を投影します。  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## 使用例  
 次の例は、3 つのテーブルを明示的に結合し、各テーブルからの結果を投影します。  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## 使用例  
 次の例は、`DefaultIfEmpty()` を使用して、`LEFT OUTER JOIN` を実現する方法を示しています。  `Employee` に `Order` がない場合は、`DefaultIfEmpty()` メソッドから null が返されます。  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## 使用例  
 次の例は、結合の結果の `let` 式を投影します。  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## 使用例  
 次の例は、複合キーを使用する `join` を示しています。  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## 使用例  
 次の例は、一方が null 許容で他方がそうでない `join` の作成方法を示しています。  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## 参照  
 [Query Examples](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)