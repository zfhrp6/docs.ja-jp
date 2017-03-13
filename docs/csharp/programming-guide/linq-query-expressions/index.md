---
redirect_url: /dotnet/articles/csharp/linq/index
caps.handback.revision: 21
---
# LINQ クエリ式 (C# プログラミング ガイド)
[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext-md.md)] は、クエリ機能を C\# 言語 \(および Visual Basic や場合によってその他の .NET 言語\) に直接統合する一連の技術の名前です。  [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] を使用すると、クエリは、クラス、メソッド、イベントなどと同じように、高度な機能を備えた言語構成要素になります。  
  
 クエリを記述する開発者の場合、[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] で最も違いを認識できる "統合言語" 部分はクエリ式です。  クエリ式は、C\# 3.0 で導入された宣言*クエリ構文*で記述します。  クエリ構文を使用すると、データ ソースに対する複雑なフィルター処理、順序付け、およびグループ化の操作を最小限のコードで実行できます。  同じ基本的なクエリ式のパターンを使用して、SQL データベース、[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] データセット、XML ドキュメントとストリーム、および .NET コレクション内のデータを照会および変換します。  
  
 完全なクエリ操作の例を次に示します。  完全な操作には、データ ソースの作成、クエリ式の定義、および `foreach` ステートメントでのクエリの実行が含まれます。  
  
 [!code-cs[csProgGuideLINQ#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
 C\# の [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] の基本的な事項の詳細については、「[Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)」を参照してください。  
  
## クエリ式の概要  
  
-   クエリ式を使用すると、[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 対応のデータ ソースのデータを照会および変換できます。  たとえば、1 つのクエリで、SQL データベースからデータを取得し、XML ストリームを出力として生成できます。  
  
-   クエリ式は多くの使い慣れた C\# 言語構成要素を使用するため、簡単に習得できます。  詳細については、「[Getting Started with LINQ in C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)」を参照してください。  
  
-   クエリ式の変数はすべて厳密に型指定されていますが、多くの場合、コンパイラが型を推論できるので、明示的に型を指定する必要はありません。  詳細については、「[Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。  
  
-   クエリは、`foreach` ステートメントでクエリ変数の反復処理が完了するまで実行されません。  詳細については、「[Introduction to LINQ Queries \(C\#\)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
-   コンパイル時に、C\# 仕様に規定された規則に従って、クエリ式が標準クエリ演算子メソッド呼び出しに変換されます。  クエリ構文を使用して表現できるクエリはすべて、メソッド構文を使用して表現することもできます。  ただし、多くの場合、クエリ構文はよりわかりやすく簡潔です。  詳細については、「[C\# 言語仕様](../../../csharp/language-reference/language-specification.md)」および「[Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。  
  
-   一般に、[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリを記述する場合、可能なときは常にクエリ構文を使用し、必要に応じてメソッド構文を使用することをお勧めします。  この 2 つの形式の間に意味および動作についての違いはありません。  クエリ式は多くの場合、メソッド構文で記述された同等の式に比べてわかりやすくなります。  
  
-   <xref:System.Linq.Enumerable.Count%2A> や <xref:System.Linq.Enumerable.Max%2A> などの一部のクエリ操作には同等のクエリ式の句がないため、メソッド呼び出しとして表現する必要があります。  メソッド構文は、さまざまな方法でクエリ構文と組み合わせることができます。  詳細については、「[Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。  
  
-   クエリ式をコンパイルすると、クエリを適用する対象の型に応じて式ツリーまたはデリゲートを作成できます。  <xref:System.Collections.Generic.IEnumerable%601> クエリをコンパイルすると、デリゲートが作成されます。  <xref:System.Linq.IQueryable> クエリおよび <xref:System.Linq.IQueryable%601> クエリをコンパイルすると式ツリーが作成されます。  詳細については、「[式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 クエリの追加情報および一般的なタスクのコード例に関するトピックを次の表に示します。  
  
|トピック|Description|  
|----------|-----------------|  
|[クエリ式の基本](../../../csharp/programming-guide/linq-query-expressions/query-expression-basics.md)|基本的なクエリの概念を紹介し、C\# クエリ構文の例について説明します。|  
|[方法 : C\# で LINQ クエリを作成する](../../../csharp/programming-guide/linq-query-expressions/how-to-write-linq-queries.md)|クエリ式のいくつかの基本的な種類の例について説明します。|  
|[方法 : クエリ式の例外を処理する](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)|例外をスローする可能性のあるコードを、いつどのようにしてクエリ式の外に移動するかを説明します。|  
|[How to: Populate Object Collections from Multiple Sources \(LINQ\)](../Topic/How%20to:%20Populate%20Object%20Collections%20from%20Multiple%20Sources%20\(LINQ\).md)|`select` ステートメントを使用して、異なるソースのデータを新しい型にマージする方法を示します。|  
|[方法: クエリ結果をグループ化する](../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)|`group` 句のさまざまな使用方法を示します。|  
|[方法: 入れ子になったグループを作成する](../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)|ネストされたグループの作成方法を示します。|  
|[方法: グループ化操作でサブクエリを実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)|クエリの部分式を新しいクエリのデータ ソースとして使用する方法を示します。|  
|[方法 : 連続するキーで結果をグループ化する](../../../csharp/programming-guide/linq-query-expressions/how-to-group-results-by-contiguous-keys.md)|ストリーミング データ ソースの操作をグループ化できるスレッド セーフの標準クエリ演算子を実装する方法を示します。|  
|[方法 : 実行時に述語フィルターを動的に指定する](../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)|任意の数の値を渡し、`where` 句で等価比較に使用する方法を示します。|  
|[方法 : クエリの結果をメモリに格納する](../../../csharp/programming-guide/linq-query-expressions/how-to-store-the-results-of-a-query-in-memory.md)|`foreach` ループを使用しないで、クエリの結果を具体化および格納する方法を示します。|  
|[方法 : メソッドからクエリを返す](../../../csharp/programming-guide/linq-query-expressions/how-to-return-a-query-from-a-method.md)|メソッドからクエリ変数を返す方法、およびそれらを入力パラメーターとしてメソッドに渡す方法を示します。|  
|[方法 : カスタム結合操作を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)|任意の種類の述語関数に基づいて結合演算を実行する方法を示します。|  
|[方法 : 複合キーを使用して結合する](../../../csharp/programming-guide/linq-query-expressions/how-to-join-by-using-composite-keys.md)|複数の一致キーに基づいて 2 つのソースを結合する方法を示します。|  
|[方法 : join 句の結果の順序を指定する](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)|結合演算で生成されたシーケンスの順序を指定する方法を示します。|  
|[方法 : 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)|[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] で内部結合を実行する方法を示します。|  
|[方法 : グループ化結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)|[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] でグループ化結合を生成する方法を示します。|  
|[方法 : 左外部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)|[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] で左外部結合を生成する方法を示します。|  
|[方法 : クエリ式の null 値を処理する](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-null-values-in-query-expressions.md)|[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリで null 値を処理する方法を示します。|  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Walkthrough: Writing Queries in C\#](../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Basic LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)   
 [Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)   
 [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [How Linq to Objects Queries Work \(Linq to Objects クエリの機能\)](http://go.microsoft.com/fwlink/?LinkId=112389)   
 [Reading and Writing Queries \(クエリの読み込みと作成\)](http://go.microsoft.com/fwlink/?LinkId=112391)   
 [What is a collection? \(コレクションとは\)](http://go.microsoft.com/fwlink/?LinkId=112394)   
 [Link to Everything: A List of LINQ Providers \(Link to Everything: LINQ プロバイダーの一覧\)](http://go.microsoft.com/fwlink/?LinkId=112411)