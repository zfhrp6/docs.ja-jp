---
title: "Select Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySelect"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Select statement"
  - "Select clause"
  - "queries [Visual Basic], Select"
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Select Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クエリの結果を定義します。  
  
## 構文  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## 指定項目  
 `var1`  
 省略可能です。  列の式の結果を参照するために使用できるエイリアスです。  
  
 `fieldName1`  
 必ず指定します。  クエリ結果内の結果を返すフィールドの名前です。  
  
## 解説  
 `Select` 句を使用して、クエリから返される結果を定義できます。  これにより、クエリで作成される新しい匿名型のメンバーを定義するか、またはクエリで返される名前付きの型のメンバーを対象にできます。  `Select` 句は、クエリでは必須ではありません。  `Select` 句の指定がない場合、クエリは、現在のスコープで識別される範囲変数のすべてのメンバーに基づく型を返します。  詳細については、「[Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  クエリで名前付きの型が作成される場合は、<xref:System.Collections.Generic.IEnumerable%601> 型の結果が返されます。`T` は作成された型を表します。  
  
 `Select` 句では、現在のスコープ内の任意の変数を参照できます。  これには、`From` 句 \(または複数の `From` 句\) で識別される範囲変数も含まれます。  さらに、`Aggregate` 句、`Let` 句、`Group By` 句、または `Group Join` 句によってエイリアスを使用して作成された新しい変数と、クエリ式で前の位置に出現する `Select` 句の変数も含まれます。  `Select` 句には、静的な値を含めることもできます。  たとえば、次のコード例は、`Select` 句でクエリ結果を新しい匿名型として定義するクエリ式を示しています。この匿名型には、`ProductName`、`Price`、`Discount`、および `DiscountedPrice` という 4 つのメンバーがあります。  `ProductName` メンバーと `Price` メンバーの値は、`From` 句で定義される製品の範囲変数から取得されます。  `DiscountedPrice` メンバーの値は、`Let` 句で計算されます。  `Discount` メンバーは静的な値です。  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 `Select` 句は、以降のクエリ句のために新しい範囲変数セットを導入します。前の範囲変数はスコープ外になります。  クエリの戻り値は、クエリ式の最後の `Select` 句によって決定されます。  たとえば、次のクエリでは、合計が 500 を超えるすべての注文について、会社名と注文 ID を返します。  最初の `Select` 句は、`Where` 句と 2 番目の `Select` 句の範囲変数を識別します。  2 番目の `Select` 句は、このクエリで返される値を、新しい匿名型として識別します。  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 単一の項目を返すことが `Select` 句で識別された場合、クエリ式は、その単一の項目の型のコレクションを返します。  複数の項目を返すことが `Select` 句で識別された場合、クエリ式は、選択された項目に基づいて、新しい匿名型のコレクションを返します。  たとえば、次の 2 つのクエリでは、`Select` 句に基づいて、2 つの異なる型のコレクションが返されます。  最初のクエリでは、会社名を表す文字列のコレクションが返されます。  2 番目のクエリでは、会社名と住所の情報が格納された `Customer` オブジェクトのコレクションが返されます。  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## 使用例  
 次のクエリ式では、`From` 句を使用して、`customers` コレクションの範囲変数 `cust` を宣言します。  `Select` 句は、顧客名と ID 値を選択し、新しい範囲変数の `CompanyName` 列と `CustomerID` 列に値を格納します。  `For Each` ステートメントを使用して、返された各オブジェクトをループで処理し、各レコードの `CompanyName` 列と `CustomerID` 列を表示します。  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)