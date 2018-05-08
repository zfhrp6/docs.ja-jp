---
title: Visual Basic でクエリを記述します。
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: beb192f6b136455cb1adcb6cf2616578b63fcebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>チュートリアル: Visual Basic でクエリを記述する
このチュートリアルでは、書き込みを Visual Basic 言語の機能を使用する方法を示しています[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]クエリ式。 このチュートリアルでは、Student オブジェクトの一覧にクエリを作成する方法、クエリを実行する方法、およびそれらを変更する方法について説明します。 クエリでは、オブジェクト初期化子、ローカル型推論、および匿名型を含むいくつかの機能を組み込みます。  
  
 このチュートリアルを完了すると、サンプルと、特定のドキュメントに移動する準備ができてされます[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]興味のあるプロバイダー。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プロバイダーが含まれます[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]、および[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]です。  
  
## <a name="create-a-project"></a>プロジェクトの作成  
  
#### <a name="to-create-a-console-application-project"></a>コンソール アプリケーション プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  **インストールされたテンプレート**一覧で、クリックして**Visual Basic**です。  
  
4.  プロジェクトの種類の一覧でクリックして**コンソール アプリケーション**です。 **名前**ボックスで、プロジェクトの名前を入力し、をクリックして**OK**です。  
  
     プロジェクトが作成されます。 既定では、System.Core.dll への参照が含まれています。 また、**インポートされた名前空間**ボックスの一覧、[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)が含まれています、<xref:System.Linq?displayProperty=nameWithType>名前空間。  
  
5.  [コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**で**です。  
  
## <a name="add-an-in-memory-data-source"></a>メモリ内データ ソースを追加します。  
 このチュートリアルのクエリのデータ ソースの一覧は、`Student`オブジェクト。 各`Student`名、姓、学年、および教育機関のランク、学生の本文にオブジェクトが含まれています。  
  
#### <a name="to-add-the-data-source"></a>データ ソースを追加するには  
  
-   定義、`Student`クラス、およびクラスのインスタンスの一覧を作成します。  
  
    > [!IMPORTANT]
    >  定義に必要なコード、`Student`クラスし、使用するリストを作成のチュートリアルで例が提供される[する方法: リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)です。 そこからコピーし、プロジェクトに貼り付けることができます。 新しいコード プロジェクトを作成するときに表示されたコードで置き換えます。  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>学生のリストに新しい学生を追加するには  
  
-   パターンに従い、`getStudents`の別のインスタンスを追加するメソッドを`Student`リストにクラスです。 受講者を追加することをオブジェクト初期化子が紹介されます。 詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)です。  
  
## <a name="create-a-query"></a>クエリを作成する  
 実行すると、このセクションで追加のクエリは、学生の成績順位に格納上位 10 件のリストを生成します。 クエリは、完全な選択ので`Student`オブジェクトごとに、クエリ結果の型が`IEnumerable(Of Student)`です。 ただし、クエリの種類通常が指定されていないクエリ定義にします。 代わりに、コンパイラは、種類を決定するのにローカル型推論を使用します。 詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。 クエリの範囲変数、 `currentStudent`、それぞれへの参照の役割を果たす`Student`、ソースでインスタンス`students`、内の各オブジェクトのプロパティへのアクセスを提供する`students`です。  
  
#### <a name="to-create-a-simple-query"></a>簡単なクエリを作成するには  
  
1.  内の場所を検索、`Main`次のようにマークされているプロジェクトのメソッド。  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     次のコードをコピーして貼り付けます。  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  マウス ポインターを合わせる`studentQuery`コンパイラによって割り当てられた型があることを確認するコードで`IEnumerable(Of Student)`です。  
  
