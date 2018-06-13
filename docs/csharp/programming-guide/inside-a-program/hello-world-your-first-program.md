---
title: Hello World -- 最初のプログラム (C# プログラミング ガイド)
ms.date: 07/20/2015
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: 904657175d87e0d78e518248ed89b3720227360f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339171"
---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="bb3d8-102">Hello World -- 最初のプログラム (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="bb3d8-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="bb3d8-103">次の手順では、従来の "Hello World!" プログラムの C# バージョンを</span><span class="sxs-lookup"><span data-stu-id="bb3d8-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="bb3d8-104">作成します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-104">program.</span></span> <span data-ttu-id="bb3d8-105">このプログラムでは `Hello World!` という文字列を表示します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="bb3d8-106">基本概念の例については、「[Visual C# と Visual Basic の概要](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="bb3d8-107">コンソール アプリケーションを作成し、実行するには</span><span class="sxs-lookup"><span data-stu-id="bb3d8-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="bb3d8-108">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="bb3d8-109">メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="bb3d8-110">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="bb3d8-111">**[インストール済み]**、**[テンプレート]**、**[Visual C#]** の順に展開し、**[コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="bb3d8-112">**[名前]** ボックスにプロジェクト名を指定し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="bb3d8-113">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="bb3d8-114">**コード エディター**で Program.cs が開いていない場合は、**ソリューション エクスプローラー**で **Program.cs** のショートカット メニューを開き、**[コードの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="bb3d8-115">Program.cs の内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     [!code-csharp[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  <span data-ttu-id="bb3d8-116">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-116">Choose the F5 key to run the project.</span></span> <span data-ttu-id="bb3d8-117">`Hello World!` という行を含むコマンド プロンプト ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-117">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="bb3d8-118">次に、このプログラムの重要な部分を調べます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-118">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="bb3d8-119">コメント</span><span class="sxs-lookup"><span data-stu-id="bb3d8-119">Comments</span></span>  
 <span data-ttu-id="bb3d8-120">最初の行はコメントになっています。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-120">The first line contains a comment.</span></span> <span data-ttu-id="bb3d8-121">「`//`」という文字があると、これ以降その行はコメントになります。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-121">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 [!code-csharp[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 <span data-ttu-id="bb3d8-122">テキスト ブロックを `/*` 文字と `*/` 文字で囲んでコメントにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-122">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="bb3d8-123">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-123">This is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## <a name="main-method"></a><span data-ttu-id="bb3d8-124">Main メソッド</span><span class="sxs-lookup"><span data-stu-id="bb3d8-124">Main Method</span></span>  
 <span data-ttu-id="bb3d8-125">C# コンソール アプリケーションには、`Main` メソッドが必要です。このメソッドの中で制御を開始して終了します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-125">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="bb3d8-126">`Main` メソッドでは、オブジェクトを作成し、ほかのメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-126">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="bb3d8-127">`Main` メソッドはクラスまたは構造体の中に存在する [static](../../../csharp/language-reference/keywords/static.md) メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-127">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="bb3d8-128">前の "Hello World!" の</span><span class="sxs-lookup"><span data-stu-id="bb3d8-128">In the previous "Hello World!"</span></span> <span data-ttu-id="bb3d8-129">例では、`Hello` という名前のクラスに存在していました。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-129">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="bb3d8-130">次の方法のいずれかで `Main` メソッドを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-130">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="bb3d8-131">`void` 型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-131">It can return `void`.</span></span>  
  
     [!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   <span data-ttu-id="bb3d8-132">整数を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-132">It can also return an integer.</span></span>  
  
     [!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   <span data-ttu-id="bb3d8-133">どちらの戻り値の型でも、次のように引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-133">With either of the return types, it can take arguments.</span></span>  
  
     [!code-csharp[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     <span data-ttu-id="bb3d8-134">- または -</span><span class="sxs-lookup"><span data-stu-id="bb3d8-134">-or-</span></span>  
  
     [!code-csharp[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 <span data-ttu-id="bb3d8-135">`Main` メソッドのパラメーターである `args` は、`string` の配列で、プログラムの実行時に使用したコマンド ライン引数を含みます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-135">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="bb3d8-136">C++ とは異なり、この配列には実行可能 (exe) ファイルの名前は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-136">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="bb3d8-137">コマンド ライン引数の使用方法の詳細については、「[Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)」および「[方法: コマンド ラインを使用してアセンブリを作成および使用する](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-137">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="bb3d8-138"><xref:System.Console.ReadKey%2A> メソッドの末尾で `Main` を呼び出すと、F5 キーを押してデバッグ モードでプログラムを実行するときに、出力を読み取る前にコンソール ウィンドウが終了することを回避できます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-138">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="bb3d8-139">入出力</span><span class="sxs-lookup"><span data-stu-id="bb3d8-139">Input and Output</span></span>  
 <span data-ttu-id="bb3d8-140">C# プログラムは、普通、.NET Framework のランタイム ライブラリが提供する入出力サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-140">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="bb3d8-141">ステートメント `System.Console.WriteLine("Hello World!");` では、<xref:System.Console.WriteLine%2A> メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-141">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="bb3d8-142">これは、ランタイム ライブラリの <xref:System.Console> クラスの出力メソッドの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-142">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="bb3d8-143">文字列パラメーターを標準出力ストリームに出力し、最後に改行を付け加えます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-143">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="bb3d8-144">別の入出力操作には、他の <xref:System.Console> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-144">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="bb3d8-145">`using System;` ディレクティブをプログラムの開始時にインクルードした場合は、完全に修飾せずに <xref:System> クラスおよびメソッドを直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-145">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="bb3d8-146">たとえば、`Console.WriteLine` の代わりに `System.Console.WriteLine` を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-146">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-csharp[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 <span data-ttu-id="bb3d8-147">入出力メソッドの詳細については、「<xref:System.IO>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-147">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="bb3d8-148">コマンド ライン コンパイルと実行</span><span class="sxs-lookup"><span data-stu-id="bb3d8-148">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="bb3d8-149">"Hello World!" プログラムは、</span><span class="sxs-lookup"><span data-stu-id="bb3d8-149">You can compile the "Hello World!"</span></span> <span data-ttu-id="bb3d8-150">Visual Studio 統合開発環境 (IDE) の代わりに、コマンド ラインを使用してコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-150">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="bb3d8-151">コマンド プロンプトからコンパイルおよび実行するには</span><span class="sxs-lookup"><span data-stu-id="bb3d8-151">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="bb3d8-152">前の手順のコードをテキスト エディターに貼り付け、テキスト ファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-152">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="bb3d8-153">そのファイルに `Hello.cs` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-153">Name the file `Hello.cs`.</span></span> <span data-ttu-id="bb3d8-154">C# のソース コード ファイルでは、`.cs` という拡張子を使います。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-154">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="bb3d8-155">次のいずれかの手順を実行してコマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-155">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="bb3d8-156">Windows 10 の場合、**[スタート]** メニューで `Developer Command Prompt` を検索し、**[開発者コマンド プロンプト for VS 2017]** をタップまたは選択します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-156">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="bb3d8-157">[開発者コマンド プロンプト] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-157">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="bb3d8-158">Windows 7 の場合、**[スタート]** メニューを開き、Visual Studio の現在のバージョンのフォルダーを展開し、**[Visual Studio Tools]** のショートカット メニューを開いて、**[開発者コマンド プロンプト for VS 2017]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-158">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="bb3d8-159">[開発者コマンド プロンプト] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-159">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="bb3d8-160">標準のコマンド プロンプト ウィンドウからコマンド ライン ビルドを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-160">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="bb3d8-161">「[方法: Visual Studio のコマンドラインのための環境変数を設定する](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-161">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="bb3d8-162">コマンド プロンプト ウィンドウで、`Hello.cs` ファイルが格納されているフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-162">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="bb3d8-163">`Hello.cs` をコンパイルするには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-163">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="bb3d8-164">プログラムにコンパイル エラーがない場合、`Hello.exe` という名前の実行可能ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-164">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="bb3d8-165">コマンド プロンプトで、次のコマンドを入力してプログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-165">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="bb3d8-166">C# コンパイラとそのオプションの詳細については、「[C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb3d8-166">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bb3d8-167">参照</span><span class="sxs-lookup"><span data-stu-id="bb3d8-167">See Also</span></span>  
 [<span data-ttu-id="bb3d8-168">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="bb3d8-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bb3d8-169">インサイド C# プログラム</span><span class="sxs-lookup"><span data-stu-id="bb3d8-169">Inside a C# Program</span></span>](../../../csharp/programming-guide/inside-a-program/index.md)  
 [<span data-ttu-id="bb3d8-170">文字列</span><span class="sxs-lookup"><span data-stu-id="bb3d8-170">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="bb3d8-171">\<paveover>C# サンプル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="bb3d8-171">\<paveover>C# Sample Applications</span></span>](http://msdn.microsoft.com/library/9a9d7aaa-51d3-4224-b564-95409b0f3e15)  
 [<span data-ttu-id="bb3d8-172">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="bb3d8-172">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bb3d8-173">Main() とコマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="bb3d8-173">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="bb3d8-174">Visual C# と Visual Basic の概要</span><span class="sxs-lookup"><span data-stu-id="bb3d8-174">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
