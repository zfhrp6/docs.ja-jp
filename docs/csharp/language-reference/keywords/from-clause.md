---
title: "from 句 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "from_CSharpKeyword"
  - "from"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "from 句 [C#]"
  - "from キーワード [C#]"
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# from 句 (C# リファレンス)
クエリ式は、`from` 句で始める必要があります。  また、クエリ式に含めることができるサブクエリも `from` 句で始めます。  `from` 句では、次の内容が指定されます。  
  
-   クエリまたはサブクエリが実行されるデータ ソース。  
  
-   ソース シーケンス内の各要素を表すローカルの*範囲変数*。  
  
 範囲変数とデータ ソースは両方とも厳密に型指定されます。  `from` 句で参照されるデータ ソースの型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、または派生型 \(たとえば <xref:System.Linq.IQueryable%601>\) です。  
  
 次の例では、`numbers` がデータ ソースで、`num` が範囲変数です。  [var](../../../csharp/language-reference/keywords/var.md) キーワードを使用する場合でも、両方の変数は厳密に型指定されます。  
  
 [!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]  
  
## 範囲変数  
 データ ソースが <xref:System.Collections.Generic.IEnumerable%601> を実装するときに、コンパイラは範囲変数の型を推論します。  たとえば、ソースの型が `IEnumerable<Customer>` の場合、範囲変数は `Customer` であると推論されます。  型を明示的に指定する必要があるのは、ソースが <xref:System.Collections.ArrayList> などの非ジェネリックの `IEnumerable` 型の場合のみです。  詳細については、「[How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)」を参照してください。  
  
 上の例では、`num` は `int` 型と推論されます。  範囲変数は厳密に型指定されるため、範囲変数でメソッドを呼び出したり、他の操作で範囲変数を使用したりできます。  たとえば、`select num` と記述する代わりに、クエリ式が整数ではなく文字列のシーケンスを返すように `select num.ToString()` と記述できます。  式がシーケンス 14、11、13、12、10 を返すように、`select n + 10` と記述することもできます。  詳細については、「[select 句](../../../csharp/language-reference/keywords/select-clause.md)」を参照してください。  
  
 範囲変数は [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントの繰り返し変数に似ていますが、範囲変数は実際にはソースのデータを格納しない点が異なります。  範囲変数は、構文を簡略化します。これを使用すると、クエリが実行されるときの処理の内容を表すことができます。  詳細については、「[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
## 複合 from 句  
 ソース シーケンス内の各要素がそれ自体でシーケンスであったり、シーケンスを含んでいたりする場合があります。  たとえば、データ ソースが `IEnumerable<Student>` で、そのシーケンス内の各学生オブジェクトがテストの得点の一覧を含む場合があります。  各 `Student` 要素内の内部一覧にアクセスするために、複合 `from` 句を使用できます。  この方法は、入れ子になった [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用するのに似ています。  いずれかの `from` 句に [where](../../../csharp/language-reference/keywords/partial-method.md) 句または [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 句を追加して、結果をフィルター処理します。  `Student` オブジェクトのシーケンスを次の例に示します。各オブジェクトには、テストの得点を表す整数の内部 `List` が含まれます。  内部一覧にアクセスするには、複合 `from` 句を使用します。  必要に応じて、2 つの `from` 句の間に句を挿入できます。  
  
 [!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]  
  
## 複数の from 句を使用した結合の実行  
 複合 `from` 句は、単一データ ソース内の内部コレクションにアクセスするために使用されます。  ただし、独立したデータ ソースから補足するクエリを生成する複数の `from` 句をクエリに含めることもできます。  この方法により、[join 句](../../../csharp/language-reference/keywords/join-clause.md)では実行できない特定の種類の結合操作を実行できます。  
  
 2 つの `from` 句を使用して、2 つのデータ ソースの完全なクロス結合を作成する方法を次の例に示します。  
  
 [!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]  
  
 複数の `from` 句を使用する結合操作の詳細については、「[方法 : カスタム結合操作を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)」を参照してください。  
  
## 参照  
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)