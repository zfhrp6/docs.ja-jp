---
title: "Introduction to LINQ Queries (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "deferred execution [LINQ]"
  - "LINQ, queries"
  - "LINQ, deferred execution"
  - "queries [LINQ], about LINQ queries"
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
caps.latest.revision: 47
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 45
---
# Introduction to LINQ Queries (C#)
*クエリ*とは、データ ソースからデータを取得するための式です。  クエリは通常、専用のクエリ言語で表されます。  これまでに、リレーショナル データベース用の SQL や XML 用の XQuery など、データ ソースの種類に合わせてさまざまな言語が開発されてきました。  このため、開発者は、サポートする必要のあるデータ ソースの種類やデータ形式ごとに、新しいクエリ言語を習得する必要がありました。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] は、さまざまな種類のデータ ソースやデータ形式のデータを操作するための一貫したモデルを提供することにより、この負担を軽減します。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリでは、操作の対象は常にオブジェクトになります。  共通の基本的なコーディング パターンを使用することで、XML ドキュメント、SQL データベース、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] データセット、.NET コレクション、および [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーを利用できる他の任意の形式のデータを照会したり変換したりできます。  
  
## クエリ操作の 3 つの手順  
 すべての [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリ操作は、次の 3 つの手順で構成されます。  
  
1.  データ ソースを取得します。  
  
2.  クエリを作成します。  
  
3.  クエリを実行します。  
  
 クエリ操作の 3 つの手順がソース コードでどのように表されるかを次の例に示します。  この例では、わかりやすくするために整数の配列をデータ ソースとして使用していますが、他のデータ ソースを使用する場合にも同じ概念が当てはまります。  このコードは、このトピックの残りの部分全体を通して参照されます。  
  
 [!code-cs[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 次の図は、クエリ操作全体を表しています。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] では、クエリの実行はクエリ自体とは別個のものです。つまり、クエリ変数を作成するだけでは、データは取得されません。  
  
 ![完全な LINQ クエリ操作](../../../../csharp/programming-guide/concepts/linq/media/linq-query.png "LINQ\_Query")  
  
## データ ソース  
 前の例では、データ ソースが配列であるため、暗黙的にジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスがサポートされます。  つまり、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] でクエリを実行できるということです。  クエリは `foreach` ステートメントで実行されますが、`foreach` には <xref:System.Collections.IEnumerable> または <xref:System.Collections.Generic.IEnumerable%601> が必要です。  <xref:System.Collections.Generic.IEnumerable%601> をサポートする型や、ジェネリック <xref:System.Linq.IQueryable%601> などの派生インターフェイスは、*クエリ可能型*と呼ばれます。  
  
 クエリ可能型は、変更や特別な処理を行わなくても、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] データ ソースとして使用できます。  ソース データがメモリ内にクエリ可能型として存在していない場合、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーは、そのような型としてソース データを表す必要があります。  たとえば、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] では、クエリ可能な <xref:System.Xml.Linq.XElement> 型に XML ドキュメントが読み込まれます。  
  
 [!code-cs[CsLINQGettingStarted#2](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_2.cs)]  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] では、まず、デザイン時に手動で、または [Object Relational Designer \(O\/R Designer\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2) を使用して、オブジェクト リレーショナル マッピングを作成します。  オブジェクトに対するクエリを記述すると、実行時には、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] によってデータベースとの通信が処理されます。  次の例では、`Customers` がデータベース内の特定のテーブルを表し、クエリ結果の型 <xref:System.Linq.IQueryable%601> が <xref:System.Collections.Generic.IEnumerable%601> から派生しています。  
  
```c#  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
  
```  
  
 それぞれの種類のデータ ソースを作成する方法の詳細については、対応する [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーのドキュメントを参照してください。  ただし、基本的な規則は非常に単純です。[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] データ ソースは、ジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイス、またはこれを継承するインターフェイスをサポートする任意のオブジェクトです。  
  
> [!NOTE]
>  非ジェネリック <xref:System.Collections.IEnumerable> インターフェイスをサポートする <xref:System.Collections.ArrayList> などの型も、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] データ ソースとして使用できます。  詳細については、「[How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)」を参照してください。  
  
##  <a name="query"></a> クエリ  
 クエリでは、データ ソースからどのような情報を取得するかを指定します。  オプションとして、情報が返される前に、その情報を並べ替え、グループ化し、構造化する方法を指定することもできます。  クエリはクエリ変数に格納され、クエリ式で初期化されます。  クエリを簡単に記述できるようにするために、C\# に新しいクエリ構文が導入されています。  
  
 前の例のクエリでは、整数の配列からすべての偶数が返されます。  クエリ式には、`from`、`where`、および `select` の 3 つの句が含まれています \(SQL に詳しい方は、句の順番が SQL での順番とは逆になっていることに気付かれると思います\)。`from` 句はデータ ソースを指定し、`where` 句はフィルターを適用し、`select` 句は返される要素の種類を指定します。  これらのクエリ句およびその他のクエリ句の詳細については、「[LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)」で説明しています。  今の段階で重要な点は、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] では、クエリ変数自体は何も処理を行わず、データを返さないという点です。  この時点では、後でクエリが実行されるときに結果の生成に必要となる情報が格納されるだけです。  背後でどのようにクエリが構築されるかについては、「[Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。  
  
> [!NOTE]
>  クエリは、メソッド構文を使用して表すこともできます。  詳細については、「[Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。  
  
## クエリの実行  
  
### 遅延実行  
 先に説明したように、クエリ変数自体が行うのはクエリ コマンドの格納のみです。  実際のクエリの実行は、`foreach` ステートメントでクエリ変数が反復処理されるまで延期されます。  この概念を*遅延実行*と呼びます。遅延実行の例を次に示します。  
  
 [!code-cs[csLinqGettingStarted#4](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_3.cs)]  
  
 `foreach` ステートメントでは、クエリ結果の取得も行われます。  たとえば、前のクエリでは、返されるシーケンスの各値が反復変数 `num` に \(一度に 1 つずつ\) 格納されます。  
  
 クエリ変数自体にはクエリ結果は格納されないので、必要に応じて何度でもクエリを実行できます。  たとえば、別のアプリケーションによって頻繁に更新されるデータベースがあるとします。  自分のアプリケーションでは、最新のデータを取得するクエリを 1 つ作成し、それを一定の間隔で繰り返し実行することで、毎回異なる結果を取得できます。  
  
### 即時実行の強制  
 一連のソース要素に対して集計関数を実行するクエリでは、最初にそれらの要素を反復処理する必要があります。  このようなクエリには、`Count`、`Max`、`Average`、`First` などがあります。  これらのクエリでは、明示的に `foreach` ステートメントを使用しなくても同等の処理が実行されます。これは、結果を返すためにクエリ自体が `foreach` を使用する必要があるからです。  これらの種類のクエリでは、`IEnumerable` コレクションではなく、単一の値が返されることにも注意してください。  次のクエリは、ソース配列に含まれている偶数の数を返します。  
  
 [!code-cs[csLinqGettingStarted#5](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_4.cs)]  
  
 クエリの即時実行を強制し、その結果をキャッシュするには、<xref:System.Linq.Enumerable.ToList%2A> メソッドまたは <xref:System.Linq.Enumerable.ToArray%2A> メソッドを呼び出します。  
  
 [!code-cs[csLinqGettingStarted#6](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_5.cs)]  
  
 クエリ式の直後に `foreach` ループを配置することでも実行を強制できます。  ただし、`ToList` または `ToArray` を呼び出した場合は、単一のコレクション オブジェクトにすべてのデータをキャッシュする処理も行われます。  
  
## 参照  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [LINQ のサンプル](../Topic/LINQ%20Samples.md)   
 [O\/R Designer Overview](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [foreach、in](../../../../csharp/language-reference/keywords/foreach-in.md)   
 [クエリ キーワード \(LINQ\)](../../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ and Deferred Execution Video \(LINQ と遅延実行のビデオ\)](http://go.microsoft.com/fwlink/?LinkId=112414)