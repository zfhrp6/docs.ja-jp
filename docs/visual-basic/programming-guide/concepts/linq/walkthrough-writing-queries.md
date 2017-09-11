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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3e946ad09c36e94758ce13b4a37a6bf6ae54f947
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="595ac-102">チュートリアル: Visual Basic でクエリを記述する</span><span class="sxs-lookup"><span data-stu-id="595ac-102">Walkthrough: Writing Queries in Visual Basic</span></span>
<span data-ttu-id="595ac-103">このチュートリアルでは、Visual Basic 言語の機能を使用して書き込む方法[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]クエリ式。</span><span class="sxs-lookup"><span data-stu-id="595ac-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] query expressions.</span></span> <span data-ttu-id="595ac-104">このチュートリアルでは、Student オブジェクトのリストに対するクエリを作成する方法、クエリを実行する方法、およびそれらを変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="595ac-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="595ac-105">クエリでは、オブジェクト初期化子、ローカル型推論、匿名型など、いくつかの機能を組み込みます。</span><span class="sxs-lookup"><span data-stu-id="595ac-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>  
  
 <span data-ttu-id="595ac-106">このチュートリアルを完了すると、サンプルと、特定のドキュメントに移動する準備が完了されます[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]興味のあるプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="595ac-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provider you are interested in.</span></span> [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]<span data-ttu-id="595ac-107">プロバイダーには、 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]、 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、および[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="595ac-107"> providers include [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], and [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
## <a name="create-a-project"></a><span data-ttu-id="595ac-108">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="595ac-108">Create a Project</span></span>  
  
#### <a name="to-create-a-console-application-project"></a><span data-ttu-id="595ac-109">コンソール アプリケーション プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="595ac-109">To create a console application project</span></span>  
  
1.  <span data-ttu-id="595ac-110">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="595ac-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="595ac-111">**[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="595ac-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="595ac-112">**インストールされたテンプレート**一覧で、クリックして**Visual Basic**します。</span><span class="sxs-lookup"><span data-stu-id="595ac-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>  
  
4.  <span data-ttu-id="595ac-113">プロジェクトの種類の一覧でクリックして**コンソール アプリケーション**します。</span><span class="sxs-lookup"><span data-stu-id="595ac-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="595ac-114">**名**ボックスに、プロジェクトの名前を入力し、 をクリックし、 **OK**します。</span><span class="sxs-lookup"><span data-stu-id="595ac-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="595ac-115">プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="595ac-115">A project is created.</span></span> <span data-ttu-id="595ac-116">既定では、System.Core.dll への参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="595ac-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="595ac-117">また、**インポートされた名前空間**ボックスの一覧で、[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)が含まれています、<xref:System.Linq?displayProperty=fullName>名前空間</xref:System.Linq?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="595ac-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=fullName> namespace.</span></span>  
  
