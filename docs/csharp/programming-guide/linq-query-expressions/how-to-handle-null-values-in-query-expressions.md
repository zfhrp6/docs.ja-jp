---
redirect_url: /dotnet/articles/csharp/linq/handle-null-values-in-query-expressions
caps.handback.revision: 6
---
# 方法 : クエリ式の null 値を処理する (C# プログラミング ガイド)
この例は、ソース コレクション内の null である可能性がある値を処理する方法を示しています。  <xref:System.Collections.Generic.IEnumerable%601> などのオブジェクト コレクションには、値が [null](../../../csharp/language-reference/keywords/null.md) の要素を含めることができます。  ソース コレクションが null である場合や値が null の要素がソース コレクションに含まれる場合にクエリが null 値を処理していなければ、クエリを実行すると <xref:System.NullReferenceException> がスローされます。  
  
## 使用例  
 次の例に示すように、防御的にコーディングすることにより、null 参照の例外を回避できます。  
  
 [!code-cs[csProgGuideLINQ#82](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#82)]  
  
 この例では、`where` 句がカテゴリ シーケンスに含まれるすべての null 要素をフィルターで除外します。  この手法は join 句での null チェックとは無関係です。  この例の null を含む条件式は正常に機能します。`Products.CategoryID` は `int?` 型であり、この型は `Nullable<int>` の省略表現であるためです。  
  
## 使用例  
 join 句では、比較キーのうちの 1 つだけが null 許容値型である場合、残りのキーをクエリ式で null 許容型にキャストできます。  次の例の `EmployeeID` は、`int?` 型の値を含む列とします。  
  
 [!code-cs[csProgGuideLINQ#83](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#83)]  
  
## 参照  
 <xref:System.Nullable%601>   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)