---
title: "Join Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryJoinIn"
  - "vb.QueryJoin"
  - "vb.QueryJoinOn"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Join"
  - "Join statement"
  - "Join clause"
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Join Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つのコレクションを単一のコレクションに結合します。  結合操作は一致キーに基づいて実行され、`Equals` 演算子を使用します。  
  
## 構文  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## 指定項目  
 `element`  
 必須。  結合するコレクションのコントロール変数です。  
  
 `collection`  
 必須。  `Join` 演算子の左側で識別されるコレクションと結合するコレクション。  `Join` 句は、別の `Join` 句の中に入れ子で指定することも、`Group Join` 句の中に指定することもできます。  
  
 `joinClause`  
 省略可能。  クエリを絞り込むための 1 つ以上の追加の `Join` 句。  
  
 `groupJoinClause`  
 省略可能。  クエリを絞り込むための 1 つ以上の追加の `Group Join` 句。  
  
 `key1` `Equals` `key2`  
 必須。  結合するコレクションのキーを識別します。  `Equals` 演算子を使用して、結合するコレクションのキーを比較する必要があります。  複数のキーを識別する `And` 演算子を使用して、結合条件を組み合わせることができます。  `key1` は、`Join` 演算子の左側のコレクションのキーでなければなりません。  `key2` は、`Join` 演算子の右側のコレクションのキーでなければなりません。  
  
 コレクションの複数の項目を含む式を結合条件で使用するキーにすることができます。  ただし、それぞれのキー式は、該当するコレクションの項目を 1 つだけ格納できます。  
  
## 解説  
 `Join` 句は、結合するコレクションの一致するキー値に基づいて、2 つのコレクションを結合します。  結合後のコレクションには、`Join` 演算子の左側で識別されるコレクションの値と、`Join` 句の中で識別されるコレクションの値が、任意の組み合わせで格納されます。  このクエリでは、`Equals` 演算子に指定した条件と一致する結果だけが返されます。  これは、SQL の `INNER JOIN` に相当します。  
  
 1 つのクエリで複数の `Join` 句を使用して、2 つ以上のコレクションを単一のコレクションに結合できます。  
  
 `Join` 句を使用せずに、暗黙的な結合を実行してコレクションを結合できます。  これを行うには、複数の `In` 句を `From` 句に記述し、結合で使用するキーを識別する `Where` 句を指定します。  
  
 `Group Join` 句を使用して、複数のコレクションを単一の階層コレクションに結合できます。  これは、SQL の `LEFT OUTER JOIN` に似ています。  
  
## 使用例  
 次のコード例では、暗黙的な結合を実行して、顧客リストと顧客の注文を結合します。  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## 使用例  
 次のコード例では、2 つのコレクションを `Join` 句を使用して結合します。  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 この例を実行すると、次のような出力が得られます。  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## 使用例  
 次のコード例では、2 つのコレクションを `Join` 句と 2 つのキー列を使用して結合します。  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 この例を実行すると、次のような出力が得られます。  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)