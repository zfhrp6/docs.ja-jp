---
title: "Visual Basic における LINQ の概要"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bb55aecc1faafd812da212565a7a858c714e933
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic における LINQ の概要
統合言語クエリ (LINQ: Language-Integrated Query) は、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] にクエリ機能を追加します。この単純かつ強力な機能を使用して、あらゆる種類のデータを操作できます。 処理の対象であるデータベースにクエリを送信したり、検索するデータの種類ごとに異なるクエリ構文を使用したりする代わりに、LINQ では、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 言語の一部としてのクエリを採用しています。 LINQ では、データの型に関係なく、統一された構文を使用します。  
  
 LINQ を使用するとデータのクエリを SQL Server データベース、XML、インメモリ配列、およびコレクションから[!INCLUDE[vstecado](~/includes/vstecado-md.md)]データセット、またはその他のリモートまたはローカルのデータ ソースの LINQ をサポートします。 これは、共通 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 言語要素を使用して実行できます。 クエリは [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 言語で記述されるので、クエリ結果は、厳密に型指定されたオブジェクトとして返されます。 これらのオブジェクトは IntelliSense をサポートするので、コードの記述時間を短縮でき、さらに、クエリに含まれるエラーを実行時ではなくコンパイル時に把握できます。 LINQ クエリは、結果を絞り込むための追加クエリのソースとして使用できます。 クエリ結果をユーザーが簡単に表示および変更できるように、コントロールにバインディングすることもできます。  
  
 たとえば、次のコード例は、コレクションから顧客リストを返し、住所に基づいて顧客をグループ化する LINQ クエリを示しています。  
  
 [!code-vb[VbVbalrIntroToLINQ#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_1.vb)]  
  
 このトピックには、次の項目に関する情報が含まれています。  
  
-   [例の実行](#RunningtheExamples)  
  
-   [LINQ プロバイダー](#LINQProviders)  
  
-   [LINQ クエリの構造](#StructureOfALINQQuery)  
  
-   [Visual Basic LINQ クエリ演算子](#VisualBasicLINQQueryOperators)  
  
-   [LINQ to SQL を使用して、データベースに接続します。](#ConnectingToADatabase)  
  
-   [LINQ をサポートする Visual Basic の機能](#VisualBasicFeaturesThatSupportLINQ)  
  
-   [クエリ遅延に、即時実行](#QueryExecution)  
  
-   [Visual Basic における XML](#XMLInVisualBasic)  
  
-   [関連リソース](#RelatedResources)  
  
-   [方法とチュートリアルのトピック](#HowToAndWalkthroughTopics)  
  
##  <a name="RunningtheExamples"></a>例の実行  
 概要と「LINQ クエリの構造」セクションの例を実行するには、次のコードを含めます。このコードは、顧客と注文の一覧を返します。  
  
 [!code-vb[VbVbalrIntroToLINQ#31](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_2.vb)]  
  
##  <a name="LINQProviders"></a>LINQ プロバイダー  
 A *LINQ プロバイダー*マップ、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]クエリ対象データ ソースへの LINQ クエリ。 LINQ クエリを記述すると、そのクエリは、プロバイダーによって、データ ソースが実行できるコマンドに変換されます。 プロバイダーは、ソースのデータを、クエリ結果を構成するオブジェクトに変換する操作も行います。 最後に、プロバイダーは、データ ソースに更新が送信されるときに、オブジェクトをデータに変換します。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] には、次の LINQ プロバイダーが含まれています。  
  
|プロバイダー|説明|  
|---|---|  
|LINQ to Objects|LINQ to Objects プロバイダーは、インメモリ コレクションとインメモリ配列のクエリを可能にします。 オブジェクトが <xref:System.Collections.IEnumerable> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601> インターフェイスをサポートしている場合、LINQ to Objects プロバイダーを使用してクエリを実行できます。<br /><br /> LINQ to Objects プロバイダーは、<xref:System.Linq> 名前空間をインポートすることで有効にできます。この名前空間は、すべての [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] プロジェクトに対して既定でインポートされます。<br /><br /> LINQ to Objects プロバイダーの詳細については、次を参照してください。 [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)です。|  
|LINQ to SQL|LINQ to SQL プロバイダーは、SQL Server データベース内のデータのクエリと変更を可能にします。 これにより、アプリケーションのオブジェクト モデルを、データベース内のテーブルとオブジェクトに簡単に対応付けることができます。<br /><br /> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では、オブジェクト リレーショナル デザイナー (O/R デザイナー) を用意することで、LINQ to SQL の操作を容易にしています。 このデザイナーを使用して、データベース内のオブジェクトに対応付けられるアプリケーション内のオブジェクト モデルを作成します。 O/R デザイナーもストアド プロシージャにマップする機能を提供し、関数、<xref:System.Data.Linq.DataContext>データベースとの通信を管理およびオプティミスティック同時実行チェックの状態を格納するオブジェクト。<br /><br /> LINQ to SQL プロバイダーの詳細については、次を参照してください。 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)です。 オブジェクト リレーショナル デザイナーの詳細については、次を参照してください。 [LINQ to Visual Studio での SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)です。|  
|LINQ to XML|LINQ to XML プロバイダーは、XML のクエリと変更を可能にします。 インメモリ XML を変更することや、XML をファイルから読み込んだりファイルに保存したりすることができます。<br /><br /> さらに、LINQ to XML プロバイダーでは、XML リテラルと XML 軸プロパティを使用して、XML を [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コード内に直接記述できます。 詳細については、次を参照してください。 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)です。|  
|LINQ to DataSet|LINQ to DataSet プロバイダーを使用するとクエリおよび更新データを[!INCLUDE[vstecado](~/includes/vstecado-md.md)]データセット。 データセットを使用するアプリケーションに LINQ を追加することで、データセット内のデータのクエリ、集計、および更新などの機能を単純化すると同時に拡張できます。<br /><br /> 詳細については、「[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)」を参照してください。|  
  
##  <a name="StructureOfALINQQuery"></a>LINQ クエリの構造  
 LINQ クエリは多くの場合と呼ばれる、*クエリ式*、データ ソースとクエリの反復変数を識別するクエリ句の組み合わせで構成されています。 クエリ式には、並べ替え、フィルター処理、グループ化、および結合を実行する命令や、ソース データに適用する演算も指定できます。 クエリ式の構文は SQL の構文に似ているので、ほとんどの構文は、改めて覚える必要はありません。  
  
 クエリ式は、`From` 句で始まります。 この句は、クエリのソース データと、ソース データの各要素を個別に参照するために使用される変数を識別します。 これらの変数の名前は*範囲変数*または*反復変数*です。 `From` 句は、`Aggregate` クエリ以外のクエリでは必須です。このクエリでは、`From` 句は省略できます。 `From` 句または `Aggregate` 句でクエリのスコープとソースを識別した後、クエリを絞り込むためのクエリ句を自由に組み合わせて記述できます。 クエリ句の詳細については、このトピックの「[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] LINQ クエリ演算子」を参照してください。 たとえば、次のクエリでは、顧客データのソース コレクションを `customers` 変数として識別し、`cust` という名前の反復変数を識別します。  
  
 [!code-vb[VbVbalrIntroToLINQ#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_3.vb)]  
  
 この例はそのままでも有効なクエリですが、結果を絞り込むクエリ句を追加すると、はるかに強力なクエリになります。 たとえば、`Where` 句を追加して、結果を 1 つ以上の値でフィルター処理できます。 クエリ式は、1 行のコードです。追加のクエリ句は、クエリの末尾に単純に追加できます。 クエリを読みやすくするために、行連結文字のアンダースコア (_) を使用して、複数のテキスト行に分割できます。 次のコード例は、`Where` 句を含むクエリの例を示しています。  
  
 [!code-vb[VbVbalrIntroToLINQ#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_4.vb)]  
  
 別の強力なクエリ句として、`Select` 句があります。この句を使用すると、データ ソースから選択したフィールドだけを返すことができます。 LINQ クエリは、厳密に型指定されたオブジェクトの列挙可能なコレクションを返します。 クエリは、匿名型または名前付きの型のコレクションを返すことができます。 `Select` 句を使用して、データ ソースから単一のフィールドを返すことができます。 これを行った場合、返されるコレクションの型は、その単一のフィールドの型になります。 `Select` 句を使用して、データ ソースから複数のフィールドを返すこともできます。 これを行った場合、返されるコレクションの型は、新しい匿名型になります。 クエリで返されたフィールドを、指定した名前付きの型のフィールドと一致させることもできます。 次のコード例は、データ ソースから選択されたフィールドのデータが設定されたメンバーのコレクションで、匿名型のコレクションを返すクエリ式を示します。  
  
 [!code-vb[VbVbalrIntroToLINQ#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_5.vb)]  
  
 LINQ クエリを使用して、複数のデータ ソースを結合し、単一の結果を返すこともできます。 これは、1 つまたは複数の `From` 句を使用するか、`Join` クエリ句または `Group Join` クエリ句を使用して実行できます。 次のコード例は、顧客データと注文データを結合し、顧客データと注文データが格納された匿名型のコレクションを返すクエリ式を示します。  
  
 [!code-vb[VbVbalrIntroToLINQ#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_6.vb)]  
  
 `Group Join` 句を使用して、顧客オブジェクトのコレクションを格納する階層的なクエリ結果を作成できます。 各顧客オブジェクトには、その顧客のすべての注文のコレクションを含むプロパティがあります。 次のコード例は、顧客データと注文データを階層的な結果として結合し、匿名型のコレクションを返すクエリ式を示します。 このクエリは、顧客の注文データのコレクションを格納する `CustomerOrders` プロパティを含む型を返します。 その顧客のすべての注文の合計を格納する `OrderTotal` プロパティも含まれます  (このクエリは、LEFT OUTER JOIN と同等です)。  
  
 [!code-vb[VbVbalrIntroToLINQ#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_7.vb)]  
  
 上記以外にも、強力なクエリ式を作成するために使用できる、さまざまな LINQ クエリ演算子があります。 このトピックの次のセクションで、クエリ式で使用できるさまざまなクエリ句について説明します。 詳細については[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]クエリ句を参照してください[クエリ](../../../../visual-basic/language-reference/queries/queries.md)です。  
  
##  <a name="VisualBasicLINQQueryOperators"></a>Visual Basic LINQ クエリ演算子  
 LINQ クエリをサポートする <xref:System.Linq> 名前空間とその他の名前空間のクラスには、アプリケーションの要件に基づいてクエリの作成と絞り込みを行うために呼び出すことができるメソッドが含まれています。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] には、最も一般的なクエリ句のキーワードが用意されています。これらについて、次の表で説明します。  
  
|用語|定義|  
|---|---|  
|[From 句](../../../../visual-basic/language-reference/queries/from-clause.md)|クエリを開始するには、`From` 句または `Aggregate` 句のいずれかが必要です。 `From` 句は、クエリのソース コレクションと反復変数を指定します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#7](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_8.vb)]|  
|[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)|任意。 クエリの反復変数のセットを宣言します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#8](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_9.vb)]<br /><br /> `Select` 句の指定がない場合、クエリの反復変数は、`From` 句または `Aggregate` 句で指定された反復変数で構成されます。|  
|[WHERE 句](../../../../visual-basic/language-reference/queries/where-clause.md)|任意。 クエリのフィルター処理条件を指定します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#9](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_10.vb)]|  
|[Order By 句](../../../../visual-basic/language-reference/queries/order-by-clause.md)|任意。 クエリ内に列の並べ替え順序を指定します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#10](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_11.vb)]|  
|[Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)|任意。 2 つのコレクションを単一のコレクションに結合します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_12.vb)]|  
|[Group By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)|任意。 クエリ結果の要素をグループ化します。 これを使用して、グループごとに集計関数を適用できます。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_13.vb)]|  
|[Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)|任意。 2 つのコレクションを、単一の階層コレクションに結合します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_14.vb)]|  
|[Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)|クエリを開始するには、`From` 句または `Aggregate` 句のいずれかが必要です。 `Aggregate` 句は、1 つ以上の集計関数をコレクションに適用します。 たとえば、`Aggregate` 句を使用して、クエリで返されたすべての要素の合計を計算できます。<br /><br /> [!code-vb[VbVbalrIntroToLINQ#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_15.vb)]<br /><br /> `Aggregate` 句を使用してクエリを変更することもできます。 たとえば、`Aggregate` 句を使用して、関連するクエリ コレクションに対して計算を実行できます。<br /><br /> [!code-vb[VbVbalrIntroToLINQ#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_16.vb)]|  
|[Let 句](../../../../visual-basic/language-reference/queries/let-clause.md)|任意。 値を計算し、その値をクエリ内の新しい変数に代入します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_17.vb)]|  
|[Distinct 句](../../../../visual-basic/language-reference/queries/distinct-clause.md)|任意。 現在の反復変数の値を制限して、クエリ結果内で重複する値を除去します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#17](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_18.vb)]|  
|[Skip 句](../../../../visual-basic/language-reference/queries/skip-clause.md)|任意。 コレクション内の指定された数の要素をバイパスし、残りの要素を返します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#18](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_19.vb)]|  
|[Skip While 句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)|任意。 指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#19](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_20.vb)]|  
|[Take 句](../../../../visual-basic/language-reference/queries/take-clause.md)|任意。 コレクションの先頭から、指定された数の連続する要素を返します。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#20](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_21.vb)]|  
|[Take While 句](../../../../visual-basic/language-reference/queries/take-while-clause.md)|任意。 指定された条件が `true` である限り、コレクションの要素を含むようにし、残りの要素をバイパスします。 例:<br /><br /> [!code-vb[VbVbalrIntroToLINQ#21](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_22.vb)]|  
  
 詳細については[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]クエリ句を参照してください[クエリ](../../../../visual-basic/language-reference/queries/queries.md)です。  
  
 LINQ によって提供される列挙可能でクエリ可能な型のメンバーを呼び出すことで、追加の LINQ クエリ機能を使用できます。 これらの追加機能は、クエリ式の結果に対して特定のクエリ演算子を呼び出すことで使用できます。 たとえば、次のコード例では、<xref:System.Linq.Enumerable.Union%2A> メソッドを使用して、2 つのクエリの結果を、1 つのクエリ結果に結合します。 また、<xref:System.Linq.Enumerable.ToList%2A> メソッドを使用して、クエリ結果をジェネリック リストとして返します。  
  
 [!code-vb[VbVbalrIntroToLINQ#22](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/introduction-to-linq_23.vb)]  
  
 追加の LINQ 機能に関する詳細については、「[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)です。  
  
##  <a name="ConnectingToADatabase"></a>LINQ to SQL を使用して、データベースに接続します。  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では、アクセスする SQL Server データベース オブジェクト (テーブル、ビュー、ストアド プロシージャなど) を、LINQ to SQL ファイルを使用して識別します。 LINQ to SQL ファイルには、.dbml という拡張子が付きます。  
  
 SQL Server データベースに有効な接続がある場合はときに、追加できます、 **LINQ to SQL クラス**をプロジェクトに項目テンプレート。 これを行うと、オブジェクト リレーショナル デザイナー (O/R デザイナー) が表示されます。 O/R デザイナーを使用する、コード内でアクセスする項目をドラッグすると、**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**デザイナー画面にします。 LINQ to SQL ファイルは、<xref:System.Data.Linq.DataContext> オブジェクトをプロジェクトに追加します。 このオブジェクトには、アクセスするテーブルとビューのプロパティおよびコレクションと、呼び出すストアド プロシージャのメソッドが格納されます。 変更を LINQ to SQL (.dbml) ファイルに保存した後、O/R デザイナーで定義された <xref:System.Data.Linq.DataContext> オブジェクトを参照することで、コード内でこれらのオブジェクトにアクセスできます。 プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトには、LINQ to SQL ファイルの名前に基づいて名前が付けられます。 たとえば、Northwind.dbml という名前の LINQ to SQL ファイルの場合は、<xref:System.Data.Linq.DataContext> という名前の `NorthwindDataContext` オブジェクトが作成されます。  
  
 詳細な手順と例については、次を参照してください。[する方法: データベースを照会する](../../../../visual-basic/programming-guide/language-features/linq/how-to-query-a-database-by-using-linq.md)と[する方法: ストアド プロシージャを呼び出す](../../../../visual-basic/programming-guide/language-features/linq/how-to-call-a-stored-procedure-by-using-linq.md)です。  
  
##  <a name="VisualBasicFeaturesThatSupportLINQ"></a>Visual Basic の LINQ をサポートする機能します。  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] には、LINQ の使用を単純化し、LINQ クエリを実行するために記述する必要があるコードの量を減らすことができる、注目に値する機能が他にもあります。 次に例を示します。  
  
-   **匿名型**、クエリ結果に基づく新しい型を作成することができます。  
  
-   **暗黙的に型指定される変数**延期して、型を指定することができます、let、コンパイラがクエリ結果に基づき型を推論します。  
  
-   **拡張メソッド**、型自体を変更することがなく、独自のメソッドで既存の種類を拡張することができます。  
  
 詳細については、「 [Visual Basic の機能をサポート LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md)です。  
  
##  <a name="QueryExecution"></a>クエリ遅延に、即時実行  
 クエリの実行とクエリの作成は分離しています。 クエリを作成した後、その実行は、別のメカニズムによってトリガーされます。 定義されていると、すぐにクエリを実行することができます (*即時実行*)、または定義を保存して後でクエリを実行することができます (*遅延実行*)。  
  
 既定では、クエリを作成しても、クエリ自体が直ちに実行されることはありません。 代わりに、クエリ結果を参照するために使用される変数にクエリ定義が格納されます。 そのクエリ結果変数が、後でコード内の `For…Next` ループなどでアクセスされると、クエリが実行されます。 このプロセスと呼びます*遅延実行*です。  
  
 定義されていると呼ばれるときに、クエリを実行することも*即時実行*です。 即時実行は、クエリ結果の個々の要素にアクセスする必要があるメソッドを適用することで開始できます。 `Count`、`Sum`、`Average`、`Min`、`Max` などの集計関数を含めることで、この結果を得ることができます。 集計関数の詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)です。  
  
 `ToList` メソッドまたは `ToArray` メソッドを使用することでも、即時実行を開始できます。 これは、クエリを直ちに実行し、結果をキャッシュする場合に役に立ちます。 これらのメソッドの詳細については、次を参照してください。[データ型の変換](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)です。  
  
 クエリの実行の詳細については、次を参照してください。[書き込み、最初の LINQ クエリの](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
##  <a name="XMLInVisualBasic"></a>Visual Basic における XML  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] における XML の機能には、XML リテラルと XML 軸プロパティがあります。これらを使用して、コード内で XML を簡単に作成、アクセス、照会、および変更できます。 XML リテラルを使用すると、XML をコード内に直接記述できます。 Visual Basic コンパイラは、XML を、最初のクラスのデータ オブジェクトとして処理します。  
  
 次のコード例は、XML 要素を作成し、そのサブ要素と属性にアクセスし、LINQ を使用してその要素の内容を照会する方法を示しています。  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/introduction-to-linq_24.vb)]  
  
 詳細については、次を参照してください。 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)です。  
  
##  <a name="RelatedResources"></a>関連リソース  
  
|トピック|説明|  
|---|---|  
|[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)|[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] における XML の機能について説明します。これらの機能を使用して照会を行い、XML を最初のクラスのデータ オブジェクトとして [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コード内に記述できます。|  
|[クエリ](../../../../visual-basic/language-reference/queries/queries.md)|[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で使用できるクエリ句のリファレンス情報を示します。|  
|[統合言語クエリ (LINQ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)|LINQ の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|LINQ to SQL の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)|LINQ to Objects の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to ADO.NET (ポータル ページ)](http://msdn.microsoft.com/library/dd7d3c6a-ff98-47e9-a1a7-2d4cfc42d150)|LINQ to [!INCLUDE[vstecado](~/includes/vstecado-md.md)] の概要、プログラミング ガイド、およびサンプルへのリンクを示します。|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)|LINQ to XML の概要、プログラミング ガイド、およびサンプルを示します。|  
  
##  <a name="HowToAndWalkthroughTopics"></a>方法とチュートリアルのトピック  
 [方法: データベースの照会](how-to-query-a-database-by-using-linq.md)  
  
 [方法 : ストアド プロシージャの呼び出し](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [方法: データベースのデータの変更](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [方法 : 結合を使用したデータの結合](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [方法: クエリ結果を並べ替える](how-to-sort-query-results-by-using-linq.md)  
  
 [方法 : クエリ結果のフィルター処理](how-to-filter-query-results-by-using-linq.md)  
  
 [方法 : データの数、合計、または平均の算出](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [方法 : クエリ結果内の最小値と最大値の検索](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [方法: 更新、挿入、および削除 (O/R デザイナー) を実行するストアド プロシージャを割り当てる](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)  
  
## <a name="featured-book-chapters"></a>参考書籍の該当する章  
 [Chapter 17: LINQ](http://go.microsoft.com/fwlink/?LinkId=195277)で[Programming Visual Basic 2008](http://go.microsoft.com/fwlink/?LinkId=195383)  
  
## <a name="see-also"></a>参照  
 [統合言語クエリ (LINQ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Visual Basic における LINQ to XML の概要](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [LINQ to DataSet の概要](../../../../framework/data/adonet/linq-to-dataset-overview.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Visual Studio の LINQ to SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