## <a name="run-the-query"></a>クエリを実行します。  
 変数`studentQuery`クエリ、クエリの実行結果いないの定義が含まれています。 クエリを実行するための一般的なメカニズムは、`For Each`ループします。 返されるシーケンス内の各要素は、ループの反復変数を介してアクセスします。 クエリの実行の詳細については、次を参照してください。[書き込み、最初の LINQ クエリの](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
#### <a name="to-run-the-query"></a>クエリを実行するには  
  
1.  次の追加`For Each`プロジェクトのクエリの下のループします。  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  ループ コントロール変数にマウス ポインターを置く`studentRecord`にそのデータ型を参照してください。 型`studentRecord`と推論されます`Student`ので、`studentQuery`のコレクションを返します`Student`インスタンス。  
  
3.  構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
## <a name="modify-the-query"></a>クエリの変更  
 指定した順序内にある場合、クエリの結果をスキャンすると簡単です。 使用可能なフィールドに基づいて、返されるシーケンスを並べ替えることができます。  
  
#### <a name="to-order-the-results"></a>結果を並べ替えるには  
  
1.  次の追加`Order By`間句、`Where`ステートメントおよび`Select`クエリのステートメント。 `Order By`句は結果の順序をアルファベット順に A から z、に従って最後の各受講者の名前。  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  姓と名、姓で並べ替えするには、クエリに両方のフィールドを追加します。  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     指定することも`Descending`Z から A に注文する  
  
3.  構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
#### <a name="to-introduce-a-local-identifier"></a>ローカル識別子を導入するには  
  
1.  このセクションの内容をクエリ式内のローカル識別子を導入する、コードを追加します。 ローカルの識別子では、中間結果を保持します。 次の例では、`name`学生の連結を保持する識別子の最初と姓と名は、します。 利便性のためのローカル識別子を使用できますか、複数回を計算するそれ以外の場合は、式の結果を格納することでパフォーマンスの向上につながります。  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Select 句で 1 つのフィールドを射影するには  
  
1.  クエリの追加と`For Each`ソース内の要素とは異なる要素のシーケンスを生成するクエリを作成するには、このセクションからループします。 次の例では、ソースでのコレクション`Student`オブジェクトではなく各オブジェクトの 1 メンバーのみが返されます。 姓が Garcia 学生の姓。 `currentStudent.First`文字列、によって返されるシーケンスのデータ型は、`studentQuery3`は`IEnumerable(Of String)`文字列のシーケンス。 以前の例のように、データの割り当てを入力`studentQuery3`コンパイラ ローカル型推論を使用して判別するためのままです。  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  マウス ポインターを合わせる`studentQuery3`割り当ての種類があることを確認するようにコードで`IEnumerable(Of String)`です。  
  
3.  構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Select 句で匿名型を作成するには  
  
1.  匿名型を表示するには、このセクションのコードは、クエリで使用するを追加します。 完全なレコードではなく、データ ソースから複数のフィールドを取得するときにクエリで使用する (`currentStudent`前の例でレコード) 1 つのフィールド (`First`前のセクションで)。 内のフィールドを指定する結果に含めるフィールドを含んでいる新しい名前付きの型を定義するには、代わりに、`Select`句と、コンパイラは、それらのフィールドのプロパティとして持つ匿名型を作成します。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例では、成績順位は 1 ~ 10、教育機関のランクの順序で行ったりのランクと名前を返すクエリを作成します。 この例では、型で`studentQuery4`ために、推論する必要があります、`Select`句は、匿名型のインスタンスを返すし、匿名型には、使用可能な名前がありません。  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を注意してください。  
  
## <a name="additional-examples"></a>その他の例  
 電源と柔軟性を説明するためにその他の例の一覧を次に示します基本を理解すると、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 それぞれの例は、内容の簡単な説明続きます。 推論された型を表示するには、各クエリのクエリ結果の変数の上には、マウス ポインターを置きます。 使用して、`For Each`ループを使用して、結果を生成します。  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>追加情報  
 特定の種類のドキュメントおよびサンプルを読み取る準備ができたらのクエリの基本的な概念を理解したら、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]興味のあるプロバイダー。  
  
 [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [オブジェクト初期化子 : 名前付きの型と匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)
