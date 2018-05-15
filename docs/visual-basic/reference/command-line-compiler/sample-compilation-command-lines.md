---
title: コンパイル コマンド ラインのサンプル (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0f1fc1d269801efdbf2e89d10679dc8159851f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="0c352-102">コンパイル コマンドラインのサンプル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c352-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="0c352-103">Visual Studio 内から Visual Basic プログラムをコンパイルする代わりに、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルを生成するためにコマンドラインからコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="0c352-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="0c352-104">Visual Basic のコマンド ライン コンパイラは、出力ファイル、アセンブリ、およびデバッグおよびプリプロセッサ オプションおよび入力を制御するオプションの完全なセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="0c352-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="0c352-105">各オプションは、2 つの交換形式で利用可能:`-option`と`/option`です。</span><span class="sxs-lookup"><span data-stu-id="0c352-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="0c352-106">このドキュメントのみが表示されます、`-option`フォーム。</span><span class="sxs-lookup"><span data-stu-id="0c352-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="0c352-107">次の表は、独自の用途を変更するサンプルのコマンドラインを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0c352-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="0c352-108">終了</span><span class="sxs-lookup"><span data-stu-id="0c352-108">To</span></span>|<span data-ttu-id="0c352-109">使用</span><span class="sxs-lookup"><span data-stu-id="0c352-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="0c352-110">File.vb をコンパイルして File.exe を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c352-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="0c352-111">File.vb をコンパイルして File.dll を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c352-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="0c352-112">File.vb をコンパイルして My.exe を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c352-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="0c352-113">File.vb をコンパイルし、ライブラリと File.dll をという名前の参照アセンブリの両方を作成</span><span class="sxs-lookup"><span data-stu-id="0c352-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="0c352-114">最適化して、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルし、 `DEBUG` File2.exe を生成したシンボルを定義するには、</span><span class="sxs-lookup"><span data-stu-id="0c352-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="0c352-115">ロゴや警告を表示することがなく、デバッグ バージョンの File2.dll を生成する、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="0c352-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="0c352-116">Something.dll を現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="0c352-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="0c352-117">関連付けられているに関する情報を表示するには、Visual Studio IDE を使用してプロジェクトをビルドするときに**vbc**コマンドは、出力ウィンドウでコンパイラ オプションとします。</span><span class="sxs-lookup"><span data-stu-id="0c352-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="0c352-118">この情報を表示、開く、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**またはより高度な詳細度。</span><span class="sxs-lookup"><span data-stu-id="0c352-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="0c352-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c352-119">See Also</span></span>  
 [<span data-ttu-id="0c352-120">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="0c352-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0c352-121">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="0c352-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
