---
redirect_url: /dotnet/articles/csharp/linq/write-linq-queries
caps.handback.revision: 25
---
# 方法 : C# で LINQ クエリを作成する
このトピックでは、C\# で [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリを作成する次の 3 つの方法について説明します。  
  
1.  クエリ構文を使用する。  
  
2.  メソッド構文を使用する。  
  
3.  クエリ構文とメソッド構文を組み合わせて使用する。  
  
 上に示したそれぞれの方法を使用した簡単な [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリを以下の例に示します。  一般に、クエリを作成する規則として、可能な限り \(1\) を使用し、必要に応じて \(2\) および \(3\) を使用します。  
  
> [!NOTE]
>  これらのクエリは、簡単なメモリ内コレクションで動作します。ただし、基本的な構文は、[!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] および [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] で使用される構文と同じです。  
  
## 使用例  
  
## クエリ構文  
 ほとんどのクエリを作成する場合に、*クエリ構文*を使用して*クエリ式*を作成する方法が推奨されます。  次の例では、3 つのクエリ式を示します。  最初のクエリ式は、`where` 句を使用した条件を適用することにより、結果をフィルター処理または制限する方法を示しています。  これは、ソース シーケンス内の値が 7 よりも大きいか 3 よりも小さいすべての要素を返します。  2 番目の式は、返された結果の順序を指定する方法を示します。  3 番目の式は、結果をキーに従ってグループ化する方法を示します。  このクエリは、単語の最初の文字に基づいて 2 つのグループを返します。  
  
 [!code-cs[csProgGuideLINQ#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_1.cs)]  
  
 このクエリの型は <xref:System.Collections.Generic.IEnumerable%601> です。  次の例に示すように、これらのクエリのすべてを `var` を使用して記述できます。  
  
 `var query = from num in numbers...`  
  
 前のそれぞれの例で、`foreach` ステートメントによるクエリ変数の反復処理が完了するまで、クエリは実行されません。  詳細については、「[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
## 使用例  
  
## メソッド構文  
 一部のクエリ操作は、メソッド呼び出しとして表現する必要があります。  最も一般的なメソッドは、<xref:System.Linq.Enumerable.Sum%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Average%2A> など、シングルトン数値を返すメソッドです。  これらのメソッドは単一の値のみを表し、追加のクエリ操作のソースとして使用できないため、いずれのクエリでも常に最後に呼び出す必要があります。  クエリ式のメソッド呼び出しの例を次に示します。  
  
 [!code-cs[csProgGuideLINQ#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_2.cs)]  
  
## 使用例  
 メソッドにパラメーターがある場合は、次の例に示すように、[ラムダ](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)式の形式で渡します。  
  
 [!code-cs[csProgGuideLINQ#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_3.cs)]  
  
 前のクエリでは、Query \#4 だけがすぐに実行されます。  これは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック コレクションではなく、単一の値が返されるためです。  メソッド自体は、値を計算するために `foreach` を使用する必要があります。  
  
 前の各クエリは、次の例に示すように、[var](../../../csharp/language-reference/keywords/var.md) による暗黙の型指定を使用して記述できます。  
  
 [!code-cs[csProgGuideLINQ#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_4.cs)]  
  
## 使用例  
  
## クエリ構文とメソッド構文の組み合わせ  
 この例では、クエリ句の結果に基づいてメソッド構文を使用する方法を示します。  クエリ式をかっこで囲み、ドット演算子を適用してメソッドを呼び出します。  次の例で Query \#7 は、値が 3 ～ 7 の数を返します。  ただし、通常は、2 番目の変数を使用してメソッド呼び出しの結果を格納することをお勧めします。  この方法では、クエリがクエリの結果と混同される可能性が低くなります。  
  
 [!code-cs[csProgGuideLINQ#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-write-linq-queries_5.cs)]  
  
 Query \#7 は、ジェネリック コレクションではなく単一の値を返すため、すぐに実行されます。  
  
 前の各クエリは、次に示すように、`var` による暗黙の型指定を使用して記述できます。  
  
```  
var numCount = (from num in numbers...  
```  
  
 メソッド構文では次のように記述できます。  
  
```  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 明示的な型指定を使用すると、次のように記述できます。  
  
```  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## 参照  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Walkthrough: Writing Queries in C\#](../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [where 句](../../../csharp/language-reference/keywords/where-clause.md)