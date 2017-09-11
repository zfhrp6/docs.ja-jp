---
title: "方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
caps.latest.revision: 33
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
ms.openlocfilehash: 5ed3716e5c0d8cd143148522a2fb3aed5ec433ab
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="4c337-102">方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4c337-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>
<span data-ttu-id="4c337-103">Visual C# には、Office API オブジェクトへのアクセスを容易にする機能があります。</span><span class="sxs-lookup"><span data-stu-id="4c337-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="4c337-104">新機能は、名前付き引数と省略可能な引数、`dynamic` と呼ばれる新しい型、値パラメーターの場合と同様に COM メソッドの参照パラメーターに引数を渡す機能などです。</span><span class="sxs-lookup"><span data-stu-id="4c337-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>  
  
 <span data-ttu-id="4c337-105">このトピックでは、新機能を使用して、Microsoft Office Excel ワークシートを作成および表示するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="4c337-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="4c337-106">その後、Excel ワークシートにリンクされているアイコンを含む Office Word 文書を追加するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="4c337-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>  
  
 <span data-ttu-id="4c337-107">このチュートリアルを実行するには、Microsoft Office Excel 2007 と Microsoft Office Word 2007 またはそれ以降のバージョンがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c337-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>  
  
 <span data-ttu-id="4c337-108">[!INCLUDE[windowsver](~/includes/windowsver-md.md)] よりも前のオペレーティング システムを使用している場合は、[!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4c337-108">If you are using an operating system that is older than [!INCLUDE[windowsver](~/includes/windowsver-md.md)], make sure that [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] is installed.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="4c337-109">新しいコンソール アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="4c337-109">To create a new console application</span></span>  
  
1.  <span data-ttu-id="4c337-110">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="4c337-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4c337-111">**[ファイル]** メニューの **[新規作成]**をポイントし、 **[プロジェクト]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-111">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="4c337-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="4c337-113">**[インストールされたテンプレート]** ペインで、**[Visual C#]** を展開し、**[Windows]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-113">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="4c337-114">**[新しいプロジェクト]** ダイアログ ボックスの上部で、**.NET Framework 4** (またはそれ以降のバージョン) がターゲット フレームワークとして選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4c337-114">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>  
  
5.  <span data-ttu-id="4c337-115">**[テンプレート]** ペインの **[コンソール アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="4c337-116">**[名前]** フィールドに、プロジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4c337-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="4c337-117">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="4c337-118">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-references"></a><span data-ttu-id="4c337-119">参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="4c337-119">To add references</span></span>  
  
1.  <span data-ttu-id="4c337-120">**ソリューション エクスプローラー**で、プロジェクトの名前を右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="4c337-121">**[参照の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="4c337-122">**[アセンブリ]** ページの **[コンポーネント名]** 一覧で **[Microsoft.Office.Interop.Word]** を選択し、Ctrl キーを押しながら **[Microsoft.Office.Interop.Excel]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c337-122">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="4c337-123">アセンブリが表示されない場合は、アセンブリがインストールされ、表示されることの確認が必要になることがあります (「[方法: Office のプライマリ相互運用機能アセンブリをインストールする](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="4c337-123">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>  
  
3.  <span data-ttu-id="4c337-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-124">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="4c337-125">ディレクティブを使用して必要なものを追加するには</span><span class="sxs-lookup"><span data-stu-id="4c337-125">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="4c337-126">**ソリューション エクスプローラー**で、**Program.cs** ファイルを右クリックし、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-126">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="4c337-127">次の `using` ディレクティブをコード ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="4c337-127">Add the following `using` directives to the top of the code file.</span></span>  
  
     <span data-ttu-id="4c337-128">[!code-cs[csProgGuideOfficeHowTo#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-128">[!code-cs[csProgGuideOfficeHowTo#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_1.cs)]</span></span>  
  
### <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="4c337-129">銀行口座の一覧を作成するには</span><span class="sxs-lookup"><span data-stu-id="4c337-129">To create a list of bank accounts</span></span>  
  
1.  <span data-ttu-id="4c337-130">次のクラス定義を **Program.cs** の `Program` クラスの下に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4c337-130">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>  
  
     <span data-ttu-id="4c337-131">[!code-cs[csProgGuideOfficeHowTo#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-131">[!code-cs[csProgGuideOfficeHowTo#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_2.cs)]</span></span>  
  
2.  <span data-ttu-id="4c337-132">次のコードを `Main` メソッドに追加して、2 つの口座を含む `bankAccounts` 一覧を作成します。</span><span class="sxs-lookup"><span data-stu-id="4c337-132">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>  
  
     <span data-ttu-id="4c337-133">[!code-cs[csProgGuideOfficeHowTo#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-133">[!code-cs[csProgGuideOfficeHowTo#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_3.cs)]</span></span>  
  
### <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="4c337-134">口座情報を Excel にエクスポートするメソッドを宣言するには</span><span class="sxs-lookup"><span data-stu-id="4c337-134">To declare a method that exports account information to Excel</span></span>  
  
1.  <span data-ttu-id="4c337-135">次のメソッドを `Program` クラスに追加して、Excel ワークシートを設定します。</span><span class="sxs-lookup"><span data-stu-id="4c337-135">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>  
  
     <span data-ttu-id="4c337-136">[Add](http://go.microsoft.com/fwlink/?LinkId=210910) メソッドには、特定のテンプレートを指定する省略可能なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="4c337-136">Method [Add](http://go.microsoft.com/fwlink/?LinkId=210910) has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="4c337-137">[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] の新機能であるオプションのパラメーターでは、パラメーターの既定値を使用する場合は、そのパラメーターの引数を省略することができます。</span><span class="sxs-lookup"><span data-stu-id="4c337-137">Optional parameters, new in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="4c337-138">次のコードで引数が渡されないため、`Add` は、既定のテンプレートを使用して、新しいブックを作成します。</span><span class="sxs-lookup"><span data-stu-id="4c337-138">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="4c337-139">以前のバージョンの C# では、同等のステートメントには、プレースホルダーの引数 `ExcelApp.Workbooks.Add(Type.Missing)` が必要です。</span><span class="sxs-lookup"><span data-stu-id="4c337-139">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>  
  
     <span data-ttu-id="4c337-140">[!code-cs[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-140">[!code-cs[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]</span></span>  
  
2.  <span data-ttu-id="4c337-141">次のコードを `DisplayInExcel` の末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="4c337-141">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="4c337-142">このコードでは、ワークシートの最初の行の最初の 2 つの列に値が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-142">The code inserts values into the first two columns of the first row of the worksheet.</span></span>  
  
     <span data-ttu-id="4c337-143">[!code-cs[csProgGuideOfficeHowTo#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-143">[!code-cs[csProgGuideOfficeHowTo#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_5.cs)]</span></span>  
  
3.  <span data-ttu-id="4c337-144">次のコードを `DisplayInExcel` の末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="4c337-144">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="4c337-145">`foreach` ループでは、ワークシートの連続した行の最初の 2 つの列に口座の一覧の情報が配置されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-145">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>  
  
     <span data-ttu-id="4c337-146">[!code-cs[csProgGuideOfficeHowTo#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-146">[!code-cs[csProgGuideOfficeHowTo#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_6.cs)]</span></span>  
  
4.  <span data-ttu-id="4c337-147">次のコードを `DisplayInExcel` の末尾に追加して、コンテンツに合わせて列の幅を調整します。</span><span class="sxs-lookup"><span data-stu-id="4c337-147">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>  
  
     <span data-ttu-id="4c337-148">[!code-cs[csProgGuideOfficeHowTo#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-148">[!code-cs[csProgGuideOfficeHowTo#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_7.cs)]</span></span>  
  
     <span data-ttu-id="4c337-149">C# の以前のバージョンでは、`ExcelApp.Columns[1]` が `Object` を返し、`AutoFit` が Excel [Range](http://go.microsoft.com/fwlink/?LinkId=210911) メソッドであるため、これらの操作の明示的なキャストが必要です。</span><span class="sxs-lookup"><span data-stu-id="4c337-149">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel [Range](http://go.microsoft.com/fwlink/?LinkId=210911) method.</span></span> <span data-ttu-id="4c337-150">次の行にキャストを示します。</span><span class="sxs-lookup"><span data-stu-id="4c337-150">The following lines show the casting.</span></span>  
  
     <span data-ttu-id="4c337-151">[!code-cs[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-151">[!code-cs[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]</span></span>  
  
     [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="4c337-152"> 以降のバージョンでは、アセンブリが [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) コンパイラ オプションで参照される場合、または同等に、Excel の **[相互運用機能型の埋め込み]** プロパティが true に設定されている場合は、返される `Object` が `dynamic` に自動的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-152">, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="4c337-153">このプロパティの既定値は true です。</span><span class="sxs-lookup"><span data-stu-id="4c337-153">True is the default value for this property.</span></span>  
  
### <a name="to-run-the-project"></a><span data-ttu-id="4c337-154">プロジェクトを実行するには</span><span class="sxs-lookup"><span data-stu-id="4c337-154">To run the project</span></span>  
  
1.  <span data-ttu-id="4c337-155">`Main` の末尾に次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="4c337-155">Add the following line at the end of `Main`.</span></span>  
  
     <span data-ttu-id="4c337-156">[!code-cs[csProgGuideOfficeHowTo#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-156">[!code-cs[csProgGuideOfficeHowTo#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_9.cs)]</span></span>  
  
2.  <span data-ttu-id="4c337-157">Ctrl キーを押しながら、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4c337-157">Press CTRL+F5.</span></span>  
  
     <span data-ttu-id="4c337-158">2 つの口座からのデータを含む Excel ワークシートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-158">An Excel worksheet appears that contains the data from the two accounts.</span></span>  
  
### <a name="to-add-a-word-document"></a><span data-ttu-id="4c337-159">Word 文書を追加するには</span><span class="sxs-lookup"><span data-stu-id="4c337-159">To add a Word document</span></span>  
  
1.  <span data-ttu-id="4c337-160">[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] およびそれ以降のバージョンで Office プログラミングを強化するその他の方法を説明するために、次のコードでは、Word アプリケーションを開き、Excel ワークシートにリンクするアイコンを作成します。</span><span class="sxs-lookup"><span data-stu-id="4c337-160">To illustrate additional ways in which [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>  
  
     <span data-ttu-id="4c337-161">この手順の後半で提供されている `CreateIconInWordDoc` メソッドを `Program` クラスに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4c337-161">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="4c337-162">[Add](http://go.microsoft.com/fwlink/?LinkId=210937) メソッドと [PasteSpecial](http://go.microsoft.com/fwlink/?LinkId=147099) メソッドの呼び出しに伴う複雑さが、`CreateIconInWordDoc` の名前付き引数と省略可能な引数によって軽減されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-162">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to [Add](http://go.microsoft.com/fwlink/?LinkId=210937) and [PasteSpecial](http://go.microsoft.com/fwlink/?LinkId=147099).</span></span> <span data-ttu-id="4c337-163">これらの呼び出しによって、[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] で導入された、参照パラメーターを持つ COM メソッドの呼び出しを簡略化する 2 つの他の新しい機能が組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="4c337-163">These calls incorporate two other new features introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="4c337-164">第一に、値パラメーターの場合と同様に参照パラメーターに引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4c337-164">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="4c337-165">つまり、参照パラメーターごとに変数を作成することなく値を直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4c337-165">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="4c337-166">コンパイラは引数の値を保持する一時変数を生成し、呼び出しから戻るときに変数を破棄します。</span><span class="sxs-lookup"><span data-stu-id="4c337-166">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="4c337-167">第二に、引数リスト内の `ref` キーワードを省略できます。</span><span class="sxs-lookup"><span data-stu-id="4c337-167">Second, you can omit the `ref` keyword in the argument list.</span></span>  
  
     <span data-ttu-id="4c337-168">`Add` メソッドには 4 つの参照パラメーターがあり、これらはすべてオプションです。</span><span class="sxs-lookup"><span data-stu-id="4c337-168">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="4c337-169">[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 以降のバージョンでは、既定値を使用する場合は、任意またはすべてのパラメーターの引数を省略できます。</span><span class="sxs-lookup"><span data-stu-id="4c337-169">In [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], or later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="4c337-170">[!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 以前のバージョンでは、各パラメーターの引数を提供する必要があり、パラメーターが参照パラメーターであるため、引数は変数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c337-170">In [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>  
  
     <span data-ttu-id="4c337-171">`PasteSpecial` メソッドは、クリップボードの内容を挿入します。</span><span class="sxs-lookup"><span data-stu-id="4c337-171">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="4c337-172">このメソッドには 7 つの参照パラメーターがあり、これらはすべてオプションです。</span><span class="sxs-lookup"><span data-stu-id="4c337-172">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="4c337-173">次のコードでは、クリップボードの内容のソースへのリンクを作成する `Link` とリンクをアイコンとして表示する `DisplayAsIcon` の 2 つの参照パラメーターの引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="4c337-173">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="4c337-174">[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] では、これら 2 つに名前付き引数を使用して、その他を省略できます。</span><span class="sxs-lookup"><span data-stu-id="4c337-174">In [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="4c337-175">これらは参照パラメーターですが、`ref` キーワードを使用したり、引数として渡す変数を作成したりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c337-175">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="4c337-176">値は直接渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4c337-176">You can send the values directly.</span></span> <span data-ttu-id="4c337-177">[!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 以前のバージョンでは、各参照パラメーターに変数引数を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c337-177">In [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] and earlier versions, you must send a variable argument for each reference parameter.</span></span>  
  
     <span data-ttu-id="4c337-178">[!code-cs[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-178">[!code-cs[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]</span></span>  
  
     <span data-ttu-id="4c337-179">[!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 以前のバージョンの言語では、次のより複雑なコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="4c337-179">In [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] or earlier versions of the language, the following more complex code is required.</span></span>  
  
     <span data-ttu-id="4c337-180">[!code-cs[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-180">[!code-cs[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]</span></span>  
  
2.  <span data-ttu-id="4c337-181">次のステートメントを `Main` の末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="4c337-181">Add the following statement at the end of `Main`.</span></span>  
  
     <span data-ttu-id="4c337-182">[!code-cs[csProgGuideOfficeHowTo#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_12.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-182">[!code-cs[csProgGuideOfficeHowTo#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_12.cs)]</span></span>  
  
3.  <span data-ttu-id="4c337-183">次のステートメントを `DisplayInExcel` の末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="4c337-183">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="4c337-184">`Copy` メソッドはクリップボードにワークシートを追加します。</span><span class="sxs-lookup"><span data-stu-id="4c337-184">The `Copy` method adds the worksheet to the Clipboard.</span></span>  
  
     <span data-ttu-id="4c337-185">[!code-cs[csProgGuideOfficeHowTo#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_13.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-185">[!code-cs[csProgGuideOfficeHowTo#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_13.cs)]</span></span>  
  
4.  <span data-ttu-id="4c337-186">Ctrl キーを押しながら、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4c337-186">Press CTRL+F5.</span></span>  
  
     <span data-ttu-id="4c337-187">アイコンを含む Word 文書が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-187">A Word document appears that contains an icon.</span></span> <span data-ttu-id="4c337-188">ワークシートを前面に表示するアイコンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="4c337-188">Double-click the icon to bring the worksheet to the foreground.</span></span>  
  
### <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="4c337-189">[相互運用機能型の埋め込み] プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="4c337-189">To set the Embed Interop Types property</span></span>  
  
1.  <span data-ttu-id="4c337-190">実行時に、プライマリ相互運用機能アセンブリ (PIA) を必要としない COM 型を呼び出すときに、追加の拡張が可能です。</span><span class="sxs-lookup"><span data-stu-id="4c337-190">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="4c337-191">PIA への依存関係を削除することによって、バージョンに依存しない、より簡単な展開が実現されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-191">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="4c337-192">PIA を使用しないプログラミングのメリットの詳細については、「[チュートリアル: マネージ アセンブリからの型の埋め込み](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c337-192">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
     <span data-ttu-id="4c337-193">また、`dynamic` ではなく `Object` 型を使用して、COM メソッドに必要とされ、COM メソッドによって返される型を簡単に表現できるため、プログラミングがより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="4c337-193">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="4c337-194">型が `dynamic` の変数は、明示的なキャストが不要になる実行時まで評価されません。</span><span class="sxs-lookup"><span data-stu-id="4c337-194">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="4c337-195">詳細については、「[dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c337-195">For more information, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
     <span data-ttu-id="4c337-196">[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] の既定の動作では、PIA を使用せずに型情報を埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="4c337-196">In [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="4c337-197">この既定のため、前の例のいくつかは、明示的なキャストが必要ないために簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-197">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="4c337-198">たとえば、`worksheet` での `DisplayInExcel` の宣言は、`Excel._Worksheet workSheet = excelApp.ActiveSheet` ではなく `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet` と記述されます。</span><span class="sxs-lookup"><span data-stu-id="4c337-198">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="4c337-199">同じメソッドの `AutoFit` への呼び出しでも、既定値を使用せずに明示的なキャストが必要になります。これは、`ExcelApp.Columns[1]` が `Object` を返し、`AutoFit` が Excel のメソッドであるためです。</span><span class="sxs-lookup"><span data-stu-id="4c337-199">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="4c337-200">次のコードはキャストを示しています。</span><span class="sxs-lookup"><span data-stu-id="4c337-200">The following code shows the casting.</span></span>  
  
     <span data-ttu-id="4c337-201">[!code-cs[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-201">[!code-cs[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]</span></span>  
  
2.  <span data-ttu-id="4c337-202">既定値を変更し、型情報を埋め込むのではなく PIA を使用するには、**ソリューション エクスプ ローラー**で **[参照設定]** ノードを展開し、**[Microsoft.Office.Interop.Excel]** または **[Microsoft.Office.Interop.Word]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4c337-202">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>  
  
3.  <span data-ttu-id="4c337-203">**[プロパティ]** ウィンドウが表示されない場合は、**F4** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4c337-203">If you cannot see the **Properties** window, press **F4**.</span></span>  
  
4.  <span data-ttu-id="4c337-204">プロパティの一覧で **[相互運用機能型の埋め込み]** を見つけて、値を **[False]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="4c337-204">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="4c337-205">同様に、コマンド プロンプトで [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) の代わりに [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) コンパイラ オプションを使用してコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="4c337-205">Equivalently, you can compile by using the [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>  
  
### <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="4c337-206">テーブルに追加の書式設定を追加するには</span><span class="sxs-lookup"><span data-stu-id="4c337-206">To add additional formatting to the table</span></span>  
  
1.  <span data-ttu-id="4c337-207">`AutoFit` の `DisplayInExcel` への 2 つの呼び出しを次のステートメントに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4c337-207">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>  
  
     <span data-ttu-id="4c337-208">[!code-cs[csProgGuideOfficeHowTo#15](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_14.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-208">[!code-cs[csProgGuideOfficeHowTo#15](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_14.cs)]</span></span>  
  
     <span data-ttu-id="4c337-209">[AutoFormat](http://go.microsoft.com/fwlink/?LinkId=210948) メソッドには、7 つの値パラメーターがあり、これらはすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="4c337-209">The [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=210948) method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="4c337-210">名前付き引数と省略可能な引数を使用すると、一部またはすべてのパラメーターに引数を指定することができます。引数を指定しないこともできます。</span><span class="sxs-lookup"><span data-stu-id="4c337-210">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="4c337-211">前のステートメントでは、1 つのパラメーター `Format` にのみ引数が指定されています。</span><span class="sxs-lookup"><span data-stu-id="4c337-211">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="4c337-212">`Format` はパラメーター リストの最初のパラメーターであるため、パラメーター名を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c337-212">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="4c337-213">ただし、次のコードに示すように、パラメーター名が含まれている場合、ステートメントがわかりやすい場合があります。</span><span class="sxs-lookup"><span data-stu-id="4c337-213">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>  
  
     <span data-ttu-id="4c337-214">[!code-cs[csProgGuideOfficeHowTo#16](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_15.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-214">[!code-cs[csProgGuideOfficeHowTo#16](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_15.cs)]</span></span>  
  
2.  <span data-ttu-id="4c337-215">Ctrl + F5 キーを押して結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="4c337-215">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="4c337-216">その他の形式は、[XlRangeAutoFormat](http://go.microsoft.com/fwlink/?LinkId=210967) 列挙型のページに掲載されています。</span><span class="sxs-lookup"><span data-stu-id="4c337-216">Other formats are listed in the [XlRangeAutoFormat](http://go.microsoft.com/fwlink/?LinkId=210967) enumeration.</span></span>  
  
3.  <span data-ttu-id="4c337-217">手順 1 のステートメントと [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 以前のバージョンで必要な引数が示されている次のコードを比較します。</span><span class="sxs-lookup"><span data-stu-id="4c337-217">Compare the statement in step 1 with the following code, which shows the arguments that are required in [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] or earlier versions.</span></span>  
  
     <span data-ttu-id="4c337-218">[!code-cs[csProgGuideOfficeHowTo#17](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_16.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-218">[!code-cs[csProgGuideOfficeHowTo#17](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_16.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c337-219">例</span><span class="sxs-lookup"><span data-stu-id="4c337-219">Example</span></span>  
 <span data-ttu-id="4c337-220">コード例全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c337-220">The following code shows the complete example.</span></span>  
  
 <span data-ttu-id="4c337-221">[!code-cs[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c337-221">[!code-cs[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c337-222">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c337-222">See Also</span></span>  
 <span data-ttu-id="4c337-223"><xref:System.Type.Missing?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4c337-223"><xref:System.Type.Missing?displayProperty=fullName></span></span>   
 <span data-ttu-id="4c337-224">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="4c337-224">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span></span>  
 <span data-ttu-id="4c337-225">[dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="4c337-225">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="4c337-226">[名前付き引数と省略可能な引数](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="4c337-226">[Named and Optional Arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span></span>  
 [<span data-ttu-id="4c337-227">方法: Office プログラミングで名前付き引数と省略可能な引数を使用する</span><span class="sxs-lookup"><span data-stu-id="4c337-227">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)

