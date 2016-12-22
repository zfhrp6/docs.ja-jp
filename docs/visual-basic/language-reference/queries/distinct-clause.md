---
title: "Distinct Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryDistinct"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Distinct clause"
  - "Distinct statement"
  - "queries [Visual Basic], Distinct"
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Distinct Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

現在の範囲変数の値を制限して、次のクエリ句の重複値を取り除きます。  
  
## 構文  
  
```  
Distinct  
```  
  
## 解説  
 `Distinct` 句を使用して、一意の項目の一覧を返すことができます。  `Distinct` 句を使用すると、重複するクエリ結果が無視されます。  `Distinct` 句は、`Select` 句の指定によって返されるすべてのフィールドについて、重複する値に適用されます。  `Select` 句の指定がない場合、`Distinct` 句は、`From` 句に指定されたクエリの範囲変数に適用されます。  範囲変数が変更できない型の場合、その型のすべてのメンバーが既存のクエリ結果と一致すると、クエリ結果は無視されます。  
  
## 使用例  
 次のクエリ式は、顧客の一覧と顧客の注文の一覧を結合します。  一意の顧客名と注文日の一覧を返すために、`Distinct` 句が含まれています。  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)