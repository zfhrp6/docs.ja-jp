---
title: "Visual Basic でクエリを記述します。"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: "70"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e78d93895a86ad9b2456e5ac7c05db83ebf0379d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="380eb-102">チュートリアル: Visual Basic でクエリを記述する</span><span class="sxs-lookup"><span data-stu-id="380eb-102">Walkthrough: Writing Queries in Visual Basic</span></span>
<span data-ttu-id="380eb-103">このチュートリアルでは、書き込みを Visual Basic 言語の機能を使用する方法を示しています[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]クエリ式。</span><span class="sxs-lookup"><span data-stu-id="380eb-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query expressions.</span></span> <span data-ttu-id="380eb-104">このチュートリアルでは、Student オブジェクトの一覧にクエリを作成する方法、クエリを実行する方法、およびそれらを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="380eb-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="380eb-105">クエリでは、オブジェクト初期化子、ローカル型推論、および匿名型を含むいくつかの機能を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="380eb-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>  
  
 <span data-ttu-id="380eb-106">このチュートリアルを完了すると、サンプルと、特定のドキュメントに移動する準備ができてされます[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]興味のあるプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="380eb-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider you are interested in.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="380eb-107">プロバイダーが含まれます[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]、および[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="380eb-107"> providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
## <a name="create-a-project"></a><span data-ttu-id="380eb-108">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="380eb-108">Create a Project</span></span>  
  
#### <a name="to-create-a-console-application-project"></a><span data-ttu-id="380eb-109">コンソール アプリケーション プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="380eb-109">To create a console application project</span></span>  
  
1.  <span data-ttu-id="380eb-110">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="380eb-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="380eb-111">**[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="380eb-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="380eb-112">**インストールされたテンプレート**一覧で、クリックして**Visual Basic**です。</span><span class="sxs-lookup"><span data-stu-id="380eb-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>  
  
