---
title: "GUID と uniqueidentifier 値の比較 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# GUID と uniqueidentifier 値の比較
SQL Server のグローバル一意識別子 \(GUID: Globally Unique Identifier\) データ型は、16 バイトのバイナリ値を格納する `uniqueidentifier` データ型で表現されます。  GUID は、2 進数の値です。GUID は主に、多数のコンピューターが多数のサイトに存在するネットワーク内で、一意である必要のある識別子として使用されます。  GUID は、Transact\-SQL NEWID 関数を呼び出すことにより生成され、世界中のコンピューターの中で一意であることが保証されています。  詳細については、SQL Server オンライン ブックの「uniqueidentifier データの使用」を参照してください。  
  
## SqlGuid 値の使用  
 GUID の値は長くて不可解な値であるため、ユーザーには意味がわかりません。  ランダムに生成された GUID をキー値として使用して多数の行を挿入した場合に、ランダムな I\/O をインデックスにすると、パフォーマンスに悪影響を及ぼします。  また、GUID は、その他のデータ型に比べてサイズが大きくなります。  通常、GUID は、その他のデータ型が適さないような非常に限られた場合にのみ使用することをお勧めします。  
  
### GUID 値の比較  
 `uniqueidentifier` 型の値には比較演算子が使用できます。  ただし、順序付けは、2 つの値のビット パターンの比較によっては実装されません。  `uniqueidentifier` 値に対して実行可能な唯一の操作は、比較 \(\=、\<\>、\<、\>、\<\=、\>\=\) と NULL の確認 \(IS NULL および IS NOT NULL\) です。  これ以外の算術演算子を使用することはできません。  
  
 <xref:System.Guid> と <xref:System.Data.SqlTypes.SqlGuid> のいずれも、異なる GUID 値を比較するための `CompareTo` メソッドを持っています。  ただし、`System.Guid.CompareTo` と `SqlTypes.SqlGuid.CompareTo` では実装方法が異なります。  <xref:System.Data.SqlTypes.SqlGuid> は、値の末尾 6 バイトが最上位になる SQL Server の動作に従って `CompareTo` を実装します。  <xref:System.Guid> は、16 バイトすべてを評価します。  次の例は、この動作の違いを示しています。  コードの最初のセクションは、並べ替えられていない <xref:System.Guid> 値を表示し、コードの 2 つ目のセクションは、並べ替えられた <xref:System.Guid> 値を示します。  3 つ目のセクションは、並べ替えられた <xref:System.Data.SqlTypes.SqlGuid> 値を示します。  出力は、コードの一覧の下に表示されます。  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 この例を実行すると、次の結果が得られます。  
  
```  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## 参照  
 [SQL Server データ型と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)