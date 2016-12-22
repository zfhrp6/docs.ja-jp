---
title: "Order By Clause (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryOrderBy"
  - "vb.QueryAscending"
  - "vb.QueryDescending"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Order By"
  - "Order By clause"
  - "Order By statement"
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Order By Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

クエリ結果の並べ替え順序を指定します。  
  
## 構文  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## 指定項目  
 `orderExp1`  
 必ず指定します。  返される値を並べ替える方法を示す、現在のクエリ結果に含まれる 1 つ以上のフィールド。  フィールド名は、コンマ \(,\) で区切る必要があります。  `Ascending` キーワードまたは `Descending` キーワードを使用することで、各フィールドを昇順または降順のどちらに並べ替えるかを指定できます。  `Ascending` または `Descending` のどちらのキーワードも指定しない場合の既定の並べ替え順序は昇順です。  並べ替え順序フィールド間の優先順位は、左から右です。  
  
## 解説  
 `Order By` 句を使用すると、クエリの結果を並べ替えることができます。  `Order By` 句は、現在のスコープの範囲変数に基づいてのみ、結果を並べ替えることができます。  たとえば、`Select` 句は、新しいスコープに対する新しい反復変数により、クエリ式にそのスコープを設定します。  クエリで `Select` 句より前に定義されていた範囲変数は、`Select` 句の後では使用できなくなります。  したがって、`Select` 句では使用できないフィールドで結果を並べ替える必要がある場合は、`Select` 句の前に `Order By` 句を置く必要があります。  このようなことを行う必要がある場合の 1 つの例は、結果の一部として返されないフィールドでクエリを並べ替える場合です。  
  
 フィールドの昇順と降順は、そのフィールドのデータ型に対する <xref:System.IComparable> インターフェイスの実装によって決まります。  データ型が <xref:System.IComparable> インターフェイスを実装していない場合、並べ替え順序は無視されます。  
  
## 使用例  
 次のクエリ式では、`From` 句を使用して、`books` コレクションの範囲変数 `book` を宣言します。  `Order By` 句は、価格の昇順 \(既定\) にクエリ結果を並べ替えます。  同じ価格の本は、書名の昇順に並べられます。  `Select` 句は、クエリによって返される値として `Title` プロパティと `Price` プロパティを選択します。  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## 使用例  
 次のクエリ式は、`Order By` 句を使用して、クエリ結果を価格の降順に並べ替えます。  同じ価格の本は、書名の昇順に並べられます。  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## 使用例  
 次のクエリ式は、`Select` 句を使用して、書名、価格、発行日、および著者を選択します。  その後、範囲変数の `Title`、`Price`、`PublishDate`、`Author` の各フィールドに、新しいスコープを設定します。  `Order By` 句は、著者名、書名、価格の順に、新しい範囲変数を並べ替えます。  各列は、既定の順序 \(昇順\) に並べられます。  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)