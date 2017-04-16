---
title: "Querying Across Relationships | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Querying Across Relationships
他のオブジェクトまたは他のオブジェクトのコレクションをクラス定義内で参照することは、データベース内の外部キー リレーションシップに直接対応します。  クエリを実行するときにこのリレーションシップを使用するには、ドット表記を使ってリレーションシップ プロパティにアクセスし、オブジェクト間を移動します。  これらのアクセス操作は、SQL で同等の複雑な結合または相関サブクエリとして変換されます。  
  
 たとえば、次のクエリでは、ロンドン在住の顧客からの注文のみが結果として得られるように注文から顧客へと移動します。  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 リレーションシップ プロパティが存在しない場合は、これを*結合*として、SQL で記述するときと同じように手動で作成する必要があります。次にコードの例を示します。  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 このようなリレーションシップは、*リレーションシップ* プロパティを使用すると一度に定義できます。  こうすると、使いやすいドット構文を使用できるようになります。  しかし、それだけがリレーションシップ プロパティの利点ではありません。なぜなら、通常はドメイン固有のオブジェクト モデルは階層構造またはグラフとして定義されるからです。  プログラムで使用するオブジェクトには他のオブジェクトへの参照が含まれます。  このオブジェクト間リレーションシップがデータベースの外部キー型リレーションシップに相当するのは、単なる幸運な偶然です。  プロパティへのアクセスは、結合を記述するための便利な方法となります。  
  
 この点では、リレーションシップ プロパティは、クエリそのものよりもクエリの結果でより重要です。  クエリによって特定の顧客に関するデータが取得された後で、クラス定義ではその顧客の注文が存在することが示されます。  つまり、特定の顧客の `Orders` プロパティにその顧客のすべての注文が含まれると見なすことができます。  実際には、これはクラスをこのように定義することにより宣言したコントラクトです。  クエリによって注文が要求されなかった場合でも、ここに注文が含まれていると見なすことができます。  オブジェクト モデルに対して期待されるのは、それがデータベースがメモリ内に拡張されたものであり、関連オブジェクトがすぐに使用できる状態にある、という錯覚を維持することです。  
  
 リレーションシップが得られたので、クラスに定義されたリレーションシップ プロパティを参照してクエリを作成できます。  これらのリレーションシップ参照は、データベース内の外部キー リレーションシップに対応します。  これらのリレーションシップを使用する操作は、SQL で同等の複雑な結合として変換されます。  <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を使用してリレーションシップを定義している限りは、明示的な結合を [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で記述する必要はありません。  
  
 この錯覚を維持するために、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] には*遅延読み込み*と呼ばれる機能が実装されています。  詳細については、「[Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)」を参照してください。  
  
 たとえば、`CustomerID`\-`OrderID` ペアのリストを射影する次の SQL クエリがあるとします。  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用して同じ結果を得るには、`Orders` クラスに既に存在する `Customer` プロパティ参照を使用します。  次のコードに示すとおり、`Orders` 参照からは、クエリを実行し、`CustomerID`\-`OrderID` ペアを射影するために必要な情報が提供されます。  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 逆の操作も可能です。  つまり、`Orders` にクエリを実行し、その `Customer` リレーションシップ参照を使用して、関連付けられた `Customer` オブジェクトに関する情報にアクセスできます。  次のコードでは、前の例と同じ `CustomerID`\-`OrderID` ペアを射影しますが、ここでは `Orders` ではなく `Customers` にクエリを実行しています。  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## 参照  
 [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)