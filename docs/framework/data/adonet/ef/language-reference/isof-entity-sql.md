---
title: "ISOF (Entity SQL) | Microsoft Docs"
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
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# ISOF (Entity SQL)
式の型が指定の型であるか、またはそのサブタイプであるかを判断します。  
  
## 構文  
  
```  
  
expression IS [ NOT ] OF ( [ ONLY ] type)  
```  
  
## 引数  
 `expression`  
 型を判断するための任意の有効なクエリ式。  
  
 NOT  
 IS OF の EDM.Boolean の結果を否定します。  
  
 ONLY  
 `true` が `expression` 型であり、そのサブタイプでない場合に限り、IS OF が `type` を返すことを指定します。  
  
 `type`  
 `expression` を判定するための型。 型は名前空間で修飾する必要があります。  
  
## 戻り値  
 `true` が型 T で、T が基本データ型または `expression` の派生型である場合は、`type` となります。`expression` が実行時に null である場合は null となり、それ以外の場合は `false` となります。  
  
## 解説  
 `expression IS NOT OF (type)`  および  `expression IS NOT OF (ONLY type)`  式は、構文上はそれぞれ  `NOT (expression IS OF (type))`  および  `NOT (expression IS OF (ONLY type))` に相当します。  
  
 次の表に、いくつかの通常およびコーナー パターンにおける `IS OF` 演算子の動作を示します。 すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。  
  
|パターン|動作|  
|----------|--------|  
|null IS OF \(EntityType\)|スロー|  
|null IS OF \(ComplexType\)|スロー|  
|null IS OF \(RowType\)|スロー|  
|TREAT \(null AS EntityType\) IS OF \(EntityType\)|DBNull を返します。|  
|TREAT \(null AS ComplexType\) IS OF \(ComplexType\)|スロー|  
|TREAT \(null AS RowType\) IS OF \(RowType\)|スロー|  
|EntityType IS OF \(EntityType\)|true または false を返します。|  
|ComplexType IS OF \(ComplexType\)|スロー|  
|RowType IS OF \(RowType\)|スロー|  
  
## 使用例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、IS OF 演算子を使用してクエリ式の型を判定し、次に TREAT 演算子を使用して Course 型のオブジェクトを OnsiteCourse 型のオブジェクトのコレクションに変換します。 このクエリは、[School モデル](http://msdn.microsoft.com/ja-jp/859a9587-81ea-4a45-9bc0-f8d330e1adac)に基づいています。  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)