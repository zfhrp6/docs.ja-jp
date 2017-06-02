---
title: "Queries in LINQ to DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Queries in LINQ to DataSet
クエリは、データ ソースからデータを取得する式です。  一般に、クエリは専用のクエリ言語で表現されます。たとえば、リレーショナル データベースであれば SQL、XML であれば XQuery が使用されます。  そのため、開発者はクエリの対象となるデータ ソースやデータ形式ごとに新しいクエリ言語を習得する必要があります。  [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] は、データ ソースや形式の違いを意識せずにデータを扱うことのできる、より簡素化された一貫したモデルを提供します。  [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] クエリでは、常にプログラミング オブジェクトを操作することになります。  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] のクエリ操作は、データ ソースを取得し、クエリを作成して、クエリを実行するという 3 つのアクションから成ります。  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] を介したクエリは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスを実装するデータ ソースに対して行うことができます。  <xref:System.Data.DataTable> で <xref:System.Data.DataTableExtensions.AsEnumerable%2A> を呼び出すと、ジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するオブジェクトが返されます。このオブジェクトが、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリのデータ ソースとして機能します。  
  
 クエリでは、データ ソースから取得する情報を正確に指定できます。  また、並べ替え、グループ化、整形方法を指定して情報を取得することもできます。  [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] では、クエリが変数に格納されます。  一連の値を返すようにクエリを設計する場合、クエリ変数そのものが列挙可能な型であることが必要です。  このクエリ変数は、クエリの情報を保存するだけで、なんらかのアクションを実行したり、データを返したりすることはありません。  クエリを作成した後、データを取得するには、そのクエリを実行する必要があります。  
  
 一連の値を返すクエリでは、クエリ変数そのものはクエリ結果を保持しません。クエリ変数には、クエリのコマンドが格納されるだけです。  クエリ変数が `foreach` ループまたは `For Each` ループで反復処理されるまで、クエリは実行されません。  これを*遅延実行*と呼びます。つまり、作成されたクエリはすぐには実行されません。  これは、任意のタイミングでクエリを実行できるということを意味します。  これは、たとえば他のアプリケーションによって更新されるデータベースがある場合に便利です。  アプリケーションで、最新情報を取得するクエリを作成し、それを繰り返し実行することにより、更新のたびに最新の情報を取得できます。  
  
 遅延実行によって一連の値を返すクエリとは対照的に、シングルトン値を返すクエリは直ちに実行されます。  シングルトン クエリの例としては、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.First%2A> があります。  これらのシングルトン クエリは、結果を計算するためにはクエリ結果が必要であるため、直ちに実行されます。  たとえば、クエリ結果の平均を求めるためには、クエリを実行して、平均関数に入力データを与える必要があります。  シングルトン値を生成しないクエリでも、<xref:System.Linq.Enumerable.ToList%2A> メソッドまたは <xref:System.Linq.Enumerable.ToArray%2A> メソッドを使用することによって、即時実行を強制できます。  即時実行を強制するこの手法は、クエリの結果をキャッシュする場合などに使用すると効果的です。  クエリの遅延実行と即時実行の詳細については、「[Getting Started with LINQ](http://msdn.microsoft.com/ja-jp/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)」を参照してください。  
  
## クエリ  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリは、クエリ式の構文とメソッド ベースのクエリ構文という 2 とおりの構文を使って作成できます。  
  
### クエリ式の構文  
 クエリ式は宣言型のクエリ構文です。  開発者は SQL に似た構文形式を C\# または Visual Basic で用いてクエリを作成できます。  クエリ式の構文を使用することにより、フィルター、並べ替え、グループ化など、データ ソースに対するきわめて複雑な処理を最小限のコードで実行できます。  詳細については、「[LINQ クエリ式](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)」および「[基本的なクエリ操作 \(Visual Basic\)](../Topic/Basic%20Query%20Operations%20\(Visual%20Basic\).md)」を参照してください。  
  
 クエリ式の構文は、C\# 3.0 および [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)] で新たに導入されたものです。  ただし、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の共通言語ランタイム \(CLR\) は、クエリ式の構文そのものを理解することはできません。  そのため、クエリ式はコンパイル時に、CLR が理解できる形式 \(メソッド呼び出し\) へと変換されます。  これらのメソッドを*標準クエリ演算子*といいます。  開発者は、クエリ構文を使う代わりに、メソッド構文を使ってそれらを直接呼び出すこともできます。  詳細については、「[Query Syntax and Method Syntax in LINQ](../Topic/Query%20Syntax%20and%20Method%20Syntax%20in%20LINQ%20\(C%23\).md)」を参照してください。  標準クエリ演算子の使用方法の詳細については、「[NOT IN BUILD: LINQ General Programming Guide](http://msdn.microsoft.com/ja-jp/609c7a6b-cbdd-429d-99f3-78d13d3bc049)」を参照してください。  
  
 次の例では、<xref:System.Linq.Enumerable.Select%2A> を使用して `Product` テーブルからすべての行を取得し、製品名を表示しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### メソッド ベースのクエリ構文  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリを作成するもう 1 つの方法として、メソッド ベースのクエリがあります。  メソッド ベースのクエリ構文は、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] の演算子メソッドを、ラムダ式をパラメーターとして直接順次呼び出すものです。  詳細については、「[ラムダ式](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md)」を参照してください。  
  
 次の例では、<xref:System.Linq.Enumerable.Select%2A> を使用して `Product` テーブルからすべての行を取得し、製品名を表示しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## クエリの作成  
 前述したように、一連の値を返すように設計されたクエリでは、クエリ変数自体にはクエリ コマンドのみが格納されます。  クエリに即時実行を促すメソッドが含まれていなければ、`foreach` ループまたは `For Each` ループでクエリ変数を反復処理するまで、実際にはクエリは実行されません。  遅延実行により、複数のクエリを組み合わせたり、クエリを拡張したりすることが可能となります。  クエリを拡張して新しい操作を追加すると、その変更が最終的な実行時に反映されます。  次の例の最初のクエリでは、すべての製品が返されます。  2 つ目のクエリでは、サイズが "L" のすべての製品を返すように、`Where` を使って 1 つ目のクエリを拡張しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 クエリを拡張した後は、追加のクエリを作成することはできません。それ以降のすべてのクエリでは、インメモリの [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 演算子が使用されます。  クエリが実行されるのは、`foreach` ステートメントまたは `For Each` ステートメントでクエリ変数を反復処理したときか、即時実行を促すいずれかの [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 変換演算子を呼び出した場合です。  即時実行を促す演算子としては、<xref:System.Linq.Enumerable.ToList%2A>、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToLookup%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> などがあります。  
  
 次の例の最初のクエリは、すべての製品を表示価格で並べ替えて返します。  <xref:System.Linq.Enumerable.ToArray%2A> メソッドを使用して、クエリの即時実行を強制しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## 参照  
 [Programming Guide](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)   
 [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [Getting Started with LINQ in C\#](../Topic/Getting%20Started%20with%20LINQ%20in%20C%23.md)   
 [Getting Started with LINQ in Visual Basic](../Topic/Getting%20Started%20with%20LINQ%20in%20Visual%20Basic.md)