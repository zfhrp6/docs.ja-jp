---
title: "方法: Office プログラミングで名前付き引数と省略可能な引数を使用する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c773e7a6d902b9e61e724a69c9fdf5d61606de50
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="83285-102">方法: Office プログラミングで名前付き引数と省略可能な引数を使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="83285-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="83285-103">[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] で導入された名前付き引数と省略可能な引数を使うと、C# プログラミングの便利さ、柔軟性、読みやすさが向上します。</span><span class="sxs-lookup"><span data-stu-id="83285-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="83285-104">さらに、Microsoft Office オートメーション API などの COM インターフェイスへのアクセスが大幅に楽になります。</span><span class="sxs-lookup"><span data-stu-id="83285-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="83285-105">次の例の [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) メソッドには、列と行の数、書式設定、罫線、フォント、色など、テーブルの特性を表す 16 個のパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="83285-105">In the following example, method [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="83285-106">ほとんどの場合はこれらすべての特性に具体的な値を指定することはないので、16 個のパラメーターはすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="83285-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="83285-107">しかし、名前付きの省略可能な引数を使わないと、各パラメーターに値またはプレースホルダー値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83285-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="83285-108">名前付きの省略可能な引数を使うと、プロジェクトに必要なパラメーターの値だけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="83285-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="83285-109">以下の手順を行うには、Microsoft Office Word がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="83285-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="83285-110">新しいコンソール アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="83285-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="83285-111">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="83285-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="83285-112">**[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83285-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="83285-113">**[Templates Categories (テンプレート カテゴリ)]** ウィンドウで、**[Visual C#]** を展開し、**[Windows]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83285-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="83285-114">**[テンプレート]** ウィンドウの上部で、**[ターゲット フレームワーク]** ボックスに **[.NET Framework 4]** が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="83285-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="83285-115">**[テンプレート]** ウィンドウで **[コンソール アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83285-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="83285-116">**[名前]** フィールドに、プロジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="83285-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="83285-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83285-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="83285-118">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83285-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="83285-119">参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="83285-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="83285-120">**ソリューション エクスプローラー**で、プロジェクトの名前を右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83285-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="83285-121">**[参照の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83285-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="83285-122">**[.NET]** ページの **[コンポーネント名]** の一覧で、**Microsoft.Office.Interop.Word** を選びます。</span><span class="sxs-lookup"><span data-stu-id="83285-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="83285-123">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83285-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="83285-124">ディレクティブを使用して必要なものを追加するには</span><span class="sxs-lookup"><span data-stu-id="83285-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="83285-125">**ソリューション エクスプローラー**で、**Program.cs** ファイルを右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83285-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="83285-126">次の `using` ディレクティブをコード ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="83285-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     <span data-ttu-id="83285-127">[!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-127">[!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]</span></span>  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="83285-128">Word 文書にテキストを表示するには</span><span class="sxs-lookup"><span data-stu-id="83285-128">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="83285-129">Program.cs の `Program` クラスに、Word アプリケーションと Word 文書を作成する次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="83285-129">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="83285-130">[Add](http://go.microsoft.com/fwlink/?LinkId=145381) メソッドには、4 つの省略可能なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="83285-130">The [Add](http://go.microsoft.com/fwlink/?LinkId=145381) method has four optional parameters.</span></span> <span data-ttu-id="83285-131">この例では、それらの既定値を使います。</span><span class="sxs-lookup"><span data-stu-id="83285-131">This example uses their default values.</span></span> <span data-ttu-id="83285-132">そのため、呼び出しステートメントに引数は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="83285-132">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     <span data-ttu-id="83285-133">[!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-133">[!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]</span></span>  
  
2.  <span data-ttu-id="83285-134">文書内でテキストを表示する場所と表示するテキストを定義する次のコードを、メソッドの最後に追加します。</span><span class="sxs-lookup"><span data-stu-id="83285-134">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     <span data-ttu-id="83285-135">[!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-135">[!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]</span></span>  
  
### <a name="to-run-the-application"></a><span data-ttu-id="83285-136">アプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="83285-136">To run the application</span></span>  
  
1.  <span data-ttu-id="83285-137">次のステートメントを Main に追加します。</span><span class="sxs-lookup"><span data-stu-id="83285-137">Add the following statement to Main.</span></span>  
  
     <span data-ttu-id="83285-138">[!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-138">[!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]</span></span>  
  
2.  <span data-ttu-id="83285-139">Ctrl キーを押しながら F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="83285-139">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="83285-140">指定したテキストを含む Word 文書が表示されます。</span><span class="sxs-lookup"><span data-stu-id="83285-140">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="83285-141">テキストをテーブルに変更するには</span><span class="sxs-lookup"><span data-stu-id="83285-141">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="83285-142">`ConvertToTable` メソッドを使って、テーブル内のテキストを囲みます。</span><span class="sxs-lookup"><span data-stu-id="83285-142">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="83285-143">このメソッドには、16 個の省略可能なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="83285-143">The method has sixteen optional parameters.</span></span> <span data-ttu-id="83285-144">次の例に示すように、IntelliSense では省略可能なパラメーターは角かっこで囲まれています。</span><span class="sxs-lookup"><span data-stu-id="83285-144">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="83285-145">![ConvertToTable メソッドのパラメーターのリスト。](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="83285-145">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="83285-146">ConvertToTable のパラメーター</span><span class="sxs-lookup"><span data-stu-id="83285-146">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="83285-147">名前付きの省略可能な引数を使うと、変更するパラメーターの値だけを指定できます。</span><span class="sxs-lookup"><span data-stu-id="83285-147">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="83285-148">簡単なテーブルを作成するには、`DisplayInWord` メソッドの最後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="83285-148">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="83285-149">この引数は、`range` 内のテキスト文字列のコンマがテーブルのセルを区切ることを指定します。</span><span class="sxs-lookup"><span data-stu-id="83285-149">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     <span data-ttu-id="83285-150">[!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-150">[!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]</span></span>  
  
     <span data-ttu-id="83285-151">以前のバージョンの C# で `ConvertToTable` を呼び出すには、次のコードで示すように、パラメーターごとに参照引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="83285-151">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     <span data-ttu-id="83285-152">[!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-152">[!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]</span></span>  
  
2.  <span data-ttu-id="83285-153">Ctrl キーを押しながら F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="83285-153">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="83285-154">他のパラメーターを調べるには</span><span class="sxs-lookup"><span data-stu-id="83285-154">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="83285-155">テーブルを 1 列 3 行に変更するには、`DisplayInWord` の最後の行を次のステートメントに置き換えてから、Ctrl + F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="83285-155">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     <span data-ttu-id="83285-156">[!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-156">[!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]</span></span>  
  
2.  <span data-ttu-id="83285-157">テーブルに対して定義済みの書式を指定するには、`DisplayInWord` の最後の行を次のステートメントに置き換えてから、Ctrl + F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="83285-157">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="83285-158">書式には、[WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) 定数のどれでも指定できます。</span><span class="sxs-lookup"><span data-stu-id="83285-158">The format can be any of the [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) constants.</span></span>  
  
     <span data-ttu-id="83285-159">[!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-159">[!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="83285-160">例</span><span class="sxs-lookup"><span data-stu-id="83285-160">Example</span></span>  
 <span data-ttu-id="83285-161">ここまでの例をすべて含んだコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="83285-161">The following code includes the full example.</span></span>  
  
 <span data-ttu-id="83285-162">[!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="83285-162">[!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83285-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="83285-163">See Also</span></span>  
 [<span data-ttu-id="83285-164">名前付き引数と省略可能な引数</span><span class="sxs-lookup"><span data-stu-id="83285-164">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)