4.  <span data-ttu-id="380eb-113">プロジェクトの種類の一覧でクリックして**コンソール アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="380eb-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="380eb-114">**名前**ボックスで、プロジェクトの名前を入力し、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="380eb-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="380eb-115">プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="380eb-115">A project is created.</span></span> <span data-ttu-id="380eb-116">既定では、System.Core.dll への参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="380eb-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="380eb-117">また、**インポートされた名前空間**ボックスの一覧、[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)が含まれています、<xref:System.Linq?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="380eb-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
5.  <span data-ttu-id="380eb-118">[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**で**です。</span><span class="sxs-lookup"><span data-stu-id="380eb-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>  
  
## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="380eb-119">メモリ内データ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="380eb-119">Add an In-Memory Data Source</span></span>  
 <span data-ttu-id="380eb-120">このチュートリアルのクエリのデータ ソースの一覧は、`Student`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="380eb-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="380eb-121">各`Student`名、姓、学年、および教育機関のランク、学生の本文にオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="380eb-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="380eb-122">データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="380eb-122">To add the data source</span></span>  
  
-   <span data-ttu-id="380eb-123">定義、`Student`クラス、およびクラスのインスタンスの一覧を作成します。</span><span class="sxs-lookup"><span data-stu-id="380eb-123">Define a `Student` class, and create a list of instances of the class.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="380eb-124">定義に必要なコード、`Student`クラスし、使用するリストを作成のチュートリアルで例が提供される[する方法: リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)です。</span><span class="sxs-lookup"><span data-stu-id="380eb-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="380eb-125">そこからコピーし、プロジェクトに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="380eb-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="380eb-126">新しいコード プロジェクトを作成するときに表示されたコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="380eb-126">The new code replaces the code that appeared when you created the project.</span></span>  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="380eb-127">学生のリストに新しい学生を追加するには</span><span class="sxs-lookup"><span data-stu-id="380eb-127">To add a new student to the students list</span></span>  
  
-   <span data-ttu-id="380eb-128">パターンに従い、`getStudents`の別のインスタンスを追加するメソッドを`Student`リストにクラスです。</span><span class="sxs-lookup"><span data-stu-id="380eb-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="380eb-129">受講者を追加することをオブジェクト初期化子が紹介されます。</span><span class="sxs-lookup"><span data-stu-id="380eb-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="380eb-130">詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="380eb-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="create-a-query"></a><span data-ttu-id="380eb-131">クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="380eb-131">Create a Query</span></span>  
 <span data-ttu-id="380eb-132">実行すると、このセクションで追加のクエリは、学生の成績順位に格納上位 10 件のリストを生成します。</span><span class="sxs-lookup"><span data-stu-id="380eb-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="380eb-133">クエリは、完全な選択ので`Student`オブジェクトごとに、クエリ結果の型が`IEnumerable(Of Student)`です。</span><span class="sxs-lookup"><span data-stu-id="380eb-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="380eb-134">ただし、クエリの種類通常が指定されていないクエリ定義にします。</span><span class="sxs-lookup"><span data-stu-id="380eb-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="380eb-135">代わりに、コンパイラは、種類を決定するのにローカル型推論を使用します。</span><span class="sxs-lookup"><span data-stu-id="380eb-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="380eb-136">詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="380eb-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="380eb-137">クエリの範囲変数、 `currentStudent`、それぞれへの参照の役割を果たす`Student`、ソースでインスタンス`students`、内の各オブジェクトのプロパティへのアクセスを提供する`students`です。</span><span class="sxs-lookup"><span data-stu-id="380eb-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="380eb-138">簡単なクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="380eb-138">To create a simple query</span></span>  
  
1.  <span data-ttu-id="380eb-139">内の場所を検索、`Main`次のようにマークされているプロジェクトのメソッド。</span><span class="sxs-lookup"><span data-stu-id="380eb-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     <span data-ttu-id="380eb-140">次のコードをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="380eb-140">Copy the following code and paste it in.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  <span data-ttu-id="380eb-141">マウス ポインターを合わせる`studentQuery`コンパイラによって割り当てられた型があることを確認するコードで`IEnumerable(Of Student)`です。</span><span class="sxs-lookup"><span data-stu-id="380eb-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>  
  
## <a name="run-the-query"></a><span data-ttu-id="380eb-142">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="380eb-142">Run the Query</span></span>  
 <span data-ttu-id="380eb-143">変数`studentQuery`クエリ、クエリの実行結果いないの定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="380eb-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="380eb-144">クエリを実行するための一般的なメカニズムは、`For Each`ループします。</span><span class="sxs-lookup"><span data-stu-id="380eb-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="380eb-145">返されるシーケンス内の各要素は、ループの反復変数を介してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="380eb-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="380eb-146">クエリの実行の詳細については、次を参照してください。[書き込み、最初の LINQ クエリの](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。</span><span class="sxs-lookup"><span data-stu-id="380eb-146">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
#### <a name="to-run-the-query"></a><span data-ttu-id="380eb-147">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="380eb-147">To run the query</span></span>  
  
1.  <span data-ttu-id="380eb-148">次の追加`For Each`プロジェクトのクエリの下のループします。</span><span class="sxs-lookup"><span data-stu-id="380eb-148">Add the following `For Each` loop below the query in your project.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  <span data-ttu-id="380eb-149">ループ コントロール変数にマウス ポインターを置く`studentRecord`にそのデータ型を参照してください。</span><span class="sxs-lookup"><span data-stu-id="380eb-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="380eb-150">型`studentRecord`と推論されます`Student`ので、`studentQuery`のコレクションを返します`Student`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="380eb-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>  
  
3.  <span data-ttu-id="380eb-151">構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="380eb-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="380eb-152">コンソール ウィンドウに結果を注意してください。</span><span class="sxs-lookup"><span data-stu-id="380eb-152">Note the results in the console window.</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="380eb-153">クエリの変更</span><span class="sxs-lookup"><span data-stu-id="380eb-153">Modify the Query</span></span>  
 <span data-ttu-id="380eb-154">指定した順序内にある場合、クエリの結果をスキャンすると簡単です。</span><span class="sxs-lookup"><span data-stu-id="380eb-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="380eb-155">使用可能なフィールドに基づいて、返されるシーケンスを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="380eb-155">You can sort the returned sequence based on any available field.</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="380eb-156">結果を並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="380eb-156">To order the results</span></span>  
  
1.  <span data-ttu-id="380eb-157">次の追加`Order By`間句、`Where`ステートメントおよび`Select`クエリのステートメント。</span><span class="sxs-lookup"><span data-stu-id="380eb-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="380eb-158">`Order By`句は結果の順序をアルファベット順に A から z、に従って最後の各受講者の名前。</span><span class="sxs-lookup"><span data-stu-id="380eb-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  <span data-ttu-id="380eb-159">姓と名、姓で並べ替えするには、クエリに両方のフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="380eb-159">To order by last name and then first name, add both fields to the query:</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     <span data-ttu-id="380eb-160">指定することも`Descending`Z から A に注文する</span><span class="sxs-lookup"><span data-stu-id="380eb-160">You can also specify `Descending` to order from Z to A.</span></span>  
  
3.  <span data-ttu-id="380eb-161">構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="380eb-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="380eb-162">コンソール ウィンドウに結果を注意してください。</span><span class="sxs-lookup"><span data-stu-id="380eb-162">Note the results in the console window.</span></span>  
  
#### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="380eb-163">ローカル識別子を導入するには</span><span class="sxs-lookup"><span data-stu-id="380eb-163">To introduce a local identifier</span></span>  
  
1.  <span data-ttu-id="380eb-164">このセクションの内容をクエリ式内のローカル識別子を導入する、コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="380eb-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="380eb-165">ローカルの識別子では、中間結果を保持します。</span><span class="sxs-lookup"><span data-stu-id="380eb-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="380eb-166">次の例では、`name`学生の連結を保持する識別子の最初と姓と名は、します。</span><span class="sxs-lookup"><span data-stu-id="380eb-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="380eb-167">利便性のためのローカル識別子を使用できますか、複数回を計算するそれ以外の場合は、式の結果を格納することでパフォーマンスの向上につながります。</span><span class="sxs-lookup"><span data-stu-id="380eb-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  <span data-ttu-id="380eb-168">構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="380eb-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="380eb-169">コンソール ウィンドウに結果を注意してください。</span><span class="sxs-lookup"><span data-stu-id="380eb-169">Note the results in the console window.</span></span>  
  
#### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="380eb-170">Select 句で 1 つのフィールドを射影するには</span><span class="sxs-lookup"><span data-stu-id="380eb-170">To project one field in the Select clause</span></span>  
  
1.  <span data-ttu-id="380eb-171">クエリの追加と`For Each`ソース内の要素とは異なる要素のシーケンスを生成するクエリを作成するには、このセクションからループします。</span><span class="sxs-lookup"><span data-stu-id="380eb-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="380eb-172">次の例では、ソースでのコレクション`Student`オブジェクトではなく各オブジェクトの 1 メンバーのみが返されます。 姓が Garcia 学生の姓。</span><span class="sxs-lookup"><span data-stu-id="380eb-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="380eb-173">`currentStudent.First`文字列、によって返されるシーケンスのデータ型は、`studentQuery3`は`IEnumerable(Of String)`文字列のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="380eb-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="380eb-174">以前の例のように、データの割り当てを入力`studentQuery3`コンパイラ ローカル型推論を使用して判別するためのままです。</span><span class="sxs-lookup"><span data-stu-id="380eb-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  <span data-ttu-id="380eb-175">マウス ポインターを合わせる`studentQuery3`割り当ての種類があることを確認するようにコードで`IEnumerable(Of String)`です。</span><span class="sxs-lookup"><span data-stu-id="380eb-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>  
  
3.  <span data-ttu-id="380eb-176">構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="380eb-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="380eb-177">コンソール ウィンドウに結果を注意してください。</span><span class="sxs-lookup"><span data-stu-id="380eb-177">Note the results in the console window.</span></span>  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="380eb-178">Select 句で匿名型を作成するには</span><span class="sxs-lookup"><span data-stu-id="380eb-178">To create an anonymous type in the Select clause</span></span>  
  
1.  <span data-ttu-id="380eb-179">匿名型を表示するには、このセクションのコードは、クエリで使用するを追加します。</span><span class="sxs-lookup"><span data-stu-id="380eb-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="380eb-180">完全なレコードではなく、データ ソースから複数のフィールドを取得するときにクエリで使用する (`currentStudent`前の例でレコード) 1 つのフィールド (`First`前のセクションで)。</span><span class="sxs-lookup"><span data-stu-id="380eb-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="380eb-181">内のフィールドを指定する結果に含めるフィールドを含んでいる新しい名前付きの型を定義するには、代わりに、`Select`句と、コンパイラは、それらのフィールドのプロパティとして持つ匿名型を作成します。</span><span class="sxs-lookup"><span data-stu-id="380eb-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="380eb-182">詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="380eb-182">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="380eb-183">次の例では、成績順位は 1 ~ 10、教育機関のランクの順序で行ったりのランクと名前を返すクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="380eb-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="380eb-184">この例では、型で`studentQuery4`ために、推論する必要があります、`Select`句は、匿名型のインスタンスを返すし、匿名型には、使用可能な名前がありません。</span><span class="sxs-lookup"><span data-stu-id="380eb-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  <span data-ttu-id="380eb-185">構築し、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="380eb-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="380eb-186">コンソール ウィンドウに結果を注意してください。</span><span class="sxs-lookup"><span data-stu-id="380eb-186">Note the results in the console window.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="380eb-187">その他の例</span><span class="sxs-lookup"><span data-stu-id="380eb-187">Additional Examples</span></span>  
 <span data-ttu-id="380eb-188">電源と柔軟性を説明するためにその他の例の一覧を次に示します基本を理解すると、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="380eb-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="380eb-189">それぞれの例は、内容の簡単な説明続きます。</span><span class="sxs-lookup"><span data-stu-id="380eb-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="380eb-190">推論された型を表示するには、各クエリのクエリ結果の変数の上には、マウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="380eb-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="380eb-191">使用して、`For Each`ループを使用して、結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="380eb-191">Use a `For Each` loop to produce the results.</span></span>  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a><span data-ttu-id="380eb-192">追加情報</span><span class="sxs-lookup"><span data-stu-id="380eb-192">Additional Information</span></span>  
 <span data-ttu-id="380eb-193">特定の種類のドキュメントおよびサンプルを読み取る準備ができたらのクエリの基本的な概念を理解したら、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]興味のあるプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="380eb-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider that you are interested in:</span></span>  
  
 [<span data-ttu-id="380eb-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="380eb-194">LINQ to Objects</span></span>](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [<span data-ttu-id="380eb-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="380eb-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="380eb-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="380eb-196">LINQ to XML</span></span>](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [<span data-ttu-id="380eb-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="380eb-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a><span data-ttu-id="380eb-198">参照</span><span class="sxs-lookup"><span data-stu-id="380eb-198">See Also</span></span>  
 [<span data-ttu-id="380eb-199">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="380eb-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="380eb-200">Visual Basic の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="380eb-200">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="380eb-201">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="380eb-201">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="380eb-202">オブジェクト初期化子 : 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="380eb-202">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="380eb-203">匿名型</span><span class="sxs-lookup"><span data-stu-id="380eb-203">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="380eb-204">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="380eb-204">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="380eb-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="380eb-205">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="380eb-206">クエリ</span><span class="sxs-lookup"><span data-stu-id="380eb-206">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)
