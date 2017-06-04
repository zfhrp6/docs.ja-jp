---
title: "How to: Directly Execute SQL Queries | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Directly Execute SQL Queries
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、作成したクエリをパラメーター化された SQL クエリ \(テキスト形式\) に変換し、それを SQL Server に送って処理します。  
  
 アプリケーションでローカルに使用できるさまざまなメソッドの中には、SQL では実行できないものもあります。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、このようなローカル メソッドを、SQL 環境内で使用できる同等の操作や関数に変換しようとします。  [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 組み込み型のほとんどのメソッドと演算子には、SQL コマンドに直接対応する変換が用意されています。  使用可能な関数から生成できるものもあります。  生成できないものについては、ランタイム例外が発生します。  詳細については、「[SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)」を参照してください。  
  
 特殊なタスクに対して [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリでは不十分な場合は、<xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドを使用して SQL クエリを実行し、そのクエリの結果をオブジェクトに直接変換できます。  
  
## 使用例  
 次の例では、`Customer` クラスのデータが 2 つのテーブル \(customer1 および customer2\) にわたって格納されているものとします。  クエリは `Customer` オブジェクトのシーケンスを返します。  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 表形式の結果の列名がエンティティ クラスの列のプロパティと一致する限り、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は SQL クエリからオブジェクトを作成します。  
  
## 使用例  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドは、パラメーターの使用にも対応しています。  パラメーター化されたクエリを実行するには、次のようなコードを使用します。  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 クエリ テキスト内では、`Console.WriteLine()` および `String.Format()` で使用するのと同じ中かっこ表記を使用して、パラメーターを表現します。  実際には、指定したクエリ文字列について `String.Format()` が呼び出され、中かっこで囲まれたパラメーターは、生成された @p0、@p1、...、@p\(n\) のようなパラメーター名に置き換えられます。  
  
## 参照  
 [Background Information](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [Querying the Database](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)