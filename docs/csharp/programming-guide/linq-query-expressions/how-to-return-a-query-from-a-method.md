---
redirect_url: /dotnet/articles/csharp/linq/return-a-query-from-a-method
caps.handback.revision: 11
---
# 方法 : メソッドからクエリを返す (C# プログラミング ガイド)
この例では、メソッドからクエリを戻り値および `out` パラメーターとして返す方法を示します。  
  
 クエリの型は、<xref:System.Collections.IEnumerable> か <xref:System.Collections.Generic.IEnumerable%601>、または <xref:System.Linq.IQueryable%601> のような派生型である必要があります。  したがって、クエリを返すメソッドの戻り値または `out` パラメーターも同じ型である必要があります。  メソッドがクエリを具象型の <xref:System.Collections.Generic.List%601> または <xref:System.Array> に実体化する場合は、クエリ自体ではなくクエリ結果を返すと見なされます。  メソッドから返されたクエリ変数は、引き続き構成または変更できます。  
  
## 使用例  
 次の例では、最初のメソッドはクエリを戻り値として返し、2 番目のメソッドはクエリを `out` パラメーターとして返します。  どちらの場合も返されるのはクエリであり、クエリ結果ではないことに注意してください。  
  
 [!code-cs[csProgGuideLINQ#80](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#80)]  
  
## コードのコンパイル  
  
-   .NET Framework Version 3.5 以降を対象とする [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] プロジェクトを作成します。  既定では、プロジェクトには、System.Core.dll への参照と、System.Linq 名前空間に対する `using` ディレクティブが含まれます。  
  
-   クラスを例のコードで置き換えます。  
  
-   F5 キーを押して、プログラムをコンパイルおよび実行します。  
  
-   任意のキーを押して、コンソール ウィンドウを終了します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)