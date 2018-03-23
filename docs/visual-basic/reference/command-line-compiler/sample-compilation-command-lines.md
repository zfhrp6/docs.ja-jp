---
title: コンパイル コマンド ラインのサンプル (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7c3fac318e05c5e3d6fb9dd7117cac70ead03dc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="78c51-102">コンパイル コマンドラインのサンプル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78c51-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="78c51-103">コンパイルする代わりに[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]内からプログラム[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルを生成するためにコマンドラインからコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="78c51-103">As an alternative to compiling [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs from within [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="78c51-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コマンド ライン コンパイラは、入力と出力ファイル、アセンブリ、およびデバッグを制御するオプションとプリプロセッサ オプションの完全なセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="78c51-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="78c51-105">各オプションは、2 つの交換形式で利用可能:`-option`と`/option`です。</span><span class="sxs-lookup"><span data-stu-id="78c51-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="78c51-106">このドキュメントのみが表示されます、`-option`フォーム。</span><span class="sxs-lookup"><span data-stu-id="78c51-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="78c51-107">次の表は、独自の用途を変更するサンプルのコマンドラインを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="78c51-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="78c51-108">終了</span><span class="sxs-lookup"><span data-stu-id="78c51-108">To</span></span>|<span data-ttu-id="78c51-109">使用</span><span class="sxs-lookup"><span data-stu-id="78c51-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="78c51-110">File.vb をコンパイルして File.exe を作成します。</span><span class="sxs-lookup"><span data-stu-id="78c51-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="78c51-111">File.vb をコンパイルして File.dll を作成します。</span><span class="sxs-lookup"><span data-stu-id="78c51-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="78c51-112">File.vb をコンパイルして My.exe を作成します。</span><span class="sxs-lookup"><span data-stu-id="78c51-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="78c51-113">すべてコンパイル[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を最適化して、現在のディレクトリ内のファイルと`DEBUG`File2.exe を生成したシンボルを定義するには、</span><span class="sxs-lookup"><span data-stu-id="78c51-113">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="78c51-114">すべてコンパイル[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ロゴや警告を表示することがなく、デバッグ バージョンの File2.dll を生成する、現在のディレクトリ内のファイル</span><span class="sxs-lookup"><span data-stu-id="78c51-114">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="78c51-115">すべてコンパイル[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Something.dll を現在のディレクトリ内のファイル</span><span class="sxs-lookup"><span data-stu-id="78c51-115">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
 <span data-ttu-id="78c51-116">をコマンドラインからコンパイルするときは、Microsoft を明示的に参照する必要があります[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]経由のランタイム ライブラリ、`-reference`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="78c51-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] run-time library through the `-reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="78c51-117">関連付けられているに関する情報を表示するには、Visual Studio IDE を使用してプロジェクトをビルドするときに**vbc**コマンドは、出力ウィンドウでコンパイラ オプションとします。</span><span class="sxs-lookup"><span data-stu-id="78c51-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="78c51-118">この情報を表示、開く、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**またはより高度な詳細度。</span><span class="sxs-lookup"><span data-stu-id="78c51-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="78c51-119">詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="78c51-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c51-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="78c51-120">See Also</span></span>  
 [<span data-ttu-id="78c51-121">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="78c51-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="78c51-122">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="78c51-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
