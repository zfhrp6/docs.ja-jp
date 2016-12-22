---
title: "Let Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryLet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Let"
  - "Let clause"
  - "Let statement"
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Let Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

値を計算し、その値をクエリ内の新しい変数に代入します。  
  
## 構文  
  
```  
Let variable = expression [, ...]  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`variable`|必ず指定します。  指定した式の結果を参照するために使用できるエイリアスです。|  
|`expression`|必ず指定します。  評価し、指定した変数に代入する式です。|  
  
## 解説  
 `Let` 句を使用すると、各クエリ結果に対する値を計算し、エイリアスを使用してそれを参照できます。  エイリアスは、`Where` 句などの他の句で使用できます。  `Let` 句を使用すると、クエリに含まれる式の句に対してエイリアスを指定し、その式の句が使用されるたびにエイリアスに置き換えることができるので、読みやすいクエリ ステートメントを作成できます。  
  
 1 つの `Let` 句に、任意の数の `variable` と `expression` の代入を含めることができます。  各代入は、コンマ \(,\) で区切ります。  
  
## 使用例  
 次のコード例では、`Let` 句を使用して、製品の 10% 割り引きを計算しています。  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)