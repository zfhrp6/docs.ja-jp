---
title: "初めての LINQ クエリの作成 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "クエリ [Visual Basic での LINQ]、作成"
  - "LINQ クエリ [Visual Basic]"
  - "LINQ [Visual Basic]、クエリの作成"
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 54
---
# 初めての LINQ クエリの作成 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*クエリ*とは、データ ソースからデータを取得するための式です。  クエリは、専用のクエリ言語で表されます。  これまでに、リレーショナル データベース用の SQL や XML 用の XQuery など、データ ソースの種類に合わせてさまざまな言語が開発されてきました。  このため、アプリケーション開発者は、サポートするデータ ソースの種類やデータ形式ごとに新しいクエリ言語を習得する必要が生じています。  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] は、さまざまな種類のデータ ソースやデータ形式のデータを操作するための一貫したモデルを提供することにより、この負担を軽減します。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリでは、操作の対象は常にオブジェクトになります。  共通の基本的なコーディング パターンを使用することで、XML ドキュメント、SQL データベース、ADO.NET のデータセットとエンティティ、.NET Framework コレクション、および [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーを利用できる他の任意のソースまたは形式のデータを照会したり変換したりできます。  ここでは、基本的な [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリの作成と使用に関する 3 つの段階について説明します。  
  
 ![ビデオへのリンク](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") 関連するビデオ デモについては、「[How Do I: Get Started with LINQ? \(操作方法: LINQ を使用する\)](http://go.microsoft.com/fwlink/?LinkId=133021)」を参照してください。  
  
## クエリ操作の 3 つの段階  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリ操作は、次の 3 つの手順で構成されます。  
  
1.  データ ソースを取得します。  
  
2.  クエリを作成します。  
  
3.  クエリを実行します。  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] では、クエリの実行とクエリの作成は別々の操作になります。  クエリを作成するだけでは、データは取得されません。  この点については、後で詳しく説明します。  
  
 クエリ操作を構成する 3 つの部分を次の例に示します。  この例では、デモンストレーションのために、わかりやすいデータ ソースとして整数の配列を使用しています。  ただし、他のデータ ソースを使用する場合にも同じ概念が当てはまります。  
  
> [!NOTE]
>  [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)で、**\[Option Infer\]** がに設定されていることを確認します。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_1.vb)]  
  
 出力  
  
 `0 2 4 6`  
  
## データ ソース  
 前の例では、データ ソースが配列であるため、暗黙的にジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスがサポートされます。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリのデータ ソースとして配列を使用できるのは、この動作によります。  ジェネリック <xref:System.Linq.IQueryable%601> などの <xref:System.Collections.Generic.IEnumerable%601> または派生したインターフェイスをサポートする型は、*クエリ可能型と*呼ばれます。  
  
 配列は暗黙的にクエリ可能型であるため、変更や特別な処理を行わなくても、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] データ ソースとして使用できます。  これは、任意のコレクション型にも当てはまります。.NET Framework クラス ライブラリのジェネリック <xref:System.Collections.Generic.List%601>、<xref:System.Collections.Generic.Dictionary%602>などを含む、サポート <xref:System.Collections.Generic.IEnumerable%601>。  
  
 ソース データが既に <xref:System.Collections.Generic.IEnumerable%601>を実装するデータ ソースの *標準クエリ演算子* の機能を実装するために、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] のプロバイダーが必要です。  たとえば、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] は、次の例に示すように、クエリ可能な <xref:System.Xml.Linq.XElement> 型に XML ドキュメントを読み込む処理を行います。  標準クエリ演算子の詳細については、「[Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_2.vb)]  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] では、まず、デザイン時に手動で、または[Object Relational Designer \(O\/R Designer\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2) を使用して、オブジェクト リレーショナル マッピングを作成します。  オブジェクトに対するクエリを記述すると、実行時には、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] によってデータベースとの通信が処理されます。  次の例では、`customers` はデータベースのテーブルを表し、<xref:System.Data.Linq.Table%601> はジェネリック <xref:System.Linq.IQueryable%601> をサポートします。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 それぞれの種類のデータ ソースを作成する方法の詳細については、対応する [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーのドキュメントを参照してください。  これらのプロバイダーの一覧については、「[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)」を参照してください。基本的な規則は単純です。[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] データ ソースは、ジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイス、またはこれを継承するインターフェイスをサポートする任意のオブジェクトです。  
  
> [!NOTE]
>  非ジェネリック <xref:System.Collections.IEnumerable> インターフェイスをサポートする <xref:System.Collections.ArrayList> などの型も、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] データ ソースとして使用できます。  <xref:System.Collections.ArrayList> の使用例については、「[How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md)」を参照してください。  
  
