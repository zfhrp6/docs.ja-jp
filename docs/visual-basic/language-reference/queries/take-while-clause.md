---
title: "Take While Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryTakeWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Take While"
  - "Take While clause"
  - "Take While statement"
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Take While Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定された条件が `true` である限り、コレクションの要素を含むようにし、残りの要素をバイパスします。  
  
## 構文  
  
```  
Take While expression  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`expression`|必ず指定します。  要素をテストするための条件を表す式。  この式は、`Boolean` 値、または `Boolean` として評価される `Integer` などの機能的に同等な値を返す必要があります。|  
  
## 解説  
 `Take While` 句は、指定した `expression` が `false` を返すまで、クエリ結果の先頭から要素を取得します。  `expression` が `false` を返した後は、残っているすべての要素をバイパスします。  残りの結果では、`expression` は無視されます。  
  
 `Where` 句の場合、特定の条件を満たすすべての要素をクエリから取得できるという点で、`Take While` 句は `Where` 句と異なります。  `Take While` 句は、条件を満たさない最初の要素が出現するまで、要素を取得します。  `Take While` 句は、順序があるクエリ結果を操作する場合に最も役に立ちます。  
  
## 使用例  
 次のコード例では、`Take While` 句を使用して、注文がない最初の顧客が見つかるまで、結果を取得します。  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)