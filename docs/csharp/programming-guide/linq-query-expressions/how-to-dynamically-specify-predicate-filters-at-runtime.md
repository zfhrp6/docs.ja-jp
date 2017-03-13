---
redirect_url: /dotnet/articles/csharp/linq/dynamically-specify-predicate-filters-at-runtime
caps.handback.revision: 22
---
# 方法 : 実行時に述語フィルターを動的に指定する (C# プログラミング ガイド)
実行時まで、`where` 句でソース要素に適用する必要のある述語の数がわからない場合があります。  複数の述語フィルターを動的に指定する 1 つの方法は、次の例に示すように <xref:System.Linq.Enumerable.Contains%2A> メソッドを使用することです。  この例は、2 つの方法で構築されています。  まず、プログラム内で指定された値にフィルターをかけてプロジェクトを実行します。  次に、実行時に指定された入力を使用してもう一度プロジェクトを実行します。  
  
### Contains メソッドを使用してフィルターをかけるには  
  
1.  Visual Studio で、新しいコンソール アプリケーションを開きます。  これに「`PredicateFilters`」という名前を付けます。  
  
2.  「[方法 : オブジェクトのコレクションを照会する](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)」から `StudentClass` クラスをコピーし、`Program` クラスの下の `PredicateFilters` 名前空間に貼り付けます。  `StudentClass` は、`Student` オブジェクトのリストを提供します。  
  
3.  `StudentClass` の `Main` メソッドをコメント アウトします。  
  
4.  `Program` クラスを次のコードで置き換えます。  
  
     [!code-cs[csProgGuideLINQ#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  `ids` の宣言の下で、`DynamicPredicates` クラスの `Main` メソッドに次のコード行を追加します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
6.  F5 キーを押してプロジェクトを実行します。  
  
7.  次の出力が \[コマンド プロンプト\] ウィンドウに表示されます。  
  
     "Garcia: 114"  
  
     "O'Donnell: 112"  
  
     "Omelchenko: 111"  
  
8.  次の手順ではもう一度プロジェクトを実行しますが、今回は配列 `ids` ではなく、実行時に指定された入力を使用します。  **ソリューション エクスプローラー**で、**\[PredicateFilters\]** を右クリックし、**\[プロパティ\]** をクリックします。  
  
9. **\[デバッグ\]** タブをクリックします。  
  
10. **\[コマンド ライン引数\]** ウィンドウで、「122」、「117」、「120」、「115」をスペースで区切って入力します \(`122 117 120 115`\)。  プロジェクトを実行すると、これらの値は、`Main` メソッドのパラメーターである `args` の要素になります。  
  
11. `Main` メソッドで `QueryByID(ids)` を `QueryByID(args)` に変更します。  
  
12. F5 キーを押してプロジェクトを実行します。  
  
13. 次の出力が \[コマンド プロンプト\] ウィンドウに表示されます。  
  
     "Adams: 120"  
  
     "Feng: 117"  
  
     "Garcia: 115"  
  
     "Tucker: 122"  
  
### switch ステートメントを使用してフィルターをかけるには  
  
1.  `switch` ステートメントを使用すると、定義済みの代替クエリから選択できます。  次の例では、実行時に指定された学年に応じて、異なる `where` 句を `studentQuery` で使用します。  
  
2.  次のメソッドをコピーし、`DynamicPredicates` クラスに貼り付けます。  
  
     [!code-cs[csProgGuideLINQ#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  **\[コマンド ライン引数\]** ウィンドウで、前の手順の ID 番号を 1 ～ 4 の整数値に置き換えます。  
  
4.  `Main` メソッドで、`QueryByID` への呼び出しを次の呼び出しに置き換えます。この呼び出しは、`args` 配列の最初の要素をその引数として渡します \(`QueryByYear(args[0])`\)。  
  
5.  F5 キーを押してプロジェクトを実行します。  
  
### このメソッドを独自のアプリケーションで使用するには  
  
-   独自のアプリケーションに合わせてこのメソッドを変更する場合、LINQ には [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Version 3.5 または 4 が必要であること、および System.Core.dll への参照と `System.Linq` の `using` ディレクティブをプロジェクトに含める必要があることに注意してください。  LINQ to SQL、LINQ to XML、および LINQ to DataSet の型を使用するには、追加の `using` ディレクティブと参照も必要です。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [where 句](../../../csharp/language-reference/keywords/where-clause.md)