## クエリ  
 クエリでは、データ ソースからどのような情報を取得するかを指定します。  情報が返される前に、その情報を並べ替え、グループ化し、構造化する方法を指定するオプションもあります。  クエリの作成を可能にするために、Visual Basic 言語に新しいクエリ構文が組み込まれています。  
  
 次の例のクエリを実行すると、整数の配列 `numbers` からすべての偶数が返されます。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_1.vb)]  
  
 クエリ式には、`From`、`Where`、および `Select` の 3 つの句が含まれています。  クエリ式の各句の機能と目的については、「[基本的なクエリ操作 \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)」で説明しています。  詳細については、「[Queries](../../../../visual-basic/language-reference/queries/queries.md)」を参照してください。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] では、クエリ定義が変数に格納され、後で実行されることがよくあります。  前の例の `evensQuery` のようなクエリ変数は、クエリ可能型である必要があります。`evensQuery` の型はローカル型の推論を使用して、コンパイラにより再配置 `IEnumerable(Of Integer)`です。  
  
 クエリ変数自体は何も処理を行わず、データを返さないことに注意してください。  これは、クエリ定義を格納するだけです。  前の例では、クエリを実行するのは `For Each` ループです。  
  
## クエリの実行  
 クエリの実行は、クエリの作成とは別の操作です。  クエリの作成ではクエリを定義しますが、実行は別の機構によって発生します。  クエリは、定義後すぐに実行 \(*即時実行*\) することも、定義を保存しておき、後でクエリを実行 \(*遅延実行*\) することもできます。  
  
### 遅延実行  
 一般的な [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリでは、前の例の `evensQuery` ようなものが定義されます。  つまり、クエリを作成しても、すぐには実行されません。  代わりに、クエリ変数 `evensQuery` にクエリ定義が格納されます。  クエリは後で実行され、通常は、値のシーケンスを返す `For Each` ループを使用するか、`Count` や `Max` などの標準クエリ演算子を適用することで行われます。  この処理を*遅延実行*と呼びます。  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_3.vb)]  
  
 値のシーケンスの場合、取得したデータにアクセスするには、`For Each` ループの反復変数 \(前の例の `number`\) を使用します。  クエリ変数 `evensQuery` にはクエリ結果ではなくクエリ定義が保持されているため、クエリ変数を複数回使用することで、必要に応じて何度でもクエリを実行できます。  たとえば、アプリケーションで使用しているデータベースが、別のアプリケーションによって頻繁に更新されるとします。  データベースのデータを取得するクエリを作成したら、`For Each` ループを使用してクエリを繰り返し実行することで、常に最新のデータを取得できます。  
  
 次の例は、遅延実行のしくみを示しています。  前の例と同様に、`evensQuery2` が定義され、`For Each` ループで実行されますが、その後でデータ ソース `numbers` の一部の要素が変更されます。  次に、2 回目の `For Each` ループによって `evensQuery2` が再実行されます。  2 回目は、`For Each` ループが `numbers` の新しい値を使用してクエリを再実行するため、結果が異なります。  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_4.vb)]  
  
 出力  
  
 `Evens in original array:`  
  
 `0 2 4 6`  
  
 `Evens in changed array:`  
  
 `0 10 2 22 8`  
  
### 即時実行  
 クエリの遅延実行では、クエリ定義がクエリ変数に格納され、後で実行されます。  即時実行では、クエリは定義時に実行されます。  クエリ結果の個々の要素にアクセスする必要のあるメソッドを使用すると、実行が発生します。  多くの場合、即時実行は、単一の値を返す標準クエリ演算子の使用によって強制的に行われます。  例としては、`Count`、`Max`、`Average`、および `First` があります。  これらの標準クエリ演算子が適用されると、単一の結果を計算して返すために、すぐにクエリが実行されます。  単一の値を返す標準クエリ演算子の詳細については、「[Aggregation Operations](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)」、「[Element Operations](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)」、および「[Quantifier Operations](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)」を参照してください。  
  
 次の例のクエリは、整数の配列に含まれる偶数の数を返します。  クエリ定義は保存されず、`numEvens` は単純な `Integer` になります。  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_5.vb)]  
  
 `Aggregate` メソッドを使用しても、同じ結果を得ることができます。  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_6.vb)]  
  
 次のコードに示すように、クエリ \(即時実行の場合\) またはクエリ変数 \(遅延実行の場合\) に対して `ToList` メソッドまたは `ToArray` メソッドを呼び出すことでも、クエリを強制的に実行できます。  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/writing-your-first-linq-_7.vb)]  
  
 前の例では、`evensQuery3` はクエリ変数ですが、`evensList` はリストで、`evensArray` は配列です。  
  
 `ToList` または `ToArray` を使用して強制的に即時実行する方法は、クエリをすぐに実行し、結果を単一のコレクション オブジェクトにキャッシュする場合に特に便利です。  これらのメソッドの詳細については、「[Converting Data Types](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)」を参照してください。  
  
 <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> メソッドなどの `IEnumerable` メソッドを使用して、クエリを実行することもできます。  
  
## 関連ビデオ デモ  
 [How Do I: Get Started with LINQ? \(操作方法: LINQ を使用する\)](http://go.microsoft.com/fwlink/?LinkId=133021)  
  
 [Video How to: Writing Queries in Visual Basic \(ビデオ デモ: Visual Basic でのクエリの作成\)](http://go.microsoft.com/fwlink/?LinkID=100356)  
  
## 参照  
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ のサンプル](../Topic/LINQ%20Samples.md)   
 [O\/R Designer Overview](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)