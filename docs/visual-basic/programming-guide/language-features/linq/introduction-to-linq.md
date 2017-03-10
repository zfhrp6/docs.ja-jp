---
title: "Introduction to LINQ in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [LINQ in Visual Basic], about LINQ in Visual Basic queries"
  - "query execution [LINQ in Visual Basic]"
  - "range variables"
  - "LINQ [Visual Basic]"
  - "LINQ [Visual Basic], about LINQ in Visual Basic"
  - "query expressions [LINQ in Visual Basic]"
  - "LINQ"
  - "deferred execution"
  - "iteration variables"
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Introduction to LINQ in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

統合言語クエリ \(LINQ: Language\-Integrated Query\) は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] にクエリ機能を追加します。この単純かつ強力な機能を使用して、あらゆる種類のデータを操作できます。  処理の対象であるデータベースにクエリを送信したり、検索するデータの種類ごとに異なるクエリ構文を使用したりする代わりに、LINQ では、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 言語の一部としてのクエリを採用しています。  LINQ では、データの型に関係なく、統一された構文を使用します。  
  
 LINQ を使用すると、SQL Server データベース、XML、インメモリ配列、インメモリ コレクション、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] データセットなど、LINQ をサポートするリモートまたはローカルのデータ ソースのデータを照会できます。  これは、共通 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 言語要素を使用して実行できます。  クエリは [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 言語で記述されるので、クエリ結果は、厳密に型指定されたオブジェクトとして返されます。  これらのオブジェクトは IntelliSense をサポートするので、コードの記述時間を短縮でき、さらに、クエリに含まれるエラーを実行時ではなくコンパイル時に把握できます。  LINQ クエリは、結果を絞り込むための追加クエリのソースとして使用できます。  クエリ結果をユーザーが簡単に表示および変更できるように、コントロールにバインディングすることもできます。  
  
 たとえば、次のコード例は、コレクションから顧客リストを返し、住所に基づいて顧客をグループ化する LINQ クエリを示しています。  
  
 [!code-vb[VbVbalrIntroToLINQ#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_1.vb)]  
  
 このトピックには、次の項目に関する情報が含まれています。  
  
-   [例の実行](#RunningtheExamples)  
  
-   [LINQ プロバイダー](#LINQProviders)  
  
-   [LINQ クエリの構造](#StructureOfALINQQuery)  
  
-   [Visual Basic LINQ クエリ演算子](#VisualBasicLINQQueryOperators)  
  
-   [LINQ to SQL を使用したデータベースへの接続](#ConnectingToADatabase)  
  
-   [LINQ をサポートする Visual Basic の機能](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [クエリの遅延実行と即時実行](#QueryExecution)  
  
-   [Visual Basic における XML](#XMLInVisualBasic)  
  
-   [関連リソース](#RelatedResources)  
  
-   [方法とチュートリアルのトピック](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a> 例の実行  
 概要と「LINQ クエリの構造」セクションの例を実行するには、次のコードを含めます。このコードは、顧客と注文の一覧を返します。  
  
 [!code-vb[VbVbalrIntroToLINQ#31](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a> LINQ プロバイダー  
 *LINQ プロバイダー*は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] LINQ クエリを、クエリ対象のデータ ソースに対応付けます。  LINQ クエリを記述すると、そのクエリは、プロバイダーによって、データ ソースが実行できるコマンドに変換されます。  プロバイダーは、ソースのデータを、クエリ結果を構成するオブジェクトに変換する操作も行います。  最後に、プロバイダーは、データ ソースに更新が送信されるときに、オブジェクトをデータに変換します。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、次の LINQ プロバイダーが含まれています。  
  
|||  
|-|-|  
|プロバイダー|説明|  
|LINQ to Objects|LINQ to Objects プロバイダーは、インメモリ コレクションとインメモリ配列のクエリを可能にします。  オブジェクトが <xref:System.Collections.IEnumerable> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601> インターフェイスをサポートしている場合、LINQ to Objects プロバイダーを使用してクエリを実行できます。<br /><br /> LINQ to Objects プロバイダーは、<xref:System.Linq> 名前空間をインポートすることで有効にできます。この名前空間は、すべての [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] プロジェクトに対して既定でインポートされます。<br /><br /> LINQ to Objects プロバイダーの詳細については、「[LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)」を参照してください。|  
|LINQ to SQL|LINQ to SQL プロバイダーは、SQL Server データベース内のデータのクエリと変更を可能にします。  これにより、アプリケーションのオブジェクト モデルを、データベース内のテーブルとオブジェクトに簡単に対応付けることができます。<br /><br /> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) を用意することで、LINQ to SQL の操作を容易にしています。  このデザイナーを使用して、データベース内のオブジェクトに対応付けられるアプリケーション内のオブジェクト モデルを作成します。 O\/R デザイナーは、ストアド プロシージャと関数を <xref:System.Data.Linq.DataContext> オブジェクトに対応付ける機能も備えています。さらに、データベースとの通信を管理し、オプティミスティック同時実行制御チェックの状態を保存します。<br /><br /> LINQ to SQL プロバイダーの詳細については、「[LINQ to SQL](../Topic/LINQ%20to%20SQL.md)」を参照してください。  オブジェクト リレーショナル デザイナーの詳細については、「[Object Relational Designer \(O\/R Designer\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2)」を参照してください。|  
|LINQ to XML|LINQ to XML プロバイダーは、XML のクエリと変更を可能にします。  インメモリ XML を変更することや、XML をファイルから読み込んだりファイルに保存したりすることができます。<br /><br /> さらに、LINQ to XML プロバイダーでは、XML リテラルと XML 軸プロパティを使用して、XML を [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コード内に直接記述できます。  詳細については、「[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)」を参照してください。|  
|LINQ to DataSet|LINQ to DataSet プロバイダーは、[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] データセット内のデータのクエリと更新を可能にします。  データセットを使用するアプリケーションに LINQ を追加することで、データセット内のデータのクエリ、集計、および更新などの機能を単純化すると同時に拡張できます。<br /><br /> 詳細については、「[LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)」を参照してください。|  
  
##  <a name="StructureOfALINQQuery"></a> LINQ クエリの構造  
 LINQ クエリ \(*クエリ式*とも呼ばれます\) は、データ ソースを識別するクエリ句と、クエリの反復変数の組み合わせで構成されます。  クエリ式には、並べ替え、フィルター処理、グループ化、および結合を実行する命令や、ソース データに適用する演算も指定できます。  クエリ式の構文は SQL の構文に似ているので、ほとんどの構文は、改めて覚える必要はありません。  
  
 クエリ式は、`From` 句で始まります。  この句は、クエリのソース データと、ソース データの各要素を個別に参照するために使用される変数を識別します。  これらの変数は、*範囲変数*または*反復変数*と呼ばれます。  `From` 句は、`Aggregate` クエリ以外のクエリでは必須です。このクエリでは、`From` 句は省略できます。  `From` 句または `Aggregate` 句でクエリのスコープとソースを識別した後、クエリを絞り込むためのクエリ句を自由に組み合わせて記述できます。  クエリ句の詳細については、このトピックの「[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] LINQ クエリ演算子」を参照してください。  たとえば、次のクエリでは、顧客データのソース コレクションを `customers` 変数として識別し、`cust` という名前の反復変数を識別します。  
  
 [!code-vb[VbVbalrIntroToLINQ#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_3.vb)]  
  
 この例はそのままでも有効なクエリですが、結果を絞り込むクエリ句を追加すると、はるかに強力なクエリになります。  たとえば、`Where` 句を追加して、結果を 1 つ以上の値でフィルター処理できます。  クエリ式は、1 行のコードです。追加のクエリ句は、クエリの末尾に単純に追加できます。  クエリを読みやすくするために、行連結文字のアンダースコア \(\_\) を使用して、複数のテキスト行に分割できます。  次のコード例は、`Where` 句を含むクエリの例を示しています。  
  
 [!code-vb[VbVbalrIntroToLINQ#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_4.vb)]  
  
 別の強力なクエリ句として、`Select` 句があります。この句を使用すると、データ ソースから選択したフィールドだけを返すことができます。  LINQ クエリは、厳密に型指定されたオブジェクトの列挙可能なコレクションを返します。  クエリは、匿名型または名前付きの型のコレクションを返すことができます。  `Select` 句を使用して、データ ソースから単一のフィールドを返すことができます。  これを行った場合、返されるコレクションの型は、その単一のフィールドの型になります。  `Select` 句を使用して、データ ソースから複数のフィールドを返すこともできます。  これを行った場合、返されるコレクションの型は、新しい匿名型になります。  クエリで返されたフィールドを、指定した名前付きの型のフィールドと一致させることもできます。  次のコード例は、データ ソースから選択されたフィールドのデータが設定されたメンバーのコレクションで、匿名型のコレクションを返すクエリ式を示します。  
  
 [!code-vb[VbVbalrIntroToLINQ#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_5.vb)]  
  
 LINQ クエリを使用して、複数のデータ ソースを結合し、単一の結果を返すこともできます。  これは、1 つまたは複数の `From` 句を使用するか、`Join` クエリ句または `Group Join` クエリ句を使用して実行できます。  次のコード例は、顧客データと注文データを結合し、顧客データと注文データが格納された匿名型のコレクションを返すクエリ式を示します。  
  
 [!code-vb[VbVbalrIntroToLINQ#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_6.vb)]  
  
 `Group Join` 句を使用して、顧客オブジェクトのコレクションを格納する階層的なクエリ結果を作成できます。  各顧客オブジェクトには、その顧客のすべての注文のコレクションを含むプロパティがあります。  次のコード例は、顧客データと注文データを階層的な結果として結合し、匿名型のコレクションを返すクエリ式を示します。  このクエリは、顧客の注文データのコレクションを格納する `CustomerOrders` プロパティを含む型を返します。  その顧客のすべての注文の合計を格納する `OrderTotal` プロパティも含まれます   \(このクエリは、LEFT OUTER JOIN と同等です\)。  
  
 [!code-vb[VbVbalrIntroToLINQ#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_7.vb)]  
  
 上記以外にも、強力なクエリ式を作成するために使用できる、さまざまな LINQ クエリ演算子があります。  このトピックの次のセクションで、クエリ式で使用できるさまざまなクエリ句について説明します。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] クエリ句の詳細については、「[Queries](../../../../visual-basic/language-reference/queries/queries.md)」を参照してください。  
  
##  <a name="VisualBasicLINQQueryOperators"></a> Visual Basic LINQ クエリ演算子  
 LINQ クエリをサポートする <xref:System.Linq> 名前空間とその他の名前空間のクラスには、アプリケーションの要件に基づいてクエリの作成と絞り込みを行うために呼び出すことができるメソッドが含まれています。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、最も一般的なクエリ句のキーワードが用意されています。これらについて、次の表で説明します。  
  
|||  
|-|-|  
|用語|定義|  
|[From Clause](../../../../visual-basic/language-reference/queries/from-clause.md)|クエリを開始するには、`From` 句または `Aggregate` 句のいずれかが必要です。  `From` 句は、クエリのソース コレクションと反復変数を指定します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#7](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_8.vb)]|  
|[Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md)|省略可能です。  クエリの反復変数のセットを宣言します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#8](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_9.vb)]<br /><br /> `Select` 句の指定がない場合、クエリの反復変数は、`From` 句または `Aggregate` 句で指定された反復変数で構成されます。|  
|[Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md)|省略可能です。  クエリのフィルター処理条件を指定します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#9](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_10.vb)]|  
|[Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md)|省略可能です。  クエリ内に列の並べ替え順序を指定します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_11.vb)]|  
|[Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md)|省略可能です。  2 つのコレクションを単一のコレクションに結合します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_12.vb)]|  
|[Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)|省略可能です。  クエリ結果の要素をグループ化します。  これを使用して、グループごとに集計関数を適用できます。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_13.vb)]|  
|[Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md)|省略可能です。  2 つのコレクションを、単一の階層コレクションに結合します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_14.vb)]|  
|[Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|クエリを開始するには、`From` 句または `Aggregate` 句のいずれかが必要です。  `Aggregate` 句は、1 つ以上の集計関数をコレクションに適用します。  たとえば、`Aggregate` 句を使用して、クエリで返されたすべての要素の合計を計算できます。<br /><br /> [!code-vb[VbVbalrIntroToLINQ#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_15.vb)]<br /><br /> `Aggregate` 句を使用してクエリを変更することもできます。  たとえば、`Aggregate` 句を使用して、関連するクエリ コレクションに対して計算を実行できます。<br /><br /> [!code-vb[VbVbalrIntroToLINQ#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_16.vb)]|  
|[Let Clause](../../../../visual-basic/language-reference/queries/let-clause.md)|省略可能です。  値を計算し、その値をクエリ内の新しい変数に代入します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_17.vb)]|  
|[Distinct Clause](../../../../visual-basic/language-reference/queries/distinct-clause.md)|省略可能です。  現在の反復変数の値を制限して、クエリ結果内で重複する値を除去します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#17](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_18.vb)]|  
|[Skip Clause](../../../../visual-basic/language-reference/queries/skip-clause.md)|省略可能です。  コレクション内の指定された数の要素をバイパスし、残りの要素を返します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#18](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_19.vb)]|  
|[Skip While Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|省略可能です。  指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#19](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_20.vb)]|  
|[Take Clause](../../../../visual-basic/language-reference/queries/take-clause.md)|省略可能です。  コレクションの先頭から、指定された数の連続する要素を返します。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#20](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_21.vb)]|  
|[Take While Clause](../../../../visual-basic/language-reference/queries/take-while-clause.md)|省略可能です。  指定された条件が `true` である限り、コレクションの要素を含むようにし、残りの要素をバイパスします。  例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#21](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_22.vb)]|  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] クエリ句の詳細については、「[Queries](../../../../visual-basic/language-reference/queries/queries.md)」を参照してください。  
  
 LINQ によって提供される列挙可能でクエリ可能な型のメンバーを呼び出すことで、追加の LINQ クエリ機能を使用できます。  これらの追加機能は、クエリ式の結果に対して特定のクエリ演算子を呼び出すことで使用できます。  たとえば、次のコード例では、<xref:System.Linq.Enumerable.Union%2A> メソッドを使用して、2 つのクエリの結果を、1 つのクエリ結果に結合します。  また、<xref:System.Linq.Enumerable.ToList%2A> メソッドを使用して、クエリ結果をジェネリック リストとして返します。  
  
 [!code-vb[VbVbalrIntroToLINQ#22](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/introduction-to-linq_23.vb)]  
  
 その他の LINQ 機能の詳細については、「[Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。  
  
##  <a name="ConnectingToADatabase"></a> LINQ to SQL を使用したデータベースへの接続  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、アクセスする SQL Server データベース オブジェクト \(テーブル、ビュー、ストアド プロシージャなど\) を、LINQ to SQL ファイルを使用して識別します。  LINQ to SQL ファイルには、.dbml という拡張子が付きます。  
  
 SQL Server データベースへの有効な接続が存在する場合は、**LINQ to SQL クラス**項目テンプレートをプロジェクトに追加できます。  これを行うと、オブジェクト リレーショナル デザイナー \(O\/R デザイナー\) が表示されます。  O\/R デザイナーを使用して、コード内でアクセスする項目を、**サーバー エクスプローラー**\/**データベース エクスプローラー**からデザイナー画面にドラッグできます。  LINQ to SQL ファイルは、<xref:System.Data.Linq.DataContext> オブジェクトをプロジェクトに追加します。  このオブジェクトには、アクセスするテーブルとビューのプロパティおよびコレクションと、呼び出すストアド プロシージャのメソッドが格納されます。  変更を LINQ to SQL \(.dbml\) ファイルに保存した後、O\/R デザイナーで定義された <xref:System.Data.Linq.DataContext> オブジェクトを参照することで、コード内でこれらのオブジェクトにアクセスできます。  プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトには、LINQ to SQL ファイルの名前に基づいて名前が付けられます。  たとえば、Northwind.dbml という名前の LINQ to SQL ファイルの場合は、<xref:System.Data.Linq.DataContext> という名前の `NorthwindDataContext` オブジェクトが作成されます。  
  
 例と詳細な手順については、「[How to: Query a Database](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md)」と「[How to: Call a Stored Procedure](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md)」を参照してください。  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a> LINQ をサポートする Visual Basic の機能  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、LINQ の使用を単純化し、LINQ クエリを実行するために記述する必要があるコードの量を減らすことができる、注目に値する機能が他にもあります。  次に例を示します。  
  
-   **匿名型**。クエリ結果に基づいて、新しい型を作成できます。  
  
-   **暗黙的に型指定される変数**。型の指定を遅らせ、クエリ結果に基づいてコンパイラで型を推論できます。  
  
-   **拡張メソッド**。型自体を変更することなく、独自のメソッドを使用して既存の型を拡張できます。  
  
 詳細については、「[Visual Basic Features That Support LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md)」を参照してください。  
  
##  <a name="QueryExecution"></a> クエリの遅延実行と即時実行  
 クエリの実行とクエリの作成は分離しています。  クエリを作成した後、その実行は、別のメカニズムによってトリガーされます。  クエリは、定義後すぐに実行 \(*即時実行*\) することも、定義を保存しておき、後でクエリを実行 \(*遅延実行*\) することもできます。  
  
 既定では、クエリを作成しても、クエリ自体が直ちに実行されることはありません。  代わりに、クエリ結果を参照するために使用される変数にクエリ定義が格納されます。  そのクエリ結果変数が、後でコード内の `For…Next` ループなどでアクセスされると、クエリが実行されます。  この処理を*遅延実行*と呼びます。  
  
 クエリは、それを定義したときに実行することもできます。これを*即時実行*と呼びます。  即時実行は、クエリ結果の個々の要素にアクセスする必要があるメソッドを適用することで開始できます。  `Count`、`Sum`、`Average`、`Min`、`Max` などの集計関数を含めることで、この結果を得ることができます。  集計関数の詳細については、「[Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md)」を参照してください。  
  
 `ToList` メソッドまたは `ToArray` メソッドを使用することでも、即時実行を開始できます。  これは、クエリを直ちに実行し、結果をキャッシュする場合に役に立ちます。  これらのメソッドの詳細については、「[Converting Data Types](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)」を参照してください。  
  
 クエリの実行の詳細については、「[初めての LINQ クエリの作成](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)」を参照してください。  
  
##  <a name="XMLInVisualBasic"></a> Visual Basic における XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] における XML の機能には、XML リテラルと XML 軸プロパティがあります。これらを使用して、コード内で XML を簡単に作成、アクセス、照会、および変更できます。  XML リテラルを使用すると、XML をコード内に直接記述できます。  Visual Basic コンパイラは、XML を、最初のクラスのデータ オブジェクトとして処理します。  
  
 次のコード例は、XML 要素を作成し、そのサブ要素と属性にアクセスし、LINQ を使用してその要素の内容を照会する方法を示しています。  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/introduction-to-linq_24.vb)]  
  
 詳細については、「[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)」を参照してください。  
  
##  <a name="RelatedResources"></a> 関連リソース  
  
|||  
|-|-|  
|トピック|説明|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] における XML の機能について説明します。これらの機能を使用して照会を行い、XML を最初のクラスのデータ オブジェクトとして [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コード内に記述できます。|  
|[Queries](../../../../visual-basic/language-reference/queries/queries.md)|[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で使用できるクエリ句のリファレンス情報を示します。|  
|[LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)|LINQ の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to SQL](../Topic/LINQ%20to%20SQL.md)|LINQ to SQL の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)|LINQ to Objects の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to ADO.NET](../Topic/LINQ%20to%20ADO.NET%20\(Portal%20Page\)1.md)|LINQ to [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] の概要、プログラミング ガイド、およびサンプルへのリンクを示します。|  
|[LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)|LINQ to XML の概要、プログラミング ガイド、およびサンプルを示します。|  
  
##  <a name="HowToAndWalkthroughTopics"></a> 方法とチュートリアルのトピック  
 [How to: Query a Database](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md)  
  
 [How to: Call a Stored Procedure](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [How to: Modify Data in a Database](../../../../visual-basic/programming-guide/language-features/linq/how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)  
  
 [How to: Sort Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
  
 [How to: Filter Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
  
 [How to: Count, Sum, or Average Data](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [How to: Find the Minimum or Maximum Value in a Query Result](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)  
  
## 参考書籍の該当する章  
 『[Programming Visual Basic 2008](http://go.microsoft.com/fwlink/?LinkId=195383)』の「[Chapter 17: LINQ](http://go.microsoft.com/fwlink/?LinkId=195277)」  
  
## 参照  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)   
 [LINQ to DataSet Overview](../Topic/LINQ%20to%20DataSet%20Overview.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ のサンプル](../Topic/LINQ%20Samples.md)   
 [Object Relational Designer \(O\/R Designer\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2)   
 [DataContext Methods \(O\/R Designer\)](/visual-studio/data-tools/datacontext-methods-o-r-designer)