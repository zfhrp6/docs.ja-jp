---
title: "Walkthrough: Writing Queries in C# (LINQ) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "get-started-article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], walkthroughs"
  - "LINQ [C#], writing queries"
  - "queries [LINQ in C#], writing"
  - "writing LINQ queries"
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# Walkthrough: Writing Queries in C# (LINQ)
このチュートリアルでは、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリ式の記述に使用される C\# 言語の機能について説明します。  このチュートリアルを完了したら、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)]、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] to DataSets、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] など、関心のある特定の [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーのサンプルやドキュメントに進むことができます。  
  
## 必須コンポーネント  
 このチュートリアルでは、Visual Studio 2008 で導入された機能が必要です。  
  
 ![ビデオへのリンク](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") このトピックのビデオ デモについては、「[Video How to: Writing Queries in C\# \(LINQ\) \(ビデオ デモ: C\# でのクエリの作成 \(LINQ\)\)](http://go.microsoft.com/fwlink/?LinkId=100393)」を参照してください。  
  
## C\# プロジェクトの作成  
  
#### プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
3.  **\[インストール済み\]** を展開し、**\[テンプレート\]** を展開し、**\[Visual C\#\]** を展開し、を **\[コンソール アプリケーション\]** を選択します。  
  
4.  **\[名前\]** のテキスト ボックスに、別の名前を入力するか、既定の名前をそのまま使用し、を **\[OK\]** のボタンをクリックします。  
  
     **ソリューション エクスプローラー**に新しいプロジェクトが表示されます。  
  
5.  作成されたプロジェクトに、System.Core.dll への参照と <xref:System.Linq?displayProperty=fullName> 名前空間に対する `using` ディレクティブが含まれていることを確認します。  
  
## インメモリ データ ソースの作成  
 クエリのデータ ソースは、`Student` オブジェクトの単純なリストです。  各 `Student` レコードには、名、姓、およびクラス内でのその生徒のテストの点数を表す整数の配列が含まれます。  このコードをプロジェクト内にコピーします。  このコードには、次のような特徴があります。  
  
-   `Student` クラスは、自動実装プロパティで構成されます。  
  
-   リスト内の各生徒は、オブジェクト初期化子によって初期化されます。  
  
-   リスト自体は、コレクション初期化子によって初期化されます。  
  
 このデータ構造全体の初期化とインスタンス化は、明示的にコンストラクターを呼び出したり、メンバーにアクセスしたりすることなく行われます。  これらの新しい機能の詳細については、「[自動実装プロパティ](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」および「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。  
  
#### データ ソースを追加するには  
  
-   プロジェクトの `Program` クラスに、`Student` クラスおよび初期化された生徒のリストを追加します。  
  
     [!code-cs[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### Students リストに新しい Student を追加するには  
  
1.  新しい `Student` を `Students` リストに追加し、任意の名前とテストの点数を指定します。  オブジェクト初期化子の構文をより深く理解するために、新しい生徒の情報をすべて入力してください。  
  
## クエリの作成  
  
#### 簡単なクエリを作成するには  
  
-   アプリケーションの `Main` メソッドで、実行されると最初のテストの点数が 90 点より高いすべての生徒のリストを生成する単純なクエリを作成します。  `Student` オブジェクト全体が選択されるので、クエリの型は `IEnumerable<Student>` になることに注意してください。  [var](../../../../csharp/language-reference/keywords/var.md) キーワードを使用して暗黙の型指定を行うこともできますが、結果を明確に示すために、明示的な型指定を行います。  `var` の詳細については、「[暗黙的に型指定されるローカル変数](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。  
  
     クエリの範囲変数である `student` は、ソース内の各 `Student` への参照として機能します。これにより、各オブジェクトのメンバーにアクセスできるようになります。  
  
 [!code-cs[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## クエリの実行  
  
#### クエリを実行するには  
  
1.  クエリを実行する `foreach` ループを記述します。  このコードについて、次の点に注意してください。  
  
    -   返されたシーケンス内の各要素へは、`foreach` ループ内の反復変数を通じてアクセスします。  
  
    -   この変数の型は `Student` で、クエリ変数の型は互換性のある `IEnumerable<Student>` です。  
  
2.  このコードを追加したら、Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドおよび実行し、**\[コンソール\]** ウィンドウで結果を確認します。  
  
 [!code-cs[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### 別のフィルター条件を追加するには  
  
1.  `where` 句の中で複数のブール型の条件を組み合わせると、さらに詳細なクエリを作成できます。  次のコードでは、条件を追加して、最初の点数が 90 点を上回り、最後の点数が 80 点未満の生徒がクエリから返されるようにします。  `where` 句は次のようになります。  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     詳細については、「[where 句](../../../../csharp/language-reference/keywords/where-clause.md)」を参照してください。  
  
## クエリの変更  
  
#### 結果を順序に従って並べるには  
  
1.  結果を一定の順序で並べると、結果のスキャンが簡単になります。  ソース要素のアクセス可能な任意のフィールドに基づいて、返されるシーケンスを順序付けることができます。  たとえば、次の `orderby` 句は、結果を各生徒の姓のアルファベット順 \(A から Z\) に並べます。  次の `orderby` 句を、クエリの `where` ステートメントの直後、`select` ステートメントの前に追加します。  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  この `orderby` 句を変更して、最初のテストの点数に基づいて逆の順序 \(最高点から最低点\) に並べるようにします。  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  `WriteLine` の書式指定文字列を次のように変更して、点数を確認できるようにします。  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     詳細については、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」を参照してください。  
  
#### 結果をグループ化するには  
  
1.  グループ化は、クエリ式の強力な機能です。  クエリで group 句を使用すると、グループのシーケンスが生成されます。各グループには、1 つの `Key` と、そのグループのすべてのメンバーで構成される 1 つのシーケンスが含まれます。  次の新しいクエリは、生徒の姓の頭文字をキーとして生徒をグループ化します。  
  
     [!code-cs[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  ここでは、クエリの型が変わっていることに注意してください。  このクエリでは、`char` 型のキーを持つグループのシーケンスと、`Student` オブジェクトのシーケンスが生成されます。  クエリの型が変わっているため、次のコードでは `foreach` 実行ループも変更されています。  
  
     [!code-cs[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Ctrl キーを押しながら F5 キーを押してアプリケーションを実行し、**\[コンソール\]** ウィンドウで結果を確認します。  
  
     詳細については、「[group 句](../../../../csharp/language-reference/keywords/group-clause.md)」を参照してください。  
  
#### 変数の型を暗黙的に指定するには  
  
1.  `IGroupings` の `IEnumerables` を明示的にコーディングする方法は、すぐに面倒になる可能性があります。  `var` を使用すると、同じクエリと `foreach` ループをごく簡単に記述できます。  `var` キーワードは、オブジェクトの型を変更するのではなく、コンパイラに型を推論するように指示します。  `studentQuery` の型と反復変数 `group`を `var` に変更して、クエリを再実行してください。  内部の `foreach` ループでは、反復変数の型が `Student` のままであるため、クエリは変更前と同様に機能します。  `s` 反復変数を `var` に変更して、クエリを再実行してください。  この場合も、変更前とまったく同じ結果が得られます。  
  
     [!code-cs[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     [var](../../../../csharp/language-reference/keywords/var.md) の詳細については、「[暗黙的に型指定されるローカル変数](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。  
  
#### キー値に基づいてグループを並べるには  
  
1.  前のクエリを実行すると、グループはアルファベット順に並んでいないことがわかります。  これを変更するには、`group` 句の後に `orderby` 句を挿入します。  ただし、`orderby` 句を使用するには、まず `group` 句で作成されたグループへの参照として機能する識別子を指定する必要があります。  この識別子は、次のように `into` キーワードを使用することで指定します。  
  
     [!code-cs[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     このクエリを実行すると、グループはアルファベット順に並べられます。  
  
#### let を使用して識別子を指定するには  
  
1.  `let` キーワードを使用すると、クエリ式で任意の式の結果に識別子を割り当てることができます。  この識別子は、次の例のように利便性のために使用できるほか、式の結果が格納されるので何度も計算を行う必要がなくなり、パフォーマンスの向上につながります。  
  
     [!code-cs[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     詳細については、「[let 句](../../../../csharp/language-reference/keywords/let-clause.md)」を参照してください。  
  
#### クエリ式でメソッドの構文を使用するには  
  
1.  「[Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」で説明したように、一部のクエリ操作は、メソッドの構文を使用する方法でしか表すことができません。  次のコードは、ソース シーケンス内の各 `Student` の総合得点を計算し、そのクエリの結果に対して `Average()` メソッドを呼び出して、クラスの平均点を計算します。  クエリ式がかっこで囲まれていることに注意してください。  
  
     [!code-cs[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### select 句で型を変換または投影するには  
  
1.  クエリでは、ソース シーケンス内の要素とは異なる要素のシーケンスが生成されることがよくあります。  前のクエリと実行ループを削除またはコメント アウトして、次のコードに置き換えてください。  このクエリでは、`Students` ではなく文字列のシーケンスが返されます。これは `foreach` ループにも影響します。  
  
     [!code-cs[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  このチュートリアルで既に説明したコードによって、クラスの平均点はおよそ 334 点であることが示されました。  合計点がクラス平均を上回る `Students` のシーケンスを、それぞれの `Student ID` と共に生成するには、`select` ステートメントで匿名型を使用できます。  
  
     [!code-cs[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## 次の手順  
 C\# におけるクエリの基本的な使用方法を理解したら、関心のある特定の種類の [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーのドキュメントやサンプルに進むことができます。  
  
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## 参照  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Supplementary LINQ Resources](../Topic/Supplementary%20LINQ%20Resources.md)   
 [チュートリアル: Visual Basic でクエリを記述する](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)