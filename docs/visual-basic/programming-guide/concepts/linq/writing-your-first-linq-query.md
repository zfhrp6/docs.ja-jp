---
title: "初めての LINQ クエリの作成 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c16bb28189d5525654328da2dc80d868bbe61bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="writing-your-first-linq-query-visual-basic"></a>初めての LINQ クエリの作成 (Visual Basic)
"*クエリ*" は、データ ソースからデータを取得する式です。 クエリは、専用のクエリ言語で表現されます。 時間の経過と共にさまざまな言語のために開発されたさまざまな種類のデータ ソース、たとえば、リレーショナル データベース用の SQL や XML 用の XQuery です。 これにより、アプリケーション開発者は、データ ソースまたはサポートされているデータ形式の種類ごとに新しいクエリ言語を習得するために必要です。  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]さまざまな種類のデータ ソースやデータ形式のデータを操作するための一貫したモデルを提供することで、この状況を簡単になります。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリでは、操作の対象は常にオブジェクトになります。 同じ基本的なコーディング パターンを使用して、クエリ対象の XML ドキュメント内のデータ、SQL データベース、ADO.NET データセットとエンティティ、.NET Framework のコレクションと、その他のソースまたは形式を変換する、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]プロバイダーが用意されています。 このドキュメントは、作成の 3 つの段階と basic の使用について説明します。[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。  
  
## <a name="three-stages-of-a-query-operation"></a>クエリ操作の 3 つの段階  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ操作は、3 つのアクションで構成されます。  
  
1.  データ ソースを取得します。  
  
2.  クエリを作成します。  
  
3.  クエリを実行します。  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリの実行は、クエリの作成とは異なります。 クエリを作成するだけでは、すべてのデータは取得しません。 この点については、後で詳しく説明します。  
  
 次の例は、クエリ操作の 3 つの部分を示しています。 例では、デモの目的の便利なデータ ソースとして整数の配列を使用します。 ただし、同じ概念は、他のデータ ソースにも適用されます。  
  
> [!NOTE]
>  [コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**で**です。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Output:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>データ ソース  
 前の例では、データ ソースは、配列であるため、暗黙的をサポートしているジェネリック<xref:System.Collections.Generic.IEnumerable%601>インターフェイスです。 このファクトのデータ ソースとしての配列を使用することができますが、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 <xref:System.Collections.Generic.IEnumerable%601> をサポートする型や、ジェネリック <xref:System.Linq.IQueryable%601> などの派生インターフェイスは、*クエリ可能型*と呼ばれます。  
  
 暗黙的にクエリ可能型として、配列は不要変更や特別な処理として機能するように、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データ ソース。 サポートする任意のコレクション型の場合も同様です<xref:System.Collections.Generic.IEnumerable%601>、ジェネリックを含む<xref:System.Collections.Generic.List%601>、 <xref:System.Collections.Generic.Dictionary%602>、および .NET Framework クラス ライブラリの他のクラスです。  
  
 ソース データが既に実装しない場合<xref:System.Collections.Generic.IEnumerable%601>、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]の機能を実装するプロバイダーが必要な*標準クエリ演算子*そのデータ ソースのです。 たとえば、 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 、クエリ可能な XML ドキュメントを読み込みの作業を行って<xref:System.Xml.Linq.XElement>の次の例に示すように入力します。 標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)です。  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、最初に、オブジェクト リレーショナル マッピング、デザイン時に手動でまたはを使用して作成する、 [LINQ to Visual Studio での SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)Visual Studio でします。 オブジェクトに対するクエリを記述すると、実行時には、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] によってデータベースとの通信が処理されます。 次の例では、 `customers` 、データベース内の特定のテーブルを表すと<xref:System.Data.Linq.Table%601>サポート ジェネリック<xref:System.Linq.IQueryable%601>です。  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 それぞれの種類のデータ ソースを作成する方法の詳細については、対応する [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プロバイダーのドキュメントを参照してください。 (これらのプロバイダーの一覧は、次を参照してください[クエリ (LINQ: Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。)。基本的な規則は簡単:[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データ ソースは、ジェネリックをサポートする任意のオブジェクト<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、またはそこから継承するインターフェイスです。  
  
> [!NOTE]
>  などの型<xref:System.Collections.ArrayList>、非ジェネリックをサポートする<xref:System.Collections.IEnumerable>としてインターフェイスを使用することも[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データ ソース。 使用する例については、<xref:System.Collections.ArrayList>を参照してください[する方法: LINQ (Visual Basic) で ArrayList を照会](how-to-query-an-arraylist-with-linq.md)です。  
  
## <a name="the-query"></a>クエリ  
 クエリでは、データ ソースまたはソースから取得する情報を指定します。 方法については、必要があります、グループ化、並べ替えたりするが返る前に構造化を指定するオプションもがあります。 クエリの作成を有効にするには、Visual Basic は、言語にで新しいクエリ構文に組み込みます。  
  
 次の例では、クエリが、整数の配列からすべての偶数を返しますが実行される`numbers`です。  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 クエリ式には、次の 3 つの句が含まれています: `From`、 `Where`、および`Select`です。 各クエリ式の句の目的は、特定の関数は、後ほど[基本的なクエリ操作 (Visual Basic)](basic-query-operations.md)です。 詳細については、次を参照してください。[クエリ](../../../../visual-basic/language-reference/queries/queries.md)です。 において[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]、クエリ定義多くの場合は変数に格納し、後で実行します。 クエリ変数など、`evensQuery`前の例では、クエリ可能な型である必要があります。 型`evensQuery`は`IEnumerable(Of Integer)`ローカル型推論を使用して、コンパイラによって割り当てられた、します。  
  
 クエリ変数自体は何も処理され、データは返されませんに重要です。 クエリの定義のみ格納されます。 前の例では、`For Each`クエリを実行するループします。  
  
## <a name="query-execution"></a>クエリの実行  
 クエリの実行はクエリの作成とは別です。 クエリの作成、クエリを定義していますが、実行は、別のメカニズムによってトリガーされます。 定義されていると、すぐにクエリを実行することができます (*即時実行*)、または定義を保存して後でクエリを実行することができます (*遅延実行*)。  
  
### <a name="deferred-execution"></a>遅延実行  
 一般的な[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリに似ていますが、これで、前の例で`evensQuery`が定義されています。 クエリが作成されますにすぐには実行されません。 クエリ定義は、クエリ変数に格納する代わりに、`evensQuery`です。 クエリを実行した後で、通常を使用して、`For Each`またはなど、標準クエリ演算子を適用することで、値のシーケンスを返すループ`Count`または`Max`です。 このプロセスと呼びます*遅延実行*です。  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 値のシーケンスで反復変数を使用して取得したデータにアクセスする、`For Each`ループ (`number`前の例で)。 クエリ変数`evensQuery`クエリの結果ではなく、クエリの定義を保持して、クエリ変数を 1 つ以上の時間を使用して、必要な頻度、クエリを実行することができます。 たとえば、データベースを別のアプリケーションによって頻繁に更新されているアプリケーションでがあります。 使用することがそのデータベースからデータを取得するクエリを作成した後、`For Each`たびに、最新のデータを取得するクエリを繰り返し実行する、ループします。  
  
 次の例では、遅延実行の動作です。 後に`evensQuery2`定義および使用して実行されて、`For Each`データ ソースの一部の要素を前の例では、ループ、`numbers`変更されます。 1 秒あたりにし、`For Each`ループを実行`evensQuery2`もう一度です。 結果は異なる、2 回目ため、`For Each`ループ、クエリが再実行の新しい値を使用して`numbers`です。  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Output:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>即時実行  
 クエリの遅延実行は、クエリの定義は後で実行するクエリ変数に格納されます。 即時実行は、その定義の時点で、クエリが実行されます。 実行は、クエリの結果の個々 の要素へのアクセスを必要とするメソッドを適用するときにトリガーされます。 1 つの値を返す標準クエリ演算子の 1 つを使用して強制的に多くの場合、即時に実行されます。 例としては、 `Count`、 `Max`、 `Average`、および`First`です。 これらの標準クエリ演算子は、計算を単一の結果を返すために適用されるとすぐにクエリを実行します。 標準クエリ演算子の 1 つの値を返すことの詳細については、次を参照してください。[集計操作](aggregation-operations.md)、[要素操作](element-operations.md)、および[量指定子操作](quantifier-operations.md)です。  
  
 次のクエリは、整数の配列に偶数の数を返します。 クエリの定義は保存されず、および`numEvens`、単純なの`Integer`します。  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 使用して同じ結果を得ることができます、`Aggregate`メソッドです。  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 呼び出して、クエリの実行を強制することもできます、`ToList`または`ToArray`クエリ (即時) または、次のコードに示すように、(遅延)、クエリ変数にメソッドです。  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 前の例で`evensQuery3`クエリは、変数ですが`evensList`一覧と`evensArray`配列です。  
  
 使用して`ToList`または`ToArray`を強制的に即時実行はすぐにクエリを実行し、1 つのコレクション オブジェクトに結果をキャッシュするシナリオで特に便利です。 これらのメソッドの詳細については、次を参照してください。[データ型の変換](converting-data-types.md)です。  
  
 使用して実行するクエリが発生することも、`IEnumerable`などのメソッド、<xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の LINQ の概要](getting-started-with-linq.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)
