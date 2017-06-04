---
title: "LINQ to Entities クエリ内の式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# LINQ to Entities クエリ内の式
式は、単一の値、オブジェクト、メソッド、または名前空間として評価されるコード フラグメントです。  式には、リテラル値、メソッド呼び出し、演算子とそのオペランド、または単純な名前を含めることができます。  単純な名前には、変数、型メンバー、メソッド パラメーター、名前空間、または型の名前を指定できます。  式では、他の式をパラメーターとして使用する演算子、またはパラメーターが他のメソッド呼び出しであるメソッド呼び出しを使用できます。  したがって、単純な式だけでなく、非常に複雑な式も作成できます。  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリの式には、ラムダ式など、<xref:System.Linq.Expressions> 名前空間内の型で許容されている要素であれば何でも使用できます。  [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリで使用可能な式は、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] に対してクエリを実行するために使用可能な式のスーパーセットです。  [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] に対するクエリの一部である式は、`ObjectQuery<T>` および基になるデータ ソースでサポートされている演算に制限されます。  
  
 次の例では、`Where` 句で使用される比較の式を示します。  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  C\# の `unchecked` などの特殊な言語構造は、[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] では意味がありません。  
  
## このセクションの内容  
 [定数式](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [比較式](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [NULL 比較](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [初期化式](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Navigation Properties](http://msdn.microsoft.com/ja-jp/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## 参照  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)