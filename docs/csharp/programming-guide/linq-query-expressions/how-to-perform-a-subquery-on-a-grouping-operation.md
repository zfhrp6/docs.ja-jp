---
redirect_url: /dotnet/articles/csharp/linq/perform-a-subquery-on-a-grouping-operation
caps.handback.revision: 15
---
# 方法: グループ化操作でサブクエリを実行する (C# プログラミング ガイド)
ここでは、2 つの異なる方法を使用して、参照元データをグループ単位で並べ替え、各グループに対して個別にサブクエリを実行するクエリを作成します。  ソース要素をグループ化するために各例で使用する基本的な方法は、`newGroup` という名前の新しい*継続*を使用し、`newGroup` に対する新しいサブクエリを生成するというものです。  このサブクエリは、外部クエリによって作成される新しいグループのそれぞれに対して実行されます。  この例では、最終的な出力はグループではなく、匿名型のフラットなシーケンスです。  
  
 グループ化の方法の詳細については、「[group 句](../../../csharp/language-reference/keywords/group-clause.md)」を参照してください。  
  
 継続の詳細については、「[into](../../../csharp/language-reference/keywords/into.md)」を参照してください。  次の例では、インメモリ データ構造をデータ ソースとして使用していますが、任意の種類の [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] データ ソースで同じ基本原則が当てはまります。  
  
## 使用例  
 [!code-cs[csProgGuideLINQ#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
  
## コードのコンパイル  
 この例には、「[方法 : オブジェクトのコレクションを照会する](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)」のサンプル アプリケーションで定義されているオブジェクトへの参照があります。  このメソッドをコンパイルして実行するには、メソッドをそのアプリケーションの `StudentClass` クラスに貼り付け、`Main` メソッドからそのメソッドを呼び出すコードを追加します。  
  
 独自のアプリケーションに合わせてこのメソッドを変更する場合、LINQ には [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Version 3.5 が必要なこと、および System.Core.dll への参照と System.Linq の using ディレクティブをプロジェクトに含める必要があることに注意してください。  LINQ to SQL、LINQ to XML、および LINQ to DataSet の場合は、追加の using と参照も必要です。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)