5.  <span data-ttu-id="595ac-118">[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**に**します。</span><span class="sxs-lookup"><span data-stu-id="595ac-118">On the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>  
  
## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="595ac-119">メモリ内のデータ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="595ac-119">Add an In-Memory Data Source</span></span>  
 <span data-ttu-id="595ac-120">このチュートリアルのクエリのデータ ソースの一覧は、`Student`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="595ac-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="595ac-121">各`Student`オブジェクトには、名前、姓、学年、および学生全体での学術的な順位が含まれています。</span><span class="sxs-lookup"><span data-stu-id="595ac-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="595ac-122">データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="595ac-122">To add the data source</span></span>  
  
-   <span data-ttu-id="595ac-123">定義、`Student`クラスおよびクラスのインスタンスのリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="595ac-123">Define a `Student` class, and create a list of instances of the class.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="595ac-124">定義するために必要なコード、`Student`クラスし、使用されてリストの作成のチュートリアルで例が提供される[する方法: リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)します。</span><span class="sxs-lookup"><span data-stu-id="595ac-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="595ac-125">そこからコピーし、プロジェクトに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="595ac-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="595ac-126">新しいコードは、プロジェクトの作成時に表示されたコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="595ac-126">The new code replaces the code that appeared when you created the project.</span></span>  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="595ac-127">受講者リストに新しい学生を追加するには</span><span class="sxs-lookup"><span data-stu-id="595ac-127">To add a new student to the students list</span></span>  
  
-   <span data-ttu-id="595ac-128">パターンに従い、`getStudents`の別のインスタンスを追加するメソッドを`Student`クラスの一覧にします。</span><span class="sxs-lookup"><span data-stu-id="595ac-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="595ac-129">受講者の追加が発生するオブジェクト初期化子をします。</span><span class="sxs-lookup"><span data-stu-id="595ac-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="595ac-130">詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="595ac-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="create-a-query"></a><span data-ttu-id="595ac-131">クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="595ac-131">Create a Query</span></span>  
 <span data-ttu-id="595ac-132">実行すると、このセクションで追加のクエリは、学生の成績順位に入れます上位&10; 件のリストを生成します。</span><span class="sxs-lookup"><span data-stu-id="595ac-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="595ac-133">クエリは、完全な選択されるので`Student`オブジェクトごとに、クエリ結果の型が`IEnumerable(Of Student)`です。</span><span class="sxs-lookup"><span data-stu-id="595ac-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="595ac-134">ただし、クエリの型通常が指定されていないクエリ定義にします。</span><span class="sxs-lookup"><span data-stu-id="595ac-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="595ac-135">代わりに、コンパイラはローカル型推論を使用して型を調べます。</span><span class="sxs-lookup"><span data-stu-id="595ac-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="595ac-136">詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。</span><span class="sxs-lookup"><span data-stu-id="595ac-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="595ac-137">クエリの範囲変数、 `currentStudent`、それぞれへの参照の役割を果たします`Student`、ソース内のインスタンス`students`、内の各オブジェクトのプロパティへのアクセスを提供する`students`です。</span><span class="sxs-lookup"><span data-stu-id="595ac-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="595ac-138">簡単なクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="595ac-138">To create a simple query</span></span>  
  
1.  <span data-ttu-id="595ac-139">内の場所を検索、`Main`次のようにマークされているプロジェクトのメソッド。</span><span class="sxs-lookup"><span data-stu-id="595ac-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>  
  
     <span data-ttu-id="595ac-140">[!code-vb[VbLINQWalkthrough&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="595ac-140">[!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]</span></span>  
  
     <span data-ttu-id="595ac-141">次のコードをコピーし、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="595ac-141">Copy the following code and paste it in.</span></span>  
  
     <span data-ttu-id="595ac-142">[!code-vb[VbLINQWalkthrough&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="595ac-142">[!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]</span></span>  
  
2.  <span data-ttu-id="595ac-143">マウス ポインターを合わせる`studentQuery`コンパイラによって割り当てられた型があることを確認するためにコード`IEnumerable(Of Student)`します。</span><span class="sxs-lookup"><span data-stu-id="595ac-143">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>  
  
## <a name="run-the-query"></a><span data-ttu-id="595ac-144">クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="595ac-144">Run the Query</span></span>  
 <span data-ttu-id="595ac-145">変数`studentQuery`クエリの実行結果ではなく、クエリの定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="595ac-145">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="595ac-146">クエリを実行するための一般的なメカニズムは、`For Each`ループします。</span><span class="sxs-lookup"><span data-stu-id="595ac-146">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="595ac-147">返されるシーケンス内の各要素は、ループの反復変数を通じてアクセスします。</span><span class="sxs-lookup"><span data-stu-id="595ac-147">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="595ac-148">クエリの実行の詳細については、次を参照してください。[書き込みで初めて、の LINQ クエリ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。</span><span class="sxs-lookup"><span data-stu-id="595ac-148">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
#### <a name="to-run-the-query"></a><span data-ttu-id="595ac-149">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="595ac-149">To run the query</span></span>  
  
1.  <span data-ttu-id="595ac-150">次の追加`For Each`プロジェクト内のクエリの下のループします。</span><span class="sxs-lookup"><span data-stu-id="595ac-150">Add the following `For Each` loop below the query in your project.</span></span>  
  
     <span data-ttu-id="595ac-151">[!code-vb[VbLINQWalkthrough&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="595ac-151">[!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]</span></span>  
  
2.  <span data-ttu-id="595ac-152">ループ制御変数にマウス ポインターを置く`studentRecord`にそのデータ型を参照してください。</span><span class="sxs-lookup"><span data-stu-id="595ac-152">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="595ac-153">型`studentRecord`と推論`Student`ので、`studentQuery`のコレクションを返します`Student`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="595ac-153">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>  
  
3.  <span data-ttu-id="595ac-154">ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="595ac-154">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="595ac-155">コンソール ウィンドウに結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="595ac-155">Note the results in the console window.</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="595ac-156">クエリを変更します。</span><span class="sxs-lookup"><span data-stu-id="595ac-156">Modify the Query</span></span>  
 <span data-ttu-id="595ac-157">順序が指定されている場合は、クエリの結果をスキャンしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="595ac-157">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="595ac-158">使用可能なフィールドに基づいて返されるシーケンスを並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="595ac-158">You can sort the returned sequence based on any available field.</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="595ac-159">結果の順序</span><span class="sxs-lookup"><span data-stu-id="595ac-159">To order the results</span></span>  
  
1.  <span data-ttu-id="595ac-160">次の追加`Order By`句の間、`Where`ステートメントおよび`Select`クエリのステートメントです。</span><span class="sxs-lookup"><span data-stu-id="595ac-160">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="595ac-161">`Order By`句は結果の順序をアルファベット順に A から z、に従って最後の各受講者の名前。</span><span class="sxs-lookup"><span data-stu-id="595ac-161">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  <span data-ttu-id="595ac-162">姓、名、姓の順で並べ替えには、クエリを両方のフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="595ac-162">To order by last name and then first name, add both fields to the query:</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     <span data-ttu-id="595ac-163">指定することも`Descending`Z から A に注文する</span><span class="sxs-lookup"><span data-stu-id="595ac-163">You can also specify `Descending` to order from Z to A.</span></span>  
  
3.  <span data-ttu-id="595ac-164">ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="595ac-164">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="595ac-165">コンソール ウィンドウに結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="595ac-165">Note the results in the console window.</span></span>  
  
#### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="595ac-166">ローカル識別子を導入するには</span><span class="sxs-lookup"><span data-stu-id="595ac-166">To introduce a local identifier</span></span>  
  
1.  <span data-ttu-id="595ac-167">クエリ式のローカル識別子を導入するには、このセクションで、コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="595ac-167">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="595ac-168">ローカルの識別子では、中間結果を保持します。</span><span class="sxs-lookup"><span data-stu-id="595ac-168">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="595ac-169">次の例で`name`の生徒の連結を保持する識別子の最初と姓と名です。</span><span class="sxs-lookup"><span data-stu-id="595ac-169">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="595ac-170">複数回計算するわけではそれ以外の場合、式の結果を格納することでパフォーマンスの向上につながります。 または便宜のため、ローカル識別子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="595ac-170">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>  
  
     <span data-ttu-id="595ac-171">[!code-vb[VbLINQWalkthrough&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="595ac-171">[!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]</span></span>  
  
2.  <span data-ttu-id="595ac-172">ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="595ac-172">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="595ac-173">コンソール ウィンドウに結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="595ac-173">Note the results in the console window.</span></span>  
  
#### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="595ac-174">Select 句で&1; つのフィールドを射影するには</span><span class="sxs-lookup"><span data-stu-id="595ac-174">To project one field in the Select clause</span></span>  
  
1.  <span data-ttu-id="595ac-175">クエリに追加し、`For Each`ソース内の要素とは異なる要素のシーケンスを生成するクエリを作成するには、このセクションのループします。</span><span class="sxs-lookup"><span data-stu-id="595ac-175">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="595ac-176">次の例では、ソースを集めたもの`Student`オブジェクトではなく各オブジェクトの&1; メンバーのみが返されます。 姓が Garcia 学生の姓。</span><span class="sxs-lookup"><span data-stu-id="595ac-176">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="595ac-177">`currentStudent.First`によって返されるシーケンスのデータ型の文字列`studentQuery3`は`IEnumerable(Of String)`文字列のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="595ac-177">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="595ac-178">前の例と同様に、データの割り当てがの入力`studentQuery3`コンパイラ ローカル型推論を使用して確認するのには残されます。</span><span class="sxs-lookup"><span data-stu-id="595ac-178">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>  
  
     <span data-ttu-id="595ac-179">[!code-vb[VbLINQWalkthrough&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="595ac-179">[!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]</span></span>  
  
2.  <span data-ttu-id="595ac-180">マウス ポインターを合わせる`studentQuery3`割り当てられた型があることを確認するためにコード`IEnumerable(Of String)`します。</span><span class="sxs-lookup"><span data-stu-id="595ac-180">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>  
  
3.  <span data-ttu-id="595ac-181">ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="595ac-181">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="595ac-182">コンソール ウィンドウに結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="595ac-182">Note the results in the console window.</span></span>  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="595ac-183">Select 句で匿名型を作成するには</span><span class="sxs-lookup"><span data-stu-id="595ac-183">To create an anonymous type in the Select clause</span></span>  
  
1.  <span data-ttu-id="595ac-184">クエリでどのように匿名型を表示するには、このセクションのコードは使用を追加します。</span><span class="sxs-lookup"><span data-stu-id="595ac-184">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="595ac-185">完全な記録ではなく、データ ソースから複数のフィールドを取得するときにクエリで使用する (`currentStudent`前の例でのレコード) または&1; つのフィールド (`First`前のセクションで)。</span><span class="sxs-lookup"><span data-stu-id="595ac-185">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="595ac-186">内のフィールドを指定する結果に含めるフィールドを含む新しい名前付きの型を定義するには、代わりに、`Select`句と、コンパイラは、それらのフィールドのプロパティとして持つ匿名型を作成します。</span><span class="sxs-lookup"><span data-stu-id="595ac-186">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="595ac-187">詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="595ac-187">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="595ac-188">次の例では、最上級生の成績順位が 1 ~ 10、学術ランクの順序で範囲のランクと名前を返すクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="595ac-188">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="595ac-189">この例の種類で`studentQuery4`ために、推論する必要があります、`Select`句は、匿名型のインスタンスを返すし、匿名型には、使用可能な名前がありません。</span><span class="sxs-lookup"><span data-stu-id="595ac-189">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>  
  
     <span data-ttu-id="595ac-190">[!code-vb[VbLINQWalkthrough&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="595ac-190">[!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]</span></span>  
  
2.  <span data-ttu-id="595ac-191">ビルドして、ctrl キーを押しながら f5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="595ac-191">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="595ac-192">コンソール ウィンドウに結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="595ac-192">Note the results in the console window.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="595ac-193">その他の例</span><span class="sxs-lookup"><span data-stu-id="595ac-193">Additional Examples</span></span>  
 <span data-ttu-id="595ac-194">柔軟性を示すためにその他の例の一覧と電源の基本を理解すると、次に示します[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="595ac-194">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries.</span></span> <span data-ttu-id="595ac-195">それぞれの例は、内容の簡単な説明を付けたものです。</span><span class="sxs-lookup"><span data-stu-id="595ac-195">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="595ac-196">推論された型を表示するには、各クエリのクエリ結果変数の上には、マウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="595ac-196">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="595ac-197">使用して、`For Each`ループを使用して、結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="595ac-197">Use a `For Each` loop to produce the results.</span></span>  
  
 <span data-ttu-id="595ac-198">[!code-vb[VbLINQWalkthrough&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="595ac-198">[!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]</span></span>  
  
## <a name="additional-information"></a><span data-ttu-id="595ac-199">追加情報</span><span class="sxs-lookup"><span data-stu-id="595ac-199">Additional Information</span></span>  
 <span data-ttu-id="595ac-200">特定の種類のドキュメントとサンプルを参照する準備ができたらクエリの基本的な概念を理解したら、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]興味のあるプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="595ac-200">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provider that you are interested in:</span></span>  
  
 [<span data-ttu-id="595ac-201">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="595ac-201">LINQ to Objects</span></span>](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [<span data-ttu-id="595ac-202">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="595ac-202">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
  
 [<span data-ttu-id="595ac-203">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="595ac-203">LINQ to XML</span></span>](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [<span data-ttu-id="595ac-204">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="595ac-204">LINQ to DataSet</span></span>](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)  
  
## <a name="see-also"></a><span data-ttu-id="595ac-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="595ac-205">See Also</span></span>  
 <span data-ttu-id="595ac-206">[統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="595ac-206">[Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span></span>  
<span data-ttu-id="595ac-207"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="595ac-207"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="595ac-208"> [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="595ac-208"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="595ac-209"> [オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="595ac-209"> [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="595ac-210"> [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="595ac-210"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="595ac-211"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="595ac-211"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="595ac-212"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="595ac-212"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="595ac-213"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md)</span><span class="sxs-lookup"><span data-stu-id="595ac-213"> [Queries](../../../../visual-basic/language-reference/queries/queries.md)</span></span>
