---
title: コマンド ラインからのビルド (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a9dee47f06e4f7d9fc8d237376df7707130921d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="90ea2-102">コマンド ラインからのビルド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90ea2-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="90ea2-103">Visual Basic プロジェクトで構成された 1 つまたは複数の独立したソース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="90ea2-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="90ea2-104">コンパイルと呼ばれる過程で、これらのファイルが 1 つのパッケージにまとめられて — アプリケーションとして実行できる 1 つの実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="90ea2-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="90ea2-105">Visual Basic では、Visual Studio 統合開発環境 (IDE) 内からプログラムをコンパイルする代わりに、コマンド ライン コンパイラを提供します。</span><span class="sxs-lookup"><span data-stu-id="90ea2-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="90ea2-106">コマンド ライン コンパイラが状況を必要としない、IDE の機能の完全なセット用に設計された — たとえば、またはする場合を使用して限られたシステムのメモリまたはストレージの領域を持つコンピューター用の記述。</span><span class="sxs-lookup"><span data-stu-id="90ea2-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="90ea2-107">Visual Studio IDE 内からソース ファイルをコンパイルするには、選択、**ビルド**コマンドを**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="90ea2-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="90ea2-108">関連付けられているに関する情報を表示するには、Visual Studio IDE を使用してプロジェクト ファイルをビルドするときに**vbc**コマンドと、出力ウィンドウにそのスイッチ。</span><span class="sxs-lookup"><span data-stu-id="90ea2-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="90ea2-109">この情報を表示、開く、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**またはより高度な詳細度。</span><span class="sxs-lookup"><span data-stu-id="90ea2-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="90ea2-110">詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="90ea2-110">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="90ea2-111">MSBuild を使用して、コマンド プロンプトでのプロジェクト (.vbproj) ファイルをコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="90ea2-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="90ea2-112">詳細については、次を参照してください。[コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)と[チュートリアル: MSBuild を使用して](/visualstudio/msbuild/walkthrough-using-msbuild)です。</span><span class="sxs-lookup"><span data-stu-id="90ea2-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90ea2-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="90ea2-113">In This Section</span></span>  
 [<span data-ttu-id="90ea2-114">方法 : コマンド ライン コンパイラを起動する</span><span class="sxs-lookup"><span data-stu-id="90ea2-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="90ea2-115">MS-DOS のプロンプトで、または特定のサブディレクトリからコマンド ライン コンパイラを起動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90ea2-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="90ea2-116">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="90ea2-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="90ea2-117">独自の用途を変更するコマンドラインのサンプルの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="90ea2-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="90ea2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="90ea2-118">Related Sections</span></span>  
 [<span data-ttu-id="90ea2-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="90ea2-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="90ea2-120">アルファベット順または目的別に整理コンパイラ オプションの一覧を提供します。</span><span class="sxs-lookup"><span data-stu-id="90ea2-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="90ea2-121">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="90ea2-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="90ea2-122">コードの特定のセクションをコンパイルする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90ea2-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="90ea2-123">Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン</span><span class="sxs-lookup"><span data-stu-id="90ea2-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="90ea2-124">対象が別のビルドに含まれます、プロジェクトのプロパティ を選択およびが正しい順序でプロジェクトのビルドを整理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="90ea2-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
