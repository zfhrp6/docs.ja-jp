---
title: "初めて LINQ クエリ (Visual Basic) の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 48f1c5e15654580b6e4d060860a0d7001af5e2ef
ms.lasthandoff: 03/13/2017

---
# <a name="writing-your-first-linq-query-visual-basic"></a>初めての LINQ クエリの作成 (Visual Basic)
A*クエリ*データ ソースからデータを取得する式を指定します。 クエリは専用のクエリ言語で表されます。 時間の経過と共にさまざまな言語に合わせて開発されたデータ ソースの種類などのリレーショナル データベース用の SQL や XML 用の XQuery です。 これにより、データ ソースまたはサポートされているデータ形式の種類ごとに新しいクエリ言語を習得するアプリケーション開発者にとって必要です。  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]データ ソースや形式のさまざまな種類のデータを操作するための一貫したモデルを提供することで、状態の情報を簡単になります。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリでは、操作の対象は常にオブジェクトになります。 同じ基本的なコーディング パターンを使用して、クエリの XML ドキュメント内のデータ、SQL データベース、ADO.NET データセット、エンティティ、.NET Framework のコレクションと、その他のソースや形式を変換する、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]プロバイダーは、使用できます。 このドキュメントは、3 つのフェーズの作成と basic の使用について説明します。[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリ。  
  
## <a name="three-stages-of-a-query-operation"></a>クエリ操作の&3; つの段階  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリ操作は、3 つのアクションで構成されます。  
  
1.  データ ソースをソースを取得します。  
  
2.  クエリを作成します。  
  
3.  クエリを実行します。  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリの実行は、クエリの作成とは異なります。 クエリを作成するだけでは、すべてのデータは取得しません。 このポイントは、このトピックで後で詳しく説明します。  
  
 次の例は、クエリ操作の&3; つの部分を示しています。 例では、デモンストレーションを目的としての有用なデータ ソースとして整数の配列を使用します。 ただし、同じ概念は、他のデータ ソースにも適用されます。  
  
> [!NOTE]
>  [コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**に**します。  
  
 [!code-vb[VbLINQFirstQuery&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Output:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>データ ソース  
 暗黙的にジェネリックをサポート前の例では、データ ソースが配列であるため、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。 このファクトのデータ ソースとして配列を使用することができますが、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリ。 型をサポートする<xref:System.Collections.Generic.IEnumerable%601>またはジェネリックなどの派生インターフェイス<xref:System.Linq.IQueryable%601>と呼ばれます*クエリ可能型*</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>。  
  
 暗黙的にクエリ可能な型として、配列は必要ありません変更や特別な処理として処理するために、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]データ ソース。 すべてのコレクション型をサポートしている場合も同様です<xref:System.Collections.Generic.IEnumerable%601>、ジェネリックを含む<xref:System.Collections.Generic.List%601>、 <xref:System.Collections.Generic.Dictionary%602>、および .NET Framework クラス ライブラリの他のクラス</xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.IEnumerable%601>。  
  
 ソース データが既に実装されていない場合<xref:System.Collections.Generic.IEnumerable%601>、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]の機能を実装するプロバイダーが必要な*標準クエリ演算子*データ ソースのためです</xref:System.Collections.Generic.IEnumerable%601>。 たとえば、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 、クエリ可能な XML ドキュメントを読み込みの作業を行って<xref:System.Xml.Linq.XElement>の次の例に示すように入力します</xref:System.Xml.Linq.XElement>。 標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)します。  
  
 [!code-vb[VbLINQFirstQuery&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、最初に、オブジェクト リレーショナル マッピング、デザイン時に手動でまたはを使用して作成する、 [LINQ to SQL ツール Visual Studio で](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)Visual Studio でします。 オブジェクトに対するクエリを記述すると、実行時には、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] によってデータベースとの通信が処理されます。 次の例で`customers`データベース、および<xref:System.Data.Linq.Table%601>ジェネリック<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601>をサポートしている</xref:System.Data.Linq.Table%601>特定のテーブルを表します  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 それぞれの種類のデータ ソースを作成する方法の詳細については、対応する [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] プロバイダーのドキュメントを参照してください。 (これらのプロバイダーの一覧は、次を参照してください[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。)。基本的な規則は単純です、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]データ ソースが、ジェネリック<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、またはそれを継承するインターフェイス</xref:System.Collections.Generic.IEnumerable%601>をサポートする任意のオブジェクト。  
  
> [!NOTE]
>  などの型<xref:System.Collections.ArrayList>非ジェネリックをサポートする<xref:System.Collections.IEnumerable>としてインターフェイスを使用することも[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]データ ソース</xref:System.Collections.IEnumerable></xref:System.Collections.ArrayList>。 使用する例については、<xref:System.Collections.ArrayList>を参照してください[方法: LINQ (Visual Basic) で ArrayList を照会](how-to-query-an-arraylist-with-linq.md)</xref:System.Collections.ArrayList>。  
  
## <a name="the-query"></a>クエリ  
 クエリでは、データ ソースまたはソースから取得する情報を指定します。 どのように情報をする必要があります、グループ化、並べ替えたりするが返る前に構造化を指定するオプションもあります。 クエリの作成を有効にするには、Visual Basic は、言語に新しいクエリ構文を組み込まいます。  
  
 次の例では、クエリでは、整数の配列からすべての偶数が返されますが実行される`numbers`します。  
  
 [!code-vb[VbLINQFirstQuery&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 クエリ式には、次の&3; つの句が含まれています: `From`、 `Where`、および`Select`です。 特定の機能と各クエリ式の句の目的は、後ほど[基本的なクエリ操作 (Visual Basic)](basic-query-operations.md)します。 詳細については、次を参照してください。[クエリ](../../../../visual-basic/language-reference/queries/queries.md)します。 において[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]、クエリ定義多くの場合は、変数に格納し、後で実行します。 クエリ変数など、`evensQuery`前の例では、クエリ可能な型である必要があります。 型`evensQuery`は`IEnumerable(Of Integer)`、ローカル型推論を使用して、コンパイラによって割り当てられています。  
  
 ことが重要で、クエリ変数自体は何も起こりませんとデータは返されません。 また、クエリの定義のみ格納されます。 前の例では、`For Each`クエリを実行するループします。  
  
## <a name="query-execution"></a>クエリの実行  
 クエリの実行は、クエリの作成とは別です。 クエリの作成には、クエリが定義されますが、実行は、別のメカニズムによってトリガーされます。 定義されていると、すぐには、クエリを実行することができます (*即時実行*)、または定義を保存して後でクエリを実行することができます (*遅延実行*)。  
  
### <a name="deferred-execution"></a>遅延実行  
 標準的な[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリに似ていますが、これで、前の例で`evensQuery`が定義されています。 クエリが作成されますが、実行は行いませんすぐに。 クエリ定義は、クエリ変数に格納する代わりに、`evensQuery`です。 クエリを実行した後で、通常を使用して、`For Each`またはなど、標準クエリ演算子を適用することで、値のシーケンスを返すループ`Count`または`Max`です。 このプロセスと呼ばれます*遅延実行*します。  
  
 [!code-vb[VbLINQFirstQuery&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 値のシーケンスに反復変数を使用して取得したデータにアクセスする、`For Each`ループ (`number`前の例では)。 クエリ変数`evensQuery`クエリの結果ではなく、クエリ定義を保持して、クエリ変数を&2; 回以上を使用して、必要な頻度にクエリを実行することができます。 たとえば、データベースを別のアプリケーションによって継続的に更新されているアプリケーションでがあります。 そのデータベースからデータを取得するクエリを作成する後は、使用、`For Each`たびに、最新のデータを取得するクエリを繰り返し実行するループ処理します。  
  
 次の例では、遅延実行の動作です。 後に`evensQuery2`が定義され、使用して実行される、`For Each`データ ソースの一部の要素を前の例では、ループ、`numbers`変更されます。 1 秒間に、`For Each`ループを実行`evensQuery2`再度します。 結果は異なって、2 回目、`For Each`ループが実行されるクエリ、新しい値を使用する`numbers`です。  
  
 [!code-vb[VbLINQFirstQuery&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Output:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>即時実行  
 クエリの遅延実行では、クエリ定義は、後で実行するクエリ変数に格納されます。 即時実行は、その定義の時点で、クエリが実行されます。 クエリ結果の個々 の要素へのアクセスを必要とするメソッドを適用すると、実行がトリガーされます。 単一の値を返す、標準クエリ演算子の&1; つを使用して強制的に多くの場合、即時に実行されます。 Examples are `Count`, `Max`, `Average`, and `First`. これらの標準クエリ演算子は、計算して単一の結果を返すために適用されるとすぐにクエリを実行します。 1 つの値を返す標準クエリ演算子の詳細については、次を参照してください。[集計操作](aggregation-operations.md)、[要素操作](element-operations.md)、および[量指定子操作](quantifier-operations.md)します。  
  
 次のクエリでは、整数の配列の中に含まれている偶数の数が返されます。 クエリ定義が保存されていない、および`numEvens`は、単純な`Integer`です。  
  
 [!code-vb[VbLINQFirstQuery&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 使用して同じ結果を得ることができます、`Aggregate`メソッドです。  
  
 [!code-vb[VbLINQFirstQuery&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 呼び出して、クエリの実行を強制できます、`ToList`または`ToArray`クエリ (即時) または次のコードに示すようにクエリ変数 (遅延) のメソッドです。  
  
 [!code-vb[VbLINQFirstQuery&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 前の例で`evensQuery3`クエリは、変数しますですが、`evensList`リストと`evensArray`配列です。  
  
 使用して`ToList`または`ToArray`を強制的に即時実行は、クエリを直ちに実行し、単一のコレクション オブジェクトの結果をキャッシュするシナリオで特に便利です。 これらの方法に関する詳細については、次を参照してください。[データの種類の変換](converting-data-types.md)します。  
  
 使用して実行するクエリが発生することも、`IEnumerable`などのメソッド、<xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>メソッド</xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](getting-started-with-linq.md)   
 [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)
