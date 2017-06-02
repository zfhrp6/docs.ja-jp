---
title: "Formulate Projections | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Formulate Projections
以下の例は、C\# の `select` ステートメントおよび [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` ステートメントを他の機能と組み合わせて、クエリの射影を作成する方法を示しています。  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) を使用して、`Customers` の連絡先の名前のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) および*匿名型*を使用して、`Customers` の連絡先の名前と電話番号のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) および*匿名型*を使用して、従業員の名前と電話番号のシーケンスを返します。  結果のシーケンスでは、`FirstName` フィールドと `LastName` フィールドは 1 つのフィールド \(`Name`\) に結合され、`HomePhone` フィールドは `Phone` という名前に変更されます。  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) および*匿名型*を使用して、すべての `ProductID`、および `HalfPrice` という名前の計算値のシーケンスを返します。  この値は、`UnitPrice` を 2 で割った値に設定されます。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) および*条件付きステートメント*を使用して、製品名と製品の購入可能性のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) および*既知の型* \(Name\) を使用して、従業員の名前のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` と `Where` \(C\# の `select` と `where`\) を使用して、London の顧客の連絡先の名前の、*フィルター処理されたシーケンス*を返します。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## 使用例  
 次の例では、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の `Select` 句 \(C\# の `select` 句\) および*匿名型*を使用して、顧客に関するデータの*成型されたサブセット*を返します。  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## 使用例  
 次の例では、入れ子になったクエリを使用して以下の結果を返します。  
  
-   すべての注文および対応する `OrderID` のシーケンス。  
  
-   注文内で割引のある項目から成るサブシーケンス。  
  
-   出荷コストが含まれない場合に節約される費用。  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## 参照  
 [Query Examples](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)