---
title: "Visual Basic でクエリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: 70
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
ms.openlocfilehash: e870d5d0640c68fa57b07986f2bf8268fd5246c9
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>チュートリアル: Visual Basic でクエリを記述する
このチュートリアルでは、Visual Basic 言語の機能を使用して書き込む方法[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]クエリ式。 このチュートリアルでは、Student オブジェクトのリストに対するクエリを作成する方法、クエリを実行する方法、およびそれらを変更する方法を示します。 クエリでは、オブジェクト初期化子、ローカル型推論、匿名型など、いくつかの機能を組み込みます。  
  
 このチュートリアルを完了すると、サンプルと、特定のドキュメントに移動する準備が完了されます[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]興味のあるプロバイダー。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]プロバイダーには、 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、および[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]です。  
  
## <a name="create-a-project"></a>プロジェクトの作成  
  
#### <a name="to-create-a-console-application-project"></a>コンソール アプリケーション プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。  
  
3.  **インストールされたテンプレート**一覧で、クリックして**Visual Basic**します。  
  
4.  プロジェクトの種類の一覧でクリックして**コンソール アプリケーション**します。 **名**ボックスに、プロジェクトの名前を入力し、 をクリックし、 **OK**します。  
  
     プロジェクトが作成されます。 既定では、System.Core.dll への参照が含まれています。 また、**インポートされた名前空間**ボックスの一覧で、[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)が含まれています、<xref:System.Linq?displayProperty=fullName>名前空間</xref:System.Linq?displayProperty=fullName>。  
  
5.  [コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**に**します。  
  
## <a name="add-an-in-memory-data-source"></a>メモリ内のデータ ソースを追加します。  
 このチュートリアルのクエリのデータ ソースの一覧は、`Student`オブジェクトです。 各`Student`オブジェクトには、名前、姓、学年、および学生全体での学術的な順位が含まれています。  
  
#### <a name="to-add-the-data-source"></a>データ ソースを追加するには  
  
-   定義、`Student`クラスおよびクラスのインスタンスのリストを作成します。  
  
    > [!IMPORTANT]
    >  定義するために必要なコード、`Student`クラスし、使用されてリストの作成のチュートリアルで例が提供される[する方法: リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)します。 そこからコピーし、プロジェクトに貼り付けることができます。 新しいコードは、プロジェクトの作成時に表示されたコードに置き換えます。  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>受講者リストに新しい学生を追加するには  
  
-   パターンに従い、`getStudents`の別のインスタンスを追加するメソッドを`Student`クラスの一覧にします。 受講者の追加が発生するオブジェクト初期化子をします。 詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)します。  
  
## <a name="create-a-query"></a>クエリを作成する  
 実行すると、このセクションで追加のクエリは、学生の成績順位に入れます上位&10; 件のリストを生成します。 クエリは、完全な選択されるので`Student`オブジェクトごとに、クエリ結果の型が`IEnumerable(Of Student)`です。 ただし、クエリの型通常が指定されていないクエリ定義にします。 代わりに、コンパイラはローカル型推論を使用して型を調べます。 詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。 クエリの範囲変数、 `currentStudent`、それぞれへの参照の役割を果たします`Student`、ソース内のインスタンス`students`、内の各オブジェクトのプロパティへのアクセスを提供する`students`です。  
  
#### <a name="to-create-a-simple-query"></a>簡単なクエリを作成するには  
  
