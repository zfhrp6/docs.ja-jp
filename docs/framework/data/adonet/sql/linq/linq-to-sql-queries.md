---
title: "LINQ to SQL Queries | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# LINQ to SQL Queries
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリは、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリと同じ構文を使用して定義します。  異なる点は、クエリ内で参照されるオブジェクトがデータベース内の要素に割り当てられるという点だけです。  詳細については、「[Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)」を参照してください。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、作成したクエリを同等の SQL クエリに変換し、それをサーバーに送って処理します。 具体的には、アプリケーションは [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API を使用してクエリの実行を要求します。  次に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロバイダーがクエリを SQL テキストに変換し、ADO プロバイダーに実行を委任します。 ADO プロバイダーは、クエリの結果を `DataReader` として返します。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] プロバイダーは、ADO の結果をユーザー オブジェクトの <xref:System.Linq.IQueryable> コレクションに変換します。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 組み込み型のほとんどのメソッドと演算子には、SQL に直接対応する変換が用意されています。  [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] で変換できないものについては、ランタイム例外が発生します。  詳細については、「[SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)」を参照してください。  
  
 次の表は、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリの項目と [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの項目の類似点と相違点を示すものです。  
  
|アイテム|LINQ クエリ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリ|  
|----------|--------------|--------------------------------------------------------------------|  
|クエリを保持するローカル変数の戻り値の型 \(シーケンスを返すクエリの場合\)|ジェネリック `IEnumerable`|ジェネリック `IQueryable`|  
|データ ソースの指定|`From` \([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\) 句または `from` \(C\#\) 句を使用|同|  
|フィルター処理|`Where`\/`where` 句を使用|同|  
|グループ化|`Group…By`\/`groupby` 句を使用|同|  
|選択 \(投影\)|`Select`\/`select` 句を使用|同|  
|遅延実行と即時実行|「[Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)」を参照してください。|同|  
|結合の実装|`Join`\/`join` 句を使用|`Join`\/`join` 句を使用できますが、<xref:System.Data.Linq.Mapping.AssociationAttribute> 属性を使用する方が効果的です。  詳細については、「[Querying Across Relationships](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)」を参照してください。|  
|リモート実行とローカル実行||詳細については、「[Remote vs. Local Execution](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)」を参照してください。|  
|ストリーミングとキャッシュ クエリ|ローカル メモリ シナリオでは適用なし||  
  
## 参照  
 [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)   
 [Basic LINQ Query Operations](../Topic/Basic%20LINQ%20Query%20Operations%20\(C%23\).md)   
 [Type Relationships in LINQ Query Operations](../Topic/Type%20Relationships%20in%20LINQ%20Query%20Operations%20\(C%23\).md)   
 [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)