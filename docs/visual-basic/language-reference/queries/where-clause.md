---
title: "Where Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QueryWhere"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Where statement"
  - "queries [Visual Basic], Where"
  - "Where clause"
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Where Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

クエリのフィルター処理条件を指定します。  
  
## 構文  
  
```  
Where condition  
```  
  
## 指定項目  
 `condition`  
 必ず指定します。  コレクション内の現在の項目の値を、出力されるコレクションに含めるかどうかを決定する式。  この式は、`Boolean` 値、または`Boolean` 値の同等値に評価される必要があります。  条件の評価が `True` の場合、要素はクエリ結果に含まれます。それ以外の場合、要素はクエリ結果から除外されます。  
  
## 解説  
 `Where` 句を使用すると、特定の条件を満たす要素だけを選択することでクエリ データをフィルター処理できます。  クエリ結果には、値が `Where` 句によって `True` と評価される要素が格納されます。それ以外の要素は除外されます。  `Where` 句で使用される式は、`Boolean` と評価される式、または`Boolean` と同等 \(値がゼロの場合は `False` と評価される整数など\) でなければなりません。  `And`、`Or`、`AndAlso`、`OrElse`、`Is`、`IsNot` などの論理演算子を使用することで、`Where` 句の中で複数の式を組み合わせることができます。  
  
 既定では、クエリ式はアクセスされる \(データにバインドされたり、`For` ループで反復されたりする\) まで評価されません。  この結果、`Where` 句は、クエリがアクセスされるまで評価されません。  `Where` 句で使用するクエリに対して外部の値がある場合は、クエリの実行時に `Where` 句で適切な値が使用されることを確認してください。  クエリ実行の詳細については、「[初めての LINQ クエリの作成](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)」を参照してください。  
  
 `Where` 句の中で関数を呼び出して、コレクション内の現在の要素の値に対して計算または操作を実行できます。  `Where` 句の中で関数を呼び出すと、アクセス時ではなく定義時に直ちにクエリを実行できます。  クエリ実行の詳細については、「[初めての LINQ クエリの作成](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)」を参照してください。  
  
## 使用例  
 次のクエリ式では、`From` 句を使用して、`customers` コレクション内の各 `Customer` オブジェクト用の範囲変数 `cust` を宣言します。  `Where` 句は、この範囲変数を使用して、出力を指定された地区の顧客に制限します。  `For Each` ループにより、クエリ結果内の各顧客の会社名が表示されます。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## 使用例  
 次の例では `Where` の句で `And` と `Or` の論理演算子を使用します。  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## 参照  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)