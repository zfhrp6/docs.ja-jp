---
title: "チュートリアル: C# でのクエリの作成 (LINQ)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0885c3cc989260cf67608bec0ff512c9f4835f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="11631-102">チュートリアル: C# でのクエリの作成 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="11631-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="11631-103">このチュートリアルでは、LINQ クエリ式の記述に使用される C# 言語機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="11631-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="11631-104">C# プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="11631-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11631-105">以下に示すのは Visual Studio 用の手順です。</span><span class="sxs-lookup"><span data-stu-id="11631-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="11631-106">別の開発環境を使用している場合は、System.Core.dll への参照と <xref:System.Linq?displayProperty=nameWithType> 名前空間の `using` ディレクティブを使用したコンソール プロジェクトを作成してください。</span><span class="sxs-lookup"><span data-stu-id="11631-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="11631-107">Visual Studio でプロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="11631-107">To create a project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="11631-108">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="11631-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="11631-109">メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="11631-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="11631-110">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="11631-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="11631-111">**[インストール済み]**、**[テンプレート]**、**[Visual C#]** の順に展開し、**[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="11631-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="11631-112">**[名前]** テキスト ボックスで、別の名前を入力するか、既定の名前をそのまま使用し、**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="11631-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="11631-113">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="11631-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="11631-114">プロジェクトには、System.Core.dll への参照と、<xref:System.Linq?displayProperty=nameWithType> 名前空間の `using` ディレクティブが使用されています。</span><span class="sxs-lookup"><span data-stu-id="11631-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="11631-115">メモリ内データ ソースの作成</span><span class="sxs-lookup"><span data-stu-id="11631-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="11631-116">クエリのデータ ソースは、`Student` オブジェクトのシンプルなリストです。</span><span class="sxs-lookup"><span data-stu-id="11631-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="11631-117">各 `Student` レコードには、名前、姓、およびクラスでのテストの点数を表す整数の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="11631-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="11631-118">このコードをプロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="11631-118">Copy this code into your project.</span></span> <span data-ttu-id="11631-119">これには、次のような特徴があります。</span><span class="sxs-lookup"><span data-stu-id="11631-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="11631-120">`Student` クラスは自動実装プロパティで構成されています。</span><span class="sxs-lookup"><span data-stu-id="11631-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="11631-121">リスト内の各生徒は、オブジェクト初期化子で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="11631-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="11631-122">リスト自体は、コレクション初期化子で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="11631-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="11631-123">この全体的なデータ構造は、コンストラクターへの明示的な呼び出しや、明示的なメンバー アクセスを行うことなく初期化され、インスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="11631-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="11631-124">これらの新機能について詳しくは、「[自動実装プロパティ](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」および「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11631-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="11631-125">データ ソースを追加するには</span><span class="sxs-lookup"><span data-stu-id="11631-125">To add the data source</span></span>  
  
-   <span data-ttu-id="11631-126">`Student` クラスと、初期化された生徒リストを、プロジェクト内の `Program` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="11631-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="11631-127">生徒リストに新しい生徒を追加するには</span><span class="sxs-lookup"><span data-stu-id="11631-127">To add a new Student to the Students list</span></span>  
  
1.  <span data-ttu-id="11631-128">新しい `Student` を `Students` リストに追加し、目的の名前とテスト点数を使用します。</span><span class="sxs-lookup"><span data-stu-id="11631-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="11631-129">オブジェクト初期化子の構文をより効果的に学習するために、新しい生徒の情報をすべて入力するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="11631-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="11631-130">クエリの作成</span><span class="sxs-lookup"><span data-stu-id="11631-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="11631-131">簡単なクエリを作成するには</span><span class="sxs-lookup"><span data-stu-id="11631-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="11631-132">アプリケーションの `Main` メソッドで、シンプルなクエリを作成します。このクエリでは、実行時に、最初のテストの点数が 90 を超える全生徒のリストを生成するようにします。</span><span class="sxs-lookup"><span data-stu-id="11631-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="11631-133">`Student` オブジェクト全体が選択されているため、クエリの型は `IEnumerable<Student>` です。</span><span class="sxs-lookup"><span data-stu-id="11631-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="11631-134">コードでは、[var](../../../../csharp/language-reference/keywords/var.md) キーワードを使用して暗黙的型指定を使用することもできますが、結果を明確に示すために、明示的型指定を使用します。</span><span class="sxs-lookup"><span data-stu-id="11631-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="11631-135">(`var` について詳しくは、「[暗黙的に型指定されたローカル変数](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」をご覧ください。)</span><span class="sxs-lookup"><span data-stu-id="11631-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="11631-136">なお、クエリの範囲変数 (`student`) は、ソース内の各 `Student` への参照として機能し、各オブジェクトのメンバー アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="11631-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="11631-137">クエリの実行</span><span class="sxs-lookup"><span data-stu-id="11631-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="11631-138">クエリを実行するには</span><span class="sxs-lookup"><span data-stu-id="11631-138">To execute the query</span></span>  
  
