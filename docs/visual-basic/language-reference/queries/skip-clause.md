---
title: "Skip Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySkip"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Skip"
  - "Skip statement"
  - "Skip clause"
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Skip Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コレクション内の指定された数の要素をバイパスし、残りの要素を返します。  
  
## 構文  
  
```  
Skip count  
```  
  
## 指定項目  
 `count`  
 必ず指定します。  スキップする連続する要素の数として評価される値または式です。  
  
## 解説  
 `Skip` 句を使用すると、クエリは結果リストの先頭から指定した数の要素をバイパスし、残りの要素を返します。  スキップする要素の数は、`count` パラメーターで指定します。  
  
 `Skip` 句を `Take` 句と一緒に使用して、クエリの任意の部分のデータ範囲を返すことができます。  これを行うには、範囲の先頭となる要素のインデックスを `Skip` 句に渡し、範囲のサイズを `Take` 句に渡します。  
  
 クエリで `Skip` 句を使用するときは、`Skip` 句が意図した結果をバイパスできるような順序で結果が返されることも、確認することが必要になる場合があります。  クエリ結果の順序の詳細については、「[Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
 `SkipWhile` 句を使用すると、指定した条件に応じた特定の要素だけが無視されるように指定できます。  
  
## 使用例  
 次のコード例では、`Skip` 句を `Take` 句と一緒に使用して、ページのクエリからデータを返します。  `GetCustomers` 関数は、`Skip` 句を使用して、指定されたインデックス値になるまでリストの顧客をバイパスし、`Take` 句を使用して、そのインデックス値から始まる顧客のページを返します。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#1)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)