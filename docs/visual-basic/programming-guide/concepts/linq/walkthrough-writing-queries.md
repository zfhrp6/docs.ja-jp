---
title: "チュートリアル: Visual Basic でクエリを記述する | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "クエリ [Visual Basic での LINQ], 作成"
  - "LINQ [Visual Basic], チュートリアル"
  - "LINQ [Visual Basic], クエリの作成"
  - "記述 (LINQ クエリを) [Visual Basic]"
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: 70
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 68
---
# チュートリアル: Visual Basic でクエリを記述する
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このチュートリアルでは、Visual Basic 言語の機能を使用して [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] クエリ式を記述する方法について説明します。  ここでは、Student オブジェクトのリストの作成方法、クエリの実行方法、およびクエリの変更方法を示します。  クエリには、オブジェクト初期化子、ローカル型の推論、匿名型など、Visual Basic 2008 で新たに導入された機能が組み込まれています。  
  
 このチュートリアルを完了したら、関心のある特定の [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーのサンプルやドキュメントに進むことができます。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーには、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)]、[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/linq-query-expressions/includes/linq-dataset-md.md)]、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] などがあります。  
  
## プロジェクトの作成  
  
#### コンソール アプリケーション プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  **\[インストールされているテンプレート\]** の **\[Visual Basic\]** をクリックします。  
  
4.  プロジェクトの種類の一覧の **\[コンソール アプリケーション\]** をクリックします。  **\[プロジェクト名\]** ボックスにプロジェクトの名前を入力し、**\[OK\]** をクリックします。  
  
     プロジェクトが作成されます。  プロジェクトには、System.Core.dll への参照が既定で含まれます。  また、[\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic) の **\[インポートされた名前空間\]** の一覧には、<xref:System.Linq?displayProperty=fullName> 名前空間が含まれます。  
  
5.  [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)で、**\[Option Infer\]** がに設定されていることを確認します。  
  
## インメモリ データ ソースの追加  
 このチュートリアルのクエリのデータ ソースは、`Student` オブジェクトのリストです。  各 `Student` オブジェクトには、名、姓、学年、および学生全体における成績順位が含まれます。  
  
#### データ ソースを追加するには  
  
-   `Student` クラスを定義し、そのクラスのインスタンスのリストを作成します。  
  
    > [!IMPORTANT]
    >  このチュートリアルの例で使用する `Student` クラスの定義とリストの作成に必要なコードは、「[How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)」に記載されています。  そこからコードをコピーし、プロジェクトに貼り付けることができます。  プロジェクトの作成時に表示されたコードを、新しいコードで置き換えます。  
  
#### 学生のリストに新しい学生を追加するには  
  
-   `getStudents` メソッドのパターンに従って、`Student` クラスの別のインスタンスをリストに追加します。  学生を追加すると、オブジェクト初期化子が導入されます。  詳細については、「[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)」を参照してください。  
  
## クエリの作成  
 このセクションで追加したクエリが実行されると、成績順位が上位 10 人に入る学生のリストが生成されます。  クエリは毎回完全な `Student` オブジェクトを選択するので、クエリ結果の型は `IEnumerable(Of Student)` になります。  ただし、通常はクエリ定義にクエリの型を指定することはありません。  代わりに、コンパイラがローカル型の推論を使用して型を判断します。  詳細については、「[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。  クエリの範囲変数である `currentStudent` は、ソース `students` 内の各 `Student` インスタンスへの参照として機能します。これにより、`students` 内の各オブジェクトのプロパティにアクセスできるようになります。  
  
#### 簡単なクエリを作成するには  
  
1.  プロジェクトの `Main` メソッドで、次のようにマークされている場所を探します。  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/walkthrough-writing-quer_1_1.vb)]  
  
     次のコードをコピーして貼り付けます。  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/walkthrough-writing-quer_1_2.vb)]  
  
2.  マウス ポインターをコード内の `studentQuery` の上に置き、コンパイラが割り当てた型が `IEnumerable(Of Student)` であることを確認します。  
  
## クエリの実行  
 変数 `studentQuery` には、クエリの実行結果ではなく、クエリの定義が含まれます。  通常、クエリの実行には `For Each` ループが使用されます。  返されたシーケンス内の各要素へは、ループの反復変数を通じてアクセスします。  クエリ実行の詳細については、「[初めての LINQ クエリの作成](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)」を参照してください。  
  
#### クエリを実行するには  
  
1.  プロジェクト内のクエリの下に、次の `For Each` ループを追加します。  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/walkthrough-writing-quer_1_3.vb)]  
  
