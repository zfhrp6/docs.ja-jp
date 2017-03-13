---
redirect_url: /dotnet/articles/csharp/linq/store-the-results-of-a-query-in-memory
caps.handback.revision: 13
---
# 方法 : クエリの結果をメモリに格納する (C# プログラミング ガイド)
基本的に、クエリは、データの取得方法と編成方法を指示するための一連の命令です。  クエリを実行するには、<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドを呼び出す必要があります。  この呼び出しは、`foreach` ループを使用して要素を反復処理する際に行います。  クエリを評価し、`foreach` のループを実行せずに結果を格納するには、クエリ変数で次のメソッドを 1 回を呼び出します:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 クエリ結果を格納するときは、次の例に示すように、返されたコレクション オブジェクトを新しい変数に代入することをお勧めします。  
  
## 使用例  
 [!code-cs[csProgGuideLINQ#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  
## コードのコンパイル  
  
-   .NET Framework Version 3.5 を対象とする [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] プロジェクトを作成します。  既定では、プロジェクトには、System.Core.dll への参照と、System.Linq 名前空間に対する `using` ディレクティブが含まれます。  
  
-   コードをプロジェクト内にコピーします。  
  
-   F5 キーを押して、プログラムをコンパイルおよび実行します。  
  
-   任意のキーを押して、コンソール ウィンドウを終了します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)