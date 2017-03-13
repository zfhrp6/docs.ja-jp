---
redirect_url: /dotnet/articles/csharp/linq/group-query-results
caps.handback.revision: 19
---
# 方法: クエリ結果をグループ化する (C# プログラミング ガイド)
グループ化は、[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] の最も強力な機能の 1 つです。  以下の例では、データをグループ化する各種の方法を示します。  
  
-   1 つのプロパティ  
  
-   文字列プロパティの先頭の文字  
  
-   計算済みの数値の範囲  
  
-   ブール型の述語またはその他の式  
  
-   複合キー  
  
 また、最後の 2 つのクエリでは、学生の姓と名のみを含む新しい匿名型に結果が格納されます。  詳細については、「[group 句](../../../csharp/language-reference/keywords/group-clause.md)」を参照してください。  
  
## 使用例  
 このトピックのすべての例で、次のヘルパー クラスとデータ ソースが使用されています。  
  
 [!code-cs[csProgGuideLINQ#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_1.cs)]  
  
## 使用例  
 グループ化キーとして要素の 1 つのプロパティを使用してソース要素をグループ化する方法を次の例に示します。  この例では、キーは学生の姓である `string` です。  部分文字列をキーとして使用することもできます。  このグループ化操作では、型の既定の等値比較子が使用されています。  
  
 `StudentClass` クラスに次のメソッドを貼り付けます。  `Main` メソッド内の呼び出しステートメントを `sc.GroupBySingleProperty()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_2.cs)]  
  
## 使用例  
 グループ化キーとしてオブジェクトのプロパティ以外のものを使用してソース要素をグループ化する方法を次の例に示します。  この例では、キーは学生の姓の最初の文字です。  
  
 `StudentClass` クラスに次のメソッドを貼り付けます。  `Main` メソッド内の呼び出しステートメントを `sc.GroupBySubstring()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_3.cs)]  
  
## 使用例  
 グループ化キーとして数値の範囲を使用してソース要素をグループ化する方法を次の例に示します。  このクエリでは、姓と名および学生が属するパーセンタイルの範囲のみを含む匿名型に結果が格納されます。  結果を表示するのに完全な `Student` オブジェクトを使用する必要がないため、匿名型が使用されています。  `GetPercentile` は、学生の平均点に基づいてパーセンタイルを計算するヘルパー関数です。  メソッドは 0 ～ 10 の整数を返します。  
  
 [!code-cs[csProgGuideLINQ#50](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_4.cs)]  
  
 `StudentClass` クラスに次のメソッドを貼り付けます。  `Main` メソッド内の呼び出しステートメントを `sc.GroupByRange()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_5.cs)]  
  
## 使用例  
 ブール型の比較式を使用してソース要素をグループ化する方法を次の例に示します。  この例では、ブール式を使用して、学生の試験の平均点が 75 点より高いかどうかを調べています。  前の例と同様、完全なソース要素は必要ないため、結果は匿名型に格納されます。  匿名型のプロパティは `Key` メンバーのプロパティになること、およびクエリの実行時に名前でアクセスできることに注意してください。  
  
 `StudentClass` クラスに次のメソッドを貼り付けます。  `Main` メソッド内の呼び出しステートメントを `sc.GroupByBoolean()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_6.cs)]  
  
## 使用例  
 匿名型を使用して複数の値を含むキーをカプセル化する方法を次の例に示します。  この例では、最初のキー値は学生の姓の最初の文字です。  2 番目のキー値は、最初の試験で学生が 85 点を超えたかどうかを示すブール値です。  キーとして任意のプロパティを使用してグループを並べ替えることができます。  
  
 `StudentClass` クラスに次のメソッドを貼り付けます。  `Main` メソッド内の呼び出しステートメントを `sc.GroupByCompositeKey()` に変更します。  
  
 [!code-cs[csProgGuideLINQ#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-group-query-results_7.cs)]  
  
## コードのコンパイル  
 テストする各メソッドをコピーし、`StudentClass` クラスに貼り付けます。  メソッドの呼び出しステートメントを `Main` メソッドに追加し、F5 キーを押します。  
  
 独自のアプリケーションに合わせてこれらのメソッドを変更する場合、LINQ には [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の Version 3.5 または 4 が必要であること、および System.Core.dll への参照と System.Linq の using ディレクティブをプロジェクトに含める必要があることに注意してください。  LINQ to SQL、LINQ to XML、および LINQ to DataSet の型を使用するには、追加の using ディレクティブと参照も必要です。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 <xref:System.Linq.Enumerable.GroupBy%2A>   
 <xref:System.Linq.IGrouping%602>   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group 句](../../../csharp/language-reference/keywords/group-clause.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [方法: グループ化操作でサブクエリを実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)   
 [方法: 入れ子になったグループを作成する](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)   
 [Grouping Data](../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)