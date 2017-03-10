---
title: "where 句 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "whereclause_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "where 句 [C#]"
  - "where キーワード [C#]"
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# where 句 (C# リファレンス)
`where` 句はクエリ式で使用され、クエリ式でデータ ソースのどの要素が返されるようにするかを指定します。  各ソース要素 \(範囲変数で参照される\) にブール条件 \(*述語*\) を適用し、指定した条件に該当するものを返します。  単一のクエリ式に複数の `where` 句を含めることができ、単一の句に複数の述語部分式を含めることができます。  
  
## 使用例  
 次の例の `where` 句は、5 未満の数値以外のすべての数値をフィルターで除外します。  `where` 句を削除すると、データ ソースのすべての数値が返されます。  式 `num < 5` が各要素に適用される述語です。  
  
 [!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Where.cs#5)]  
  
## 使用例  
 単一の `where` 句の中で、[&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 演算子と [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 演算子を使用することにより、述語を必要な数だけ指定できます。  次の例のクエリは、5 未満の偶数だけを選択するために 2 つの述語を指定しています。  
  
 [!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Where.cs#6)]  
  
## 使用例  
 `where` 句には、ブール値を返すメソッドを 1 つ以上含めることができます。  次の例の `where` 句は、範囲変数の現在の値が偶数であるか奇数であるかを判断するためにメソッドを使用しています。  
  
 [!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Where.cs#7)]  
  
## 解説  
 `where` 句はフィルター処理機構です。  クエリ式内の最初の句と最後の句以外のほとんどどこにでも置くことができます。  `where` 句は、[group](../../../csharp/language-reference/keywords/group-clause.md) 句の前にも後ろにも置くことができます。どちらに置くかは、ソース要素のフィルター処理をグループ化の前に行うか後に行うかによります。  
  
 指定した述語がデータ ソースの要素に対して無効だった場合、コンパイル時にエラーになります。  これは、[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] が備えている厳密な型チェックの 1 つの利点です。  
  
 `where` キーワードは、コンパイル時に <xref:System.Linq.Enumerable.Where%2A> 標準クエリ演算子メソッドの呼び出しに変換されます。  
  
## 参照  
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from 句](../../../csharp/language-reference/keywords/from-clause.md)   
 [select 句](../../../csharp/language-reference/keywords/select-clause.md)   
 [Filtering Data](../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)