2.  マウス ポインターをループ制御変数 `studentRecord` の上に置き、データ型を確認します。  `studentQuery` は `Student` インスタンスのコレクションを返すので、`studentRecord` の型は `Student` であると推論されます。  
  
3.  Ctrl キーを押しながら F5 キーを押して、アプリケーションをビルドおよび実行します。  コンソール ウィンドウで結果を確認します。  
  
## クエリの変更  
 クエリ結果が指定した順序で並んでいると、結果のスキャンが簡単になります。  使用可能な任意のフィールドに基づいて、返されるシーケンスを並べ替えることができます。  
  
#### 結果を順序に従って並べるには  
  
1.  次の `Order By` 句を、クエリの `Where` ステートメントと `Select` ステートメントの間に追加します。  この `Order By` 句は、結果を各生徒の姓のアルファベット順 \(A から Z\) に並べます。  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  名、姓の順に従って並べるには、両方のフィールドをクエリに追加します。  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     `Descending` を指定すると、Z から A の順に並べることもできます。  
  
3.  Ctrl キーを押しながら F5 キーを押して、アプリケーションをビルドおよび実行します。  コンソール ウィンドウで結果を確認します。  
  
#### ローカル識別子を導入するには  
  
1.  クエリ式にローカル識別子を取り入れるには、このセクションのコードを追加します。  ローカル識別子には、中間結果が保持されます。  次の例の `name` は、学生の名前と姓を連結したものを保持する識別子です。  ローカル識別子は、利便性のために使用できるほか、式の結果が格納されるので何度も計算を行う必要がなくなり、パフォーマンスの向上につながります。  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/walkthrough-writing-quer_1_4.vb)]  
  
2.  Ctrl キーを押しながら F5 キーを押して、アプリケーションをビルドおよび実行します。  コンソール ウィンドウで結果を確認します。  
  
#### Select 句で 1 つのフィールドを投影するには  
  
1.  ソース内の要素とは異なる要素のシーケンスを生成するクエリを作成するには、このセクションのクエリと `For Each` ループを追加します。  次の例では、ソースは `Student` オブジェクトのコレクションですが、返されるのは各オブジェクトの 1 つのメンバーだけです。この場合は、Garcia という姓を持つ学生の名だけが返されます。  `currentStudent.First` は文字列なので、`studentQuery3` が返すシーケンスのデータ型は `IEnumerable(Of String)` \(文字列のシーケンス\) になります。  前の例のように、`studentQuery3` に対するデータ型の割り当ては、コンパイラによってローカル型の推論を使用して決定されます。  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/walkthrough-writing-quer_1_5.vb)]  
  
2.  マウス ポインターをコード内の `studentQuery3` の上に置き、割り当てられた型が `IEnumerable(Of String)` であることを確認します。  
  
3.  Ctrl キーを押しながら F5 キーを押して、アプリケーションをビルドおよび実行します。  コンソール ウィンドウで結果を確認します。  
  
#### Select 句で匿名型を作成するには  
  
1.  クエリで匿名型がどのように使用されるかを確認するには、このセクションのコードを追加します。  これは、クエリで完全なレコード \(前の例の `currentStudent` レコード\) や単一のフィールド \(前の例の `First`\) を返すのではなく、データ ソースからいくつかのフィールドを返す場合に使用します。  、結果に含めるフィールドを含む新しい名前付きの型を定義する代わりに `Select` 句でフィールドを指定すると、コンパイラはそれらのフィールドをプロパティとして持つ匿名型を作成します。詳細については、「[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例では、成績順位が 1 位から 10 位までの最上級生の名前と順位を成績順に返すクエリを作成します。  この例では、`studentQuery4` の型を推論する必要があります。これは、`Select` 句から返されるのは匿名型のインスタンスであり、匿名型には使用できる名前がないためです。  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/walkthrough-writing-quer_1_6.vb)]  
  
2.  Ctrl キーを押しながら F5 キーを押して、アプリケーションをビルドおよび実行します。  コンソール ウィンドウで結果を確認します。  
  
## その他の例  
 これで基本的な事項は理解できたので、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリの柔軟性と利便性を紹介するその他の例の一覧を次に示します。  それぞれの例の前には、その動作についての簡単な説明が記載されています。  推論された型を確認するために各クエリのクエリ結果変数の上にマウス ポインターを置きます。結果を生成するには、`For Each` ループを使用します。  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/walkthrough-writing-quer_1_7.vb)]  
  
## 追加情報  
 クエリの基本的な概念を理解したら、関心のある特定の種類の [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーのドキュメントやサンプルに進むことができます。  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
## 参照  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Supplementary LINQ Resources](../Topic/Supplementary%20LINQ%20Resources.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)