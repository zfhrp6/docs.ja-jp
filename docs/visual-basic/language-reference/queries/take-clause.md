---
title: "Take Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryTake"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Take statement"
  - "queries [Visual Basic], Take"
  - "Take clause"
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Take Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コレクションの先頭から、指定された数の連続する要素を返します。  
  
## 構文  
  
```  
Take count  
```  
  
## 指定項目  
 `count`  
 必ず指定します。  値、または返される連続する要素の数に評価される式。  
  
## 解説  
 `Take` 句を使用すると、結果リストの先頭から取得された、指定した数の連続する要素がクエリに含まれます。  含まれる要素の数は、`count` パラメーターによって指定されます。  
  
 `Take` 句を`Skip` 句と一緒に使用して、クエリの任意の部分の範囲のデータを返すことができます。  これを行うには、範囲の先頭となる要素のインデックスを `Skip` 句に渡し、範囲のサイズを `Take` 句に渡します。  この場合、`Take` 句は、`Skip` 句の後ろに指定する必要があります。  
  
 クエリで `Take` 句を使用するときは、`Take` 句によって目的の結果を取得することが可能な順序で結果が返されることを確認する必要があります。  クエリ結果の順序の詳細については、「[Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
 `TakeWhile` 句を使用して、指定した条件に応じた特定の要素だけが返されるように指定できます。  
  
## 使用例  
 次のコード例では、`Take` 句を `Skip` 句と一緒に使用して、ページのクエリからデータを返します。  GetCustomers 関数は、`Skip` 句を使用して、指定された開始インデックス値までリストの顧客をバイパスし、`Take` 句を使用して、そのインデックス値から始まる顧客のページを返します。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#1)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)