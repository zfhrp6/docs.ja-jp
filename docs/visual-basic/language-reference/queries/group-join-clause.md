---
title: "Group Join Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryGroupJoinIn"
  - "vb.QueryGroupJoinOn"
  - "vb.QueryGroupJoin"
  - "vb.QueryGroupJoinInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Group Join clause"
  - "Group Join statement"
  - "queries [Visual Basic], Group Join"
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Group Join Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つのコレクションを、単一の階層コレクションに結合します。  結合操作は、一致するキーに基づいて実行されます。  
  
## 構文  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`element`|必ず指定します。  結合するコレクションのコントロール変数です。|  
|`type`|省略可能です。  `element` の型。  `type` の指定がない場合、`element` の型は `collection` から推論されます。|  
|`collection`|必ず指定します。  `Group Join` 演算子の左側にあるコレクションと結合するコレクション。  `Group Join` 句は、`Join` 句または別の `Group Join` 句の中に入れ子にできます。|  
|`key1` `Equals` `key2`|必ず指定します。  結合するコレクションのキーを識別します。  `Equals` 演算子を使用して、結合するコレクションのキーを比較する必要があります。  複数のキーを識別する `And` 演算子を使用して、結合条件を組み合わせることができます。  `key1` パラメーターは、`Join` 演算子の左側のコレクションのキーでなければなりません。  `key2` パラメーターは、`Join` 演算子の右側のコレクションのキーでなければなりません。<br /><br /> コレクションの複数の項目を含む式を結合条件で使用するキーにすることができます。  ただし、それぞれのキー式は、該当するコレクションの項目を 1 つだけ格納できます。|  
|`expressionList`|必ず指定します。  コレクションの要素グループの集計方法を識別する 1 つ以上の式。  グループ化された結果のメンバー名を識別するには、`Group` キーワード \(`<alias> = Group`\) を使用します。  グループに適用する集計関数を記述することもできます。|  
  
## 解説  
 `Group Join` 句は、結合するコレクションの一致するキー値に基づいて、2 つのコレクションを結合します。  結合後のコレクションには、第 2 のコレクションの要素のうち、第 1 のコレクションのキー値と一致する要素のコレクションを参照するメンバーを格納できます。  第 2 のコレクションのグループ化された要素に適用する集計関数を指定することもできます。  集計関数の詳細については、「[Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)」を参照してください。  
  
 たとえば、管理者のコレクションと従業員のコレクションがあるとします。  どちらのコレクションの要素にも、特定の管理者の部下である従業員を識別する ManagerID プロパティがあります。  結合操作の結果には、ManagerID 値が一致する管理者と従業員が含まれます。  `Group Join` 操作の結果には、管理者の完全な一覧が含まれます。  各管理者の結果には、それぞれの管理者と一致する従業員の一覧を参照するメンバーが含まれます。  
  
 `Group Join` 操作の結果作成されるコレクションには、`From` 句で識別されるコレクションの値と、`Group Join` 句の `Into` 句で識別される式の値の組み合わせが含まれます。  `Into` 句で有効な式の詳細については、[Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md) を参照してください。  
  
 `Group Join` 操作は、`Group Join` 演算子の左側で識別されるコレクションを結果としてすべて返します。  これは、結合するコレクションの中に一致するものがない場合にも当てはまります。  これは、SQL の `LEFT OUTER JOIN` に似ています。  
  
 `Join` 句を使用して、複数のコレクションを単一のコレクションに結合できます。  これは、SQL の `INNER JOIN` に相当します。  
  
## 使用例  
 次のコード例では、`Group Join` 句を使用して 2 つのコレクションを結合します。  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#14)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)