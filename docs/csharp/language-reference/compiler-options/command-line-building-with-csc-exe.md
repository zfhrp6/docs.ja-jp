---
title: "csc.exe を使用したコマンド ラインからのビルド"
ms.date: 04/19/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5fe7b735977b0cde0bed266815987b773be6bdbe
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="90267-102">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="90267-102">Command-line build with csc.exe</span></span>
<span data-ttu-id="90267-103">C# コンパイラは、その実行可能ファイルの名前 (*csc.exe*) をコマンド プロンプトに入力することによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="90267-103">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="90267-104">**Visual Studio 用開発者コマンド プロンプト** ウィンドウを使用した場合、必要なすべての環境変数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="90267-104">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="90267-105">このツールを表示する方法については、「[Visual Studio 用開発者コマンド プロンプト](../../../framework/tools/developer-command-prompt-for-vs.md)」トピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="90267-105">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span> 

<span data-ttu-id="90267-106">標準のコマンド プロンプト ウィンドウを使用する場合は、コンピューター上の任意のサブディレクトリから *csc.exe* を呼び出すことができるようにパスを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90267-106">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="90267-107">また、*vsvars32.bat* を実行して、コマンド ライン ビルドをサポートするための適切な環境変数を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90267-107">You also must run *vsvars32.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="90267-108">検索して実行する方法の手順など、*vsvars32.bat* の詳細については、「[方法: Visual Studio のコマンド ラインのための環境変数を設定する](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90267-108">For more information about *vsvars32.bat*, including instructions for how to find and run it, see [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="90267-109">[!INCLUDE[winsdklong](~/includes/winsdklong-md.md)] のみがインストールされているコンピューターでは、**SDK コマンド プロンプト** (**[Microsoft .NET Framework SDK]** メニュー オプションから開くことができます) で C# コンパイラを使用できます。</span><span class="sxs-lookup"><span data-stu-id="90267-109">If you're working on a computer that has only the [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)], you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="90267-110">MSBuild を使用して、プログラムによって C# プログラムをビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="90267-110">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="90267-111">詳細については、「[MSBuild](/visualstudio/msbuild/msbuild)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90267-111">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="90267-112">通常、実行可能ファイル *csc.exe* は、*Windows* ディレクトリの Microsoft.NET\Framework\\*\<バージョン>* フォルダーに格納されています。</span><span class="sxs-lookup"><span data-stu-id="90267-112">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="90267-113">ただし、この格納場所は、特定のコンピューターの構成によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="90267-113">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="90267-114">複数のバージョンの .NET Framework がコンピューターにインストールされている場合、このファイルのバージョンが複数見つかります。</span><span class="sxs-lookup"><span data-stu-id="90267-114">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="90267-115">このようなインストールの詳細については、「[方法: インストールされている .NET Framework バージョンを確認する](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90267-115">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
>  <span data-ttu-id="90267-116">Visual Studio IDE を使用してプロジェクトをビルドすると、**csc** コマンドとその関連するコンパイラ オプションが**出力**ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="90267-116">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="90267-117">この情報を表示するには、「[方法: ビルド ログ ファイルを表示、保存、および構成する](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log)」の手順に従って、ログ データの詳細レベルを **[標準]** または **[詳細]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="90267-117">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="90267-118">プロジェクトをリビルドした後、C# コンパイラの呼び出しを見つけるために**出力**ウィンドウで **csc** を検索します。</span><span class="sxs-lookup"><span data-stu-id="90267-118">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="90267-119">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="90267-119">**In this topic**</span></span>

- [<span data-ttu-id="90267-120">コマンド ライン構文の規則</span><span class="sxs-lookup"><span data-stu-id="90267-120">Rules for command-line syntax</span></span>](#-rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="90267-121">サンプル コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="90267-121">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="90267-122">C# コンパイラと C++ コンパイラの出力の相違点</span><span class="sxs-lookup"><span data-stu-id="90267-122">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="90267-123">C# コンパイラのコマンド ライン構文の規則</span><span class="sxs-lookup"><span data-stu-id="90267-123">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="90267-124">C# コンパイラは、オペレーティング システムのコマンド ラインで指定された引数を次の規則に従って解釈します。</span><span class="sxs-lookup"><span data-stu-id="90267-124">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="90267-125">引数は、空白 (スペースまたはタブ) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="90267-125">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="90267-126">キャレット (^) は、エスケープ文字やデリミターとしては認識されません。</span><span class="sxs-lookup"><span data-stu-id="90267-126">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="90267-127">キャレットは、オペレーティング システムのコマンド ライン パーサーによって処理されてからプログラムの `argv` 配列に渡されます。</span><span class="sxs-lookup"><span data-stu-id="90267-127">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="90267-128">二重引用符で囲まれた文字列 ("string") は、空白を含む場合でも、単一の引数と見なされます。</span><span class="sxs-lookup"><span data-stu-id="90267-128">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="90267-129">二重引用符で囲んだ文字列を引数に埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="90267-129">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="90267-130">円記号を前に付けた二重引用符 (\\") は、リテラル二重引用符文字 (") として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="90267-130">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="90267-131">二重引用符の直前にある円記号以外は、円記号 (\) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="90267-131">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="90267-132">二重引用符の直前に円記号が偶数個 (0 個は含まない) あると、円記号のペアごとに 1 個の円記号が `argv` 配列に格納されます。この場合、二重引用符は文字列のデリミターとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="90267-132">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="90267-133">二重引用符の直前に円記号が奇数個 (3 個以上) あると、円記号のペアごとに 1 個の円記号が `argv` 配列に格納されます。この場合、二重引用符は残った円記号によりエスケープ シーケンスになります。</span><span class="sxs-lookup"><span data-stu-id="90267-133">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="90267-134">これにより、リテラル二重引用符 (") が `argv` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="90267-134">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="90267-135">C# コンパイラのコマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="90267-135">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="90267-136">*File.cs* をコンパイルして *File.exe* を作成します。</span><span class="sxs-lookup"><span data-stu-id="90267-136">Compiles *File.cs* producing *File.exe*:</span></span>

```console
csc File.cs 
```

- <span data-ttu-id="90267-137">*File.cs* をコンパイルして *File.dll* を作成します。</span><span class="sxs-lookup"><span data-stu-id="90267-137">Compiles *File.cs* producing *File.dll*:</span></span>

```console
csc -target:library File.cs
```

- <span data-ttu-id="90267-138">*File.cs* をコンパイルして *My.exe* を作成します。</span><span class="sxs-lookup"><span data-stu-id="90267-138">Compiles *File.cs* and creates *My.exe*:</span></span>

```console
csc -out:My.exe File.cs
```

- <span data-ttu-id="90267-139">最適化を有効にし、DEBUG シンボルを定義して、現在のディレクトリにあるすべての C# ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="90267-139">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="90267-140">*File2.exe* が出力されます。</span><span class="sxs-lookup"><span data-stu-id="90267-140">The output is *File2.exe*:</span></span>

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- <span data-ttu-id="90267-141">現在のディレクトリにあるすべての C# ファイルをコンパイルして、デバッグ バージョンの *File2.dll* を作成します。</span><span class="sxs-lookup"><span data-stu-id="90267-141">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="90267-142">ロゴや警告は表示されません。</span><span class="sxs-lookup"><span data-stu-id="90267-142">No logo and no warnings are displayed:</span></span>

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- <span data-ttu-id="90267-143">現在のディレクトリにあるすべての C# ファイルをコンパイルして、*Something.xyz* (DLL) に出力します。</span><span class="sxs-lookup"><span data-stu-id="90267-143">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="90267-144">C# コンパイラと C++ コンパイラの出力の相違点</span><span class="sxs-lookup"><span data-stu-id="90267-144">Differences between C# compiler and C++ compiler output</span></span>
<span data-ttu-id="90267-145">C# コンパイラを起動してもオブジェクト (*.obj*) ファイルは作成されず、出力ファイルが直接作成されます。</span><span class="sxs-lookup"><span data-stu-id="90267-145">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="90267-146">このため、C# コンパイラにはリンカーが不要です。</span><span class="sxs-lookup"><span data-stu-id="90267-146">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="90267-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="90267-147">See also</span></span>
 [<span data-ttu-id="90267-148">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="90267-148">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="90267-149">アルファベット順の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="90267-149">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [<span data-ttu-id="90267-150">カテゴリ別の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="90267-150">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [<span data-ttu-id="90267-151">Main() とコマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="90267-151">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="90267-152">コマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="90267-152">Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [<span data-ttu-id="90267-153">方法: コマンド ライン引数を表示する</span><span class="sxs-lookup"><span data-stu-id="90267-153">How to: Display Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="90267-154">方法: foreach を使用してコマンド ライン引数にアクセスする</span><span class="sxs-lookup"><span data-stu-id="90267-154">How to: Access Command-Line Arguments Using foreach</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [<span data-ttu-id="90267-155">Main() の戻り値</span><span class="sxs-lookup"><span data-stu-id="90267-155">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
