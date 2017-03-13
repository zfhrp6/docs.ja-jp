---
redirect_url: /dotnet/articles/csharp/linq/query-expression-basics
caps.handback.revision: 32
---
# クエリ式の基本 (C# プログラミング ガイド)
## クエリの機能と処理内容  
 *クエリ*は、特定のデータ ソースから取得するデータ、および返されるデータの形状と構成を記述する一連の命令です。  クエリは、生成される結果とは区別されるものです。  
  
 通常、ソース データは同じ種類の要素のシーケンスとして論理的に編成されます。  SQL データベース テーブルには行のシーケンスが格納されます。  同様に、[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] <xref:System.Data.DataTable> には <xref:System.Data.DataRow> オブジェクトのシーケンスが格納されます。  XML ファイルには、XML 要素の "シーケンス" があります \(ただし、これらの XML 要素はツリー構造で階層として編成されます\)。  インメモリ コレクションにはオブジェクトのシーケンスが格納されます。  
  
 アプリケーションの視点からは、元のソース データの種類と構成は重要ではありません。  アプリケーションは、常にソース データを <xref:System.Collections.Generic.IEnumerable%601> コレクションまたは <xref:System.Linq.IQueryable%601> コレクションと見なします。  [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] では、ソース データは `IEnumerable`\<<xref:System.Xml.Linq.XElement>\> として表示されます。  [!INCLUDE[linq_dataset](../../../csharp/programming-guide/linq-query-expressions/includes/linq-dataset-md.md)] では、`IEnumerable`\<<xref:System.Data.DataRow>\> になります。  [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] では、SQL テーブル内のデータを表すために定義したカスタム オブジェクトの `IEnumerable` または `IQueryable` になります。  
  
 このソース シーケンスにより、クエリは次の 3 つのいずれかの処理を実行できます。  
  
