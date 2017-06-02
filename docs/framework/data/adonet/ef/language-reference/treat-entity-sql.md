---
title: "TREAT (Entity SQL) | Microsoft Docs"
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
  - "ESQL"
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# TREAT (Entity SQL)
特定の基本データ型のオブジェクトを指定の派生型のオブジェクトとして処理します。  
  
## 構文  
  
```  
  
TREAT (expression as type)  
```  
  
## 引数  
 `expression`  
 エンティティを返す任意の有効なクエリ式。  
  
> [!NOTE]
>  指定の式の型は、特定のデータ型のサブタイプである必要があります。または、データ型は式の型のサブタイプである必要があります。  
  
 `type`  
 エンティティ型。 型は名前空間で修飾する必要があります。  
  
> [!NOTE]
>  指定の式は、特定のデータ型のサブタイプである必要があります。または、データ型は式のサブタイプである必要があります。  
  
## 戻り値  
 指定されたデータ型の値。  
  
## 解説  
 TREAT は関連クラス間でキャストを実行するために使用します。 たとえば、`Employee` が `Person` から派生し、p が `Person` 型である場合、`TREAT(p AS NamespaceName.Employee)` はジェネリック型の `Person` インスタンスを `Employee` にキャストします。つまり、p を `Employee` として処理できます。  
  
 TREAT は、次のようにクエリを実行できる継承シナリオで使用されます。  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 このクエリは、`Person` エンティティを `Employee` 型にキャストします。 p の値が実際には `Employee` 型でない場合、この式は `null` 値を返します。  
  
> [!NOTE]
>  指定された式 ```Employee``` は、指定されたデータ型 `Person` のサブタイプである必要があります。または、データ型は式のサブタイプである必要があります。 そうでない場合は、コンパイル時にエラーが発生します。  
  
 次の表に、いくつかの通常パターンと一般的でないパターンにおける TREAT の動作を示します。 すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。  
  
|パターン|動作|  
|----------|--------|  
|`TREAT (null AS EntityType)`|`DbNull` を返します。|  
|`TREAT (null AS ComplexType)`|例外をスローします。|  
|`TREAT (null AS RowType)`|例外をスローします。|  
|`TREAT (EntityType AS EntityType)`|`EntityType` または `null` を返します。|  
|`TREAT (ComplexType AS ComplexType)`|例外をスローします。|  
|`TREAT (RowType AS RowType)`|例外をスローします。|  
  
## 使用例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、TREAT 演算子を使用して、Course 型のオブジェクトを OnsiteCourse 型のオブジェクトのコレクションに変換します。 このクエリは、[School モデル](http://msdn.microsoft.com/ja-jp/859a9587-81ea-4a45-9bc0-f8d330e1adac)に基づいています。  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [NULL 値が許容される構造化型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)