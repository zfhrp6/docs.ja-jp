---
title: "Skip While Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySkipWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Skip While statement"
  - "Skip While clause"
  - "queries [Visual Basic], Skip While"
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Skip While Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。  
  
## 構文  
  
```  
Skip While expression  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`expression`|必ず指定します。  要素をテストするための条件を表す式。  この式は、`Boolean` 値、または `Boolean` として評価される `Integer` などの機能的に同等な値を返す必要があります。|  
  
## 解説  
 `Skip While` 句は、指定された `expression` が `false` を返すまで、クエリ結果の先頭から要素をバイパスします。  `expression` が `false` を返した後、残っているすべての要素が結果として返されます。  残りの結果では、`expression` は無視されます。  
  
 `Where` 句の場合、特定の条件と一致しないすべての要素をクエリから除外できるという点で、`Skip While` 句は `Where` 句とは異なります。  `Skip While` 句は、条件を満たさない最初の要素が出現するまで、要素を除外します。  `Skip While` 句は、順序があるクエリ結果を操作する場合に最も役に立ちます。  
  
 `Skip` 句を使用することで、クエリ結果の先頭から特定の数の結果をバイパスできます。  
  
## 使用例  
 次のコード例では、`Skip While` 句を使用して、米国 \(United States\) 在住の最初の顧客が見つかるまで結果をバイパスします。  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#3)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)