-   要素のサブセットを取得し、個別の要素を変更せずに新しいシーケンスを生成します。  次の例に示すように、クエリは返されたシーケンスをさまざまな方法で並べ替えまたはグループ化できます \(`scores` は `int[]` であると想定しています\)。  
  
     [!code-cs[csrefQueryExpBasics#45](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_1.cs)]  
  
-   前の例のように要素のシーケンスを取得しますが、それらを新しい種類のオブジェクトに変換します。  たとえば、クエリはデータ ソース内の特定の顧客レコードから姓だけを取得できます。  完全なレコードを取得し、そのレコードを使用して別のインメモリ オブジェクトの種類を作成したり、最終的な結果シーケンスを生成する前に XML データを作成したりすることもできます。  `int` から `string` への変換の例を次に示します。  新しい種類の `highScoresQuery` に注意してください。  
  
     [!code-cs[csrefQueryExpBasics#46](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_2.cs)]  
  
-   次のような、ソース データに関するシングルトン値を取得します。  
  
    -   特定の条件に一致する要素の数。  
  
    -   最大値または最小値を持つ要素。  
  
    -   条件に一致する最初の要素、または指定した一連の要素内の特定の値の合計。  たとえば、次のクエリは `scores` 整数配列から 80 を超える得点の数を返します。  
  
     [!code-cs[csrefQueryExpBasics#47](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_3.cs)]  
  
     前の例では、`Count` メソッドの呼び出しの前に、クエリ式をかっこで囲んでいました。  これは、具体的な結果を格納する新しい変数を使用して表すこともできます。  この方法は、クエリを格納する変数と結果を格納するクエリを区別できるため、読みやすくなります。  
  
     [!code-cs[csrefQueryExpBasics#48](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_4.cs)]  
  
 前の例では、クエリは `Count` の呼び出しで実行されます。これは、`highScoresQuery` で返される要素の数を判断するために、`Count` は結果を反復処理する必要があるためです。  
  
## クエリ式とは  
 *クエリ式*は、クエリ構文で表されるクエリです。  クエリ式は最上位の言語構成要素です。  クエリ式は他の式と同じであり、C\# 式が有効なすべてのコンテキストで使用できます。  クエリ式は、SQL または XQuery に似た宣言構文で記述された一連の句で構成されます。  各句には 1 つ以上の C\# 式が含まれ、これらの式自体がクエリ式になるか、クエリ式を含みます。  
  
 クエリ式は [from](../../../csharp/language-reference/keywords/from-clause.md) 句で始まり、最後には [select](../../../csharp/language-reference/keywords/select-clause.md) 句または [group](../../../csharp/language-reference/keywords/group-clause.md) 句を指定する必要があります。  最初の `from` 句と最後の `select` 句または `group` 句の間には、1 つ以上のオプションの句として、[where](../../../csharp/language-reference/keywords/where-clause.md)、[orderby](../../../csharp/language-reference/keywords/orderby-clause.md)、[join](../../../csharp/language-reference/keywords/join-clause.md)、[let](../../../csharp/language-reference/keywords/let-clause.md)、および追加の [from](../../../csharp/language-reference/keywords/from-clause.md) の各句を含めることができます。  [into](../../../csharp/language-reference/keywords/into.md) キーワードを使用して、`join` 句または `group` 句の結果を有効にし、同じクエリ式内の別のクエリ句のソースとして使用することもできます。  
  
### クエリ変数  
 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] では、クエリ変数は、クエリの*結果*ではなく、*クエリ*を格納する変数です。具体的には、クエリ変数は常に列挙型で、`foreach` ステートメントまたは `IEnumerator.MoveNext` メソッドの直接呼び出しで反復処理されるときの要素のシーケンスを生成します。  
  
 1 つのデータ ソース、1 つのフィルター処理句、および 1 つの並べ替え句があり、ソース要素の変換は行われない単純なクエリを次のコード例に示します。  `select` 句によりクエリが終了します。  
  
 [!code-cs[csrefQueryExpBasics#49](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_5.cs)]  
  
 前の例では、`scoreQuery` は*クエリ変数*です。単に*クエリ*と呼ばれることもあります。  クエリ変数には、`foreach` ループで生成される実際の結果データは格納されません。  `foreach` ステートメントを実行すると、クエリ変数 `scoreQuery` ではクエリ結果は返されません。  クエリ結果は反復変数 `testScore` で返されます。  `scoreQuery` 変数は、2 番目の `foreach` ループで反復処理できます。  変数またはデータ ソースが変更されない限り、同じ結果が生成されます。  
  
 クエリ変数には、クエリ構文またはメソッド構文で表されるクエリ、またはその 2 つの組み合わせを格納できます。  次の例では、`queryMajorCities` と `queryMajorCities2` はどちらもクエリ変数です。  
  
 [!code-cs[csrefQueryExpBasics#50](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_6.cs)]  
  
 一方、クエリで初期化されても、クエリ変数ではない変数を次の 2 つの例に示します。  これらの変数は結果を格納するため、クエリ変数ではありません。  
  
 [!code-cs[csrefQueryExpBasics#51](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_7.cs)]  
  
> [!NOTE]
>  [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] のマニュアルでは、クエリを格納する変数にはその名前の一部として "query" という単語が含まれています。  実際の結果を格納する変数には、名前に "query" はありません。  
  
 クエリを表すさまざまな方法の詳細については、「[Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。  
  
#### クエリ変数の明示的および暗黙的な型指定  
 通常、このドキュメントでは、クエリ変数と [select 句](../../../csharp/language-reference/keywords/select-clause.md)の間の型の関係を示すために、明示的な型のクエリ変数を使用します。  ただし、[var](../../../csharp/language-reference/keywords/var.md) キーワードを使用して、コンパイル時にクエリ変数 \(またはその他のローカル変数\) の型を推論するようにコンパイラに指示することもできます。  たとえば、このトピックで示したクエリの例を、暗黙的な型指定を使用して表すこともできます。  
  
 [!code-cs[csrefQueryExpBasics#52](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_8.cs)]  
  
 詳細については、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」および「[Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。  
  
### クエリ式の開始  
 クエリ式は、`from` 句で始める必要があります。  クエリ式は、範囲変数と共にデータ ソースを指定します。  範囲変数は、ソース シーケンスが走査されているときに、ソース シーケンス内の後続の各要素を表します。  範囲変数は、データ ソース内の要素の型に基づいて厳密に型指定されます。  次の例では、`countries` は `Country` オブジェクトの配列であるため、範囲変数は `Country` としても型指定されます。  範囲変数は厳密に型指定されるため、ドット演算子を使用して型の使用可能なメンバーにアクセスできます。  
  
 [!code-cs[csrefQueryExpBasics#53](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_9.cs)]  
  
 範囲変数は、クエリがセミコロンまたは*継続*句で終了するまでスコープ内に存在します。  
  
 クエリ式には複数の `from` 句を含めることもできます。  ソース シーケンス内の各要素自体がコレクションの場合、またはコレクションを含む場合、追加の `from` 句を使用します。  たとえば、`Country` オブジェクトのコレクションがあり、それぞれに `Cities` という名前の `City` オブジェクトのコレクションが含まれるとします。  各 `Country` 内の `City` オブジェクトを照会するには、次に示すように 2 つの `from` 句を使用します。  
  
 [!code-cs[csrefQueryExpBasics#54](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_10.cs)]  
  
 詳細については、「[from 句](../../../csharp/language-reference/keywords/from-clause.md)」を参照してください。  
  
### クエリ式の終了  
 クエリ式の末尾は `select` 句または `group` 句とする必要があります。  
  
#### group 句  
 指定したキー別に構成されるグループのシーケンスを生成するには、`group` 句を使用します。  キーには任意のデータ型を指定できます。  たとえば、次のクエリは 1 つ以上の `Country` オブジェクトを含み、キーが `char` 値のグループのシーケンスを作成します。  
  
 [!code-cs[csrefQueryExpBasics#55](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_11.cs)]  
  
 グループ化の詳細については、「[group 句](../../../csharp/language-reference/keywords/group-clause.md)」を参照してください。  
  
#### select 句  
 その他のすべての種類のシーケンスを生成するには、`select` 句を使用します。  単純な `select` 句は、データ ソースに含まれるオブジェクトと同じ種類のオブジェクトのシーケンスを生成します。  この例では、データ ソースには `Country` オブジェクトが含まれます。  `orderby` 句は要素を新しい順序に並べ替え、`select` 句は並べ替えられた `Country` オブジェクトのシーケンスを生成します。  
  
 [!code-cs[csrefQueryExpBasics#56](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_12.cs)]  
  
 `select` 句を使用すると、ソース データを新しい種類のシーケンスに変換できます。  この変換は*射影*と呼ばれることもあります。  次の例では、`select` 句は、元の要素内のフィールドのサブセットのみを含む匿名型のシーケンスを*射影*します。  新しいオブジェクトは、オブジェクト初期化子を使用して初期化されます。  
  
 [!code-cs[csrefQueryExpBasics#57](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_13.cs)]  
  
 `select` 句を使用してソース データを変換するすべての方法の詳細については、「[select 句](../../../csharp/language-reference/keywords/select-clause.md)」を参照してください。  
  
#### "into" を使用した継続  
 `select` 句または `group` 句で `into` キーワードを使用すると、クエリを格納する一時識別子を作成できます。  これは、グループ化または選択操作の後に、クエリで追加のクエリ操作を実行する必要がある場合に行います。  次の例では、1000 万の範囲内の人口に従って `countries` がグループ化されます。  これらのグループが作成された後、追加の句を使用して一部のグループを除外し、グループを昇順で並べ替えます。  この追加操作を実行するには、`countryGroup` で表される継続が必要です。  
  
 [!code-cs[csrefQueryExpBasics#58](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_14.cs)]  
  
 詳細については、「[into](../../../csharp/language-reference/keywords/into.md)」を参照してください。  
  
### フィルター処理、並べ替え、および結合  
 先頭の `from` 句と末尾の `select` 句または `group` 句の間では、その他の句 \(`where`、`join`、`orderby`、`from`、`let`\) はすべて省略可能です。  省略可能な句は、クエリ本文でゼロ回または複数回使用できます。  
  
#### where 句  
 1 つ以上の述語式に基づいてソース データから要素を除外するには、`where` 句を使用します。  次の例の `where` 句には、2 つの述語があります。  
  
 [!code-cs[csrefQueryExpBasics#59](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_15.cs)]  
  
 詳細については、「[where 句](../../../csharp/language-reference/keywords/where-clause.md)」を参照してください。  
  
#### orderby 句  
 結果を昇順または降順で並べ替えるには、`orderby` 句を使用します。  2 番目の並べ替えを指定することもできます。  `Area` プロパティを使用して `country` オブジェクトで 1 番目の並べ替えを実行する例を次に示します。  次に、`Population` プロパティを使用して 2 番目の並べ替えを実行します。  
  
 [!code-cs[csrefQueryExpBasics#60](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_16.cs)]  
  
 `ascending` キーワードは省略可能です。順序を指定しないと、昇順が既定の並べ替え順序になります。  詳細については、「[orderby 句](../../../csharp/language-reference/keywords/orderby-clause.md)」を参照してください。  
  
#### join 句  
 各要素内の指定されたキーの間の等価比較に基づいて、あるデータ ソースの要素と別のデータ ソースの要素を関連付けるか、または結合するには、`join` 句を使用します。  [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] では、結合操作は要素の型が異なるオブジェクトのシーケンスで実行されます。  2 つのシーケンスを結合した後、`select` ステートメントまたは `group` ステートメントを使用して、出力シーケンスに格納される要素を指定する必要があります。  匿名型を使用して、関連する要素の各セットのプロパティを出力シーケンスの新しい型に結合することもできます。  `Category` プロパティが `categories` 文字列配列内のカテゴリの 1 つと一致する `prod` オブジェクトを関連付ける例を次に示します。  `Category` が `categories` 内の文字列と一致しない製品は除外されます。  `select` ステートメントは、プロパティが `cat` と `prod` の両方から取得される新しい型を射影します。  
  
 [!code-cs[csrefQueryExpBasics#61](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_17.cs)]  
  
 [into](../../../csharp/language-reference/keywords/into.md) キーワードを使用して、`join` 操作の結果を一時変数に格納することで、グループ結合を実行することもできます。  詳細については、「[join 句](../../../csharp/language-reference/keywords/join-clause.md)」を参照してください。  
  
#### let 句  
 新しい範囲変数でのメソッド呼び出しなど、式の結果を格納するには `let` 句を使用します。  次の例では、範囲変数 `firstName` には、`Split` から返される文字列配列の最初の要素が格納されます。  
  
 [!code-cs[csrefQueryExpBasics#62](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_18.cs)]  
  
 詳細については、「[let 句](../../../csharp/language-reference/keywords/let-clause.md)」を参照してください。  
  
### クエリ式内のサブクエリ  
 クエリ式自体にクエリ式を含めることができます。これは、*サブクエリ*とも呼ばれます。  各サブクエリは独自の `from` 句で始まります。これは、必ずしも最初の `from` 句の同じデータ ソースを指すとは限りません。  たとえば、次のクエリは、グループ化操作の結果を取得するために select ステートメントで使用されるクエリ式を示しています。  
  
 [!code-cs[csrefQueryExpBasics#63](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/query-expression-basics_19.cs)]  
  
 詳細については、「[方法: グループ化操作でサブクエリを実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [クエリ キーワード \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)