---
title: "射影の作成"
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
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8afd48c6ce7c6313e82a7b74c2271f52833d1f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="formulate-projections"></a>射影の作成
以下の例は、C# の `select` ステートメントおよび `Select` の [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ステートメントを他の機能と組み合わせて、クエリの射影を作成する方法を示しています。  
  
## <a name="example"></a>例  
 次の例で、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) を連絡先の名前のシーケンスを返す`Customers`です。  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>例  
 次の例では、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*連絡先の名前のシーケンスを返すし、電話の番号を`Customers`です。  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>例  
 次の例では、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*名前のシーケンスを返すし、従業員の電話番号にします。 `FirstName`と`LastName`フィールドが 1 つのフィールドに結合されます (`Name`)、および`HomePhone`フィールドの名前を変更する`Phone`結果のシーケンス。  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>例  
 次の例では、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*すべてのシーケンスを返します`ProductID`s とという名前の計算値`HalfPrice`です。 この値は、`UnitPrice` を 2 で割った値に設定されます。  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>例  
 次の例で、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select` (C#) 句) および*条件付きステートメント*製品名および製品の可用性のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>例  
 次の例では、 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `Select`句 (`select` (C#) 句) および*既知の型*従業員の名前のシーケンスを返します (名前)。  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>例  
 次の例で`Select`と`Where`で[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`と`where`C# の場合) を返す、*フィルター処理されたシーケンス*ロンドンの顧客の連絡先の名前のです。  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>例  
 次の例で、`Select`句[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)](`select`句 (C#)) と*匿名型*を返す、*成型されたサブセット*の顧客に関するデータ。  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>例  
 次の例では、入れ子になったクエリを使用して以下の結果を返します。  
  
-   すべての注文および対応する `OrderID` のシーケンス。  
  
-   注文内で割引のある項目から成るサブシーケンス。  
  
-   出荷コストが含まれない場合に節約される費用。  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>関連項目  
 [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