1.  内の場所を検索、`Main`次のようにマークされているプロジェクトのメソッド。  
  
     [!code-vb[VbLINQWalkthrough&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     次のコードをコピーし、貼り付けます。  
  
     [!code-vb[VbLINQWalkthrough&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  マウス ポインターを合わせる`studentQuery`コンパイラによって割り当てられた型があることを確認するためにコード`IEnumerable(Of Student)`します。  
  
## <a name="run-the-query"></a>クエリを実行します。  
 変数`studentQuery`クエリの実行結果ではなく、クエリの定義が含まれています。 クエリを実行するための一般的なメカニズムは、`For Each`ループします。 返されるシーケンス内の各要素は、ループの反復変数を通じてアクセスします。 クエリの実行の詳細については、次を参照してください。[書き込みで初めて、の LINQ クエリ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
#### <a name="to-run-the-query"></a>クエリを実行するには  
  
1.  次の追加`For Each`プロジェクト内のクエリの下のループします。  
  
     [!code-vb[VbLINQWalkthrough&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  ループ制御変数にマウス ポインターを置く`studentRecord`にそのデータ型を参照してください。 型`studentRecord`と推論`Student`ので、`studentQuery`のコレクションを返します`Student`インスタンス。  
  
3.  ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を確認します。  
  
## <a name="modify-the-query"></a>クエリを変更します。  
 順序が指定されている場合は、クエリの結果をスキャンしやすくなります。 使用可能なフィールドに基づいて返されるシーケンスを並べ替えることができます。  
  
#### <a name="to-order-the-results"></a>結果の順序  
  
1.  次の追加`Order By`句の間、`Where`ステートメントおよび`Select`クエリのステートメントです。 `Order By`句は結果の順序をアルファベット順に A から z、に従って最後の各受講者の名前。  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  姓、名、姓の順で並べ替えには、クエリを両方のフィールドを追加します。  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     指定することも`Descending`Z から A に注文する  
  
3.  ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を確認します。  
  
#### <a name="to-introduce-a-local-identifier"></a>ローカル識別子を導入するには  
  
1.  クエリ式のローカル識別子を導入するには、このセクションで、コードを追加します。 ローカルの識別子では、中間結果を保持します。 次の例で`name`の生徒の連結を保持する識別子の最初と姓と名です。 複数回計算するわけではそれ以外の場合、式の結果を格納することでパフォーマンスの向上につながります。 または便宜のため、ローカル識別子を使用できます。  
  
     [!code-vb[VbLINQWalkthrough&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を確認します。  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Select 句で&1; つのフィールドを射影するには  
  
1.  クエリに追加し、`For Each`ソース内の要素とは異なる要素のシーケンスを生成するクエリを作成するには、このセクションのループします。 次の例では、ソースを集めたもの`Student`オブジェクトではなく各オブジェクトの&1; メンバーのみが返されます。 姓が Garcia 学生の姓。 `currentStudent.First`によって返されるシーケンスのデータ型の文字列`studentQuery3`は`IEnumerable(Of String)`文字列のシーケンス。 前の例と同様に、データの割り当てがの入力`studentQuery3`コンパイラ ローカル型推論を使用して確認するのには残されます。  
  
     [!code-vb[VbLINQWalkthrough&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  マウス ポインターを合わせる`studentQuery3`割り当てられた型があることを確認するためにコード`IEnumerable(Of String)`します。  
  
3.  ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を確認します。  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Select 句で匿名型を作成するには  
  
1.  クエリでどのように匿名型を表示するには、このセクションのコードは使用を追加します。 完全な記録ではなく、データ ソースから複数のフィールドを取得するときにクエリで使用する (`currentStudent`前の例でのレコード) または&1; つのフィールド (`First`前のセクションで)。 内のフィールドを指定する結果に含めるフィールドを含む新しい名前付きの型を定義するには、代わりに、`Select`句と、コンパイラは、それらのフィールドのプロパティとして持つ匿名型を作成します。 詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。  
  
     次の例では、最上級生の成績順位が 1 ~ 10、学術ランクの順序で範囲のランクと名前を返すクエリを作成します。 この例の種類で`studentQuery4`ために、推論する必要があります、`Select`句は、匿名型のインスタンスを返すし、匿名型には、使用可能な名前がありません。  
  
     [!code-vb[VbLINQWalkthrough&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。 コンソール ウィンドウに結果を確認します。  
  
## <a name="additional-examples"></a>その他の例  
 柔軟性を示すためにその他の例の一覧と電源の基本を理解すると、次に示します[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリ。 それぞれの例は、内容の簡単な説明を付けたものです。 推論された型を表示するには、各クエリのクエリ結果変数の上には、マウス ポインターを置きます。 使用して、`For Each`ループを使用して、結果を生成します。  
  
 [!code-vb[VbLINQWalkthrough&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>追加情報  
 特定の種類のドキュメントとサンプルを参照する準備ができたらクエリの基本的な概念を理解したら、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]興味のあるプロバイダー。  
  
 [LINQ to Objects](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)