1.  <span data-ttu-id="11631-139">クエリを実行する `foreach` ループを記述します。</span><span class="sxs-lookup"><span data-stu-id="11631-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="11631-140">コードについては、以下の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="11631-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="11631-141">返されたシーケンス内の各要素は、`foreach` ループ内の反復変数を通じてアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="11631-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="11631-142">この変数の型は `Student` で、クエリ変数の型は互換性があります (`IEnumerable<Student>`)。</span><span class="sxs-lookup"><span data-stu-id="11631-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2.  <span data-ttu-id="11631-143">このコードを追加したら、アプリケーションをビルドして実行し、**[コンソール]** ウィンドウで結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="11631-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="11631-144">別のフィルター条件を追加するには</span><span class="sxs-lookup"><span data-stu-id="11631-144">To add another filter condition</span></span>  
  
1.  <span data-ttu-id="11631-145">クエリを改良するために、`where` 句で複数のブール条件を結合することができます。</span><span class="sxs-lookup"><span data-stu-id="11631-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="11631-146">次のコードでは、最初の点数が 90 より高く、最後の点数が 80 未満の生徒が返されるようにするための条件を追加しています。</span><span class="sxs-lookup"><span data-stu-id="11631-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="11631-147">`where` 句は次のコードのようになります。</span><span class="sxs-lookup"><span data-stu-id="11631-147">The `where` clause should resemble the following code.</span></span>  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="11631-148">詳しくは、「[where 句](../../../../csharp/language-reference/keywords/where-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11631-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="11631-149">クエリの変更</span><span class="sxs-lookup"><span data-stu-id="11631-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="11631-150">結果を並べ替えるには</span><span class="sxs-lookup"><span data-stu-id="11631-150">To order the results</span></span>  
  
1.  <span data-ttu-id="11631-151">クエリの結果は、一定の基準で順序付けしたほうが見やすくなります。</span><span class="sxs-lookup"><span data-stu-id="11631-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="11631-152">返されたシーケンスは、ソース要素内のアクセス可能なフィールドによって順序付けすることができます。</span><span class="sxs-lookup"><span data-stu-id="11631-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="11631-153">たとえば、次の `orderby` 句では、各生徒の名前を基準にして、A から Z へのアルファベット順で結果を並べるようにしています。</span><span class="sxs-lookup"><span data-stu-id="11631-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="11631-154">次の `orderby` 句をクエリに追加します (`where` ステートメントの直後、`select` ステートメントの前)。</span><span class="sxs-lookup"><span data-stu-id="11631-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  <span data-ttu-id="11631-155">`orderby` 句を変更し、最初のテストの点数を基準にして、結果を逆順 (最高点から最低点) で並べるようにします。</span><span class="sxs-lookup"><span data-stu-id="11631-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  <span data-ttu-id="11631-156">`WriteLine` 書式文字列を変更して、点数を表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="11631-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="11631-157">詳しくは、「[orderby 句](../../../../csharp/language-reference/keywords/orderby-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11631-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="11631-158">結果をグループ化するには</span><span class="sxs-lookup"><span data-stu-id="11631-158">To group the results</span></span>  
  
1.  <span data-ttu-id="11631-159">グループ化は、クエリ式の強力な機能です。</span><span class="sxs-lookup"><span data-stu-id="11631-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="11631-160">グループ句を使用したクエリでは、グループのシーケンスが生成され、各グループ自体に、`Key` と、そのグループの全メンバーで構成されたシーケンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="11631-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="11631-161">次の新しいクエリでは、生徒の姓の頭文字をキーに使用して、生徒をグループ化しています。</span><span class="sxs-lookup"><span data-stu-id="11631-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  <span data-ttu-id="11631-162">クエリの型が変更されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="11631-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="11631-163">`char` 型をキーに持つグループのシーケンスと、`Student` オブジェクトのシーケンスが生成されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="11631-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="11631-164">クエリの型が変更されたため、次のコードでは `foreach` 実行ループも変更されています。</span><span class="sxs-lookup"><span data-stu-id="11631-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  <span data-ttu-id="11631-165">アプリケーションを実行し、**[コンソール]** ウィンドウで結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="11631-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="11631-166">詳しくは、「[group 句](../../../../csharp/language-reference/keywords/group-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11631-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="11631-167">変数を暗黙的に型指定するには</span><span class="sxs-lookup"><span data-stu-id="11631-167">To make the variables implicitly typed</span></span>  
  
1.  <span data-ttu-id="11631-168">`IGroupings` の `IEnumerables` を明示的にコーディングするのは非常に面倒です。</span><span class="sxs-lookup"><span data-stu-id="11631-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="11631-169">`var` を使用すれば、同じクエリや `foreach` ループをはるかに効率的に記述できます。</span><span class="sxs-lookup"><span data-stu-id="11631-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="11631-170">`var` キーワードは、オブジェクトの型を変更しません。型を推論するようにコンパイラに指示するだけです。</span><span class="sxs-lookup"><span data-stu-id="11631-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="11631-171">`studentQuery` の型と反復変数 `group` を `var` に変更し、クエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="11631-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="11631-172">内部の `foreach` ループで、反復変数の型は `Student` のままになっており、クエリは以前と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="11631-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="11631-173">反復変数 `s` を `var` に変更し、クエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="11631-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="11631-174">まったく同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="11631-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     <span data-ttu-id="11631-175">[var](../../../../csharp/language-reference/keywords/var.md) について詳しくは、「[暗黙的に型指定されたローカル変数](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11631-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="11631-176">グループをキー値で順序付けるには</span><span class="sxs-lookup"><span data-stu-id="11631-176">To order the groups by their key value</span></span>  
  
1.  <span data-ttu-id="11631-177">前のクエリを実行すると、グループはアルファベット順になりません。</span><span class="sxs-lookup"><span data-stu-id="11631-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="11631-178">これを変えるには、`group` 句の後に `orderby` 句を記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11631-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="11631-179">しかし `orderby` 句を使用するには、まず、`group` 句によって作成されたグループへの参照として機能する識別子が必要になります。</span><span class="sxs-lookup"><span data-stu-id="11631-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="11631-180">この識別子は、次のように `into` キーワード使用して記述します。</span><span class="sxs-lookup"><span data-stu-id="11631-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     <span data-ttu-id="11631-181">このクエリを実行すると、グループがアルファベット順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="11631-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="11631-182">let を使用して識別子を導入するには</span><span class="sxs-lookup"><span data-stu-id="11631-182">To introduce an identifier by using let</span></span>  
  
1.  <span data-ttu-id="11631-183">`let` キーワードを使用すると、任意の式の結果の識別子をクエリ式に導入できます。</span><span class="sxs-lookup"><span data-stu-id="11631-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="11631-184">この識別子は、次の例のように便利に使用できます。式の結果を格納することで、何度も計算を行う必要がなくなり、パフォーマンスの向上につながります。</span><span class="sxs-lookup"><span data-stu-id="11631-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     <span data-ttu-id="11631-185">詳しくは、「[let 句](../../../../csharp/language-reference/keywords/let-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11631-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="11631-186">クエリ式でメソッド構文を使用するには</span><span class="sxs-lookup"><span data-stu-id="11631-186">To use method syntax in a query expression</span></span>  
  
1.  <span data-ttu-id="11631-187">「[LINQ でのクエリ構文とメソッド構文](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」で説明したように、一部のクエリ操作は、メソッド構文を使用することでのみ表現できます。</span><span class="sxs-lookup"><span data-stu-id="11631-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="11631-188">次のコードは、ソース シーケンス内の各 `Student` の合計点数を計算し、そのクエリの結果に対して `Average()` メソッドを呼び出して、クラスの平均点数を計算します。</span><span class="sxs-lookup"><span data-stu-id="11631-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span> <span data-ttu-id="11631-189">クエリ式を囲むかっこが配置されたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="11631-189">Note the placement of parentheses around the query expression.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="11631-190">select 句で変換またはプロジェクトを実行するには</span><span class="sxs-lookup"><span data-stu-id="11631-190">To transform or project in the select clause</span></span>  
  
1.  <span data-ttu-id="11631-191">クエリでは、ソース シーケンス内の要素とは異なる要素のシーケンスを生成することがよくあります。</span><span class="sxs-lookup"><span data-stu-id="11631-191">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="11631-192">前のクエリと実行ループを削除またはコメント アウトして、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="11631-192">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="11631-193">クエリが (`Students` ではなく) 文字列のシーケンスを返すことに注意してください。このことは、`foreach` ループに反映されます。</span><span class="sxs-lookup"><span data-stu-id="11631-193">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  <span data-ttu-id="11631-194">このチュートリアルの前のコードでは、クラスの平均点が約 334 と示されました。</span><span class="sxs-lookup"><span data-stu-id="11631-194">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="11631-195">合計点がクラス平均よりも高い `Students` のシーケンスを (生徒の `Student ID` と共に) 生成するには、`select` ステートメントで匿名型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="11631-195">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a><span data-ttu-id="11631-196">次の手順</span><span class="sxs-lookup"><span data-stu-id="11631-196">Next Steps</span></span>  
 <span data-ttu-id="11631-197">C# でのクエリ操作の基本が理解できたら、興味がある種類の LINQ プロバイダーについて、ドキュメントやサンプルを読んでみましょう。</span><span class="sxs-lookup"><span data-stu-id="11631-197">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="11631-198">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="11631-198">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
  
 [<span data-ttu-id="11631-199">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="11631-199">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="11631-200">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="11631-200">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="11631-201">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="11631-201">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="11631-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="11631-202">See Also</span></span>  
 [<span data-ttu-id="11631-203">統合言語クエリ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="11631-203">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="11631-204">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="11631-204">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="11631-205">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="11631-205">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
