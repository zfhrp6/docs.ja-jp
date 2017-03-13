---
title: "select 句 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "select_CSharpKeyword"
  - "select"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "select 句 [C#]"
  - "select キーワード [C#]"
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# select 句 (C# リファレンス)
クエリ式で、`select` 句は、クエリを実行したときに生成される値の型を指定します。  結果は、前にあるすべての句の評価および `select` 句自体の式に基づいて生成されます。  クエリ式の末尾は `select` 句または [group](../../../csharp/language-reference/keywords/group-clause.md) 句にする必要があります。  
  
 クエリ式の簡単な `select` 句の例を次に示します。  
  
 [!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 `select` 句で生成されるシーケンスの型によって、クエリ変数 `queryHighScores` の型が決まります。  最も簡単なケースでは、`select` で範囲変数だけを指定します。  この場合、返されるシーケンスにはデータ ソースと同じ型の要素が含まれます。  詳細については、「[Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。  一方、`select` 句には、ソース データを新しい型に変換 \(または*投影*\) するための強力な機構も用意されています。  詳細については、「[LINQ によるデータ変換 \(C\#\)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)」を参照してください。  
  
## 使用例  
 `select` 句で指定できるさまざまな形式すべてを次の例に示します。  それぞれのクエリで、`select` 句と*クエリ変数*の型 \(`studentQuery1`、`studentQuery2` など\) の関係を確認してください。  
  
 [!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 前の例の `studentQuery8` に示したように、返されるシーケンスの要素を、ソース要素のプロパティのサブセットだけに制限することが必要になる場合があります。  返されるシーケンスをできる限り小さいサイズにすることにより、必要となるメモリ量を減らし、クエリの実行速度を高めることができます。  これは、`select` 句で匿名型を作成し、オブジェクト初期化子を使用して、ソース要素の適切なプロパティでその匿名型を初期化することにより実現できます。  この操作を行う方法の例については、「[オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。  
  
## 解説  
 コンパイル時に、`select` 句は <xref:System.Linq.Enumerable.Select%2A> 標準クエリ演算子に対するメソッド呼び出しに変換されます。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [from 句](../../../csharp/language-reference/keywords/from-clause.md)   
 [partial \(メソッド\) \(C\# リファレンス\)](../../../csharp/language-reference/keywords/partial-method.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)