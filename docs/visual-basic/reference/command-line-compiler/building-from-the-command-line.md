---
title: "コマンド ライン (Visual Basic の場合) からのビルド |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
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
ms.openlocfilehash: e7550a4a54637ea5ef425a1cb7ae02abd07808a8
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="39d2f-102">コマンド ラインからのビルド (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39d2f-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="39d2f-103">A[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクトは&1; つ以上の別のソース ファイルの構成されています。</span><span class="sxs-lookup"><span data-stu-id="39d2f-103">A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project is made up of one or more separate source files.</span></span> <span data-ttu-id="39d2f-104">コンパイルと呼ばれるプロセス中にこれらのファイルが&1; つのパッケージにまとめられて — アプリケーションとして実行できる実行可能ファイルです。</span><span class="sxs-lookup"><span data-stu-id="39d2f-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="39d2f-105">内からプログラムをコンパイルする別の方法として、コマンド ライン コンパイラを提供、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]統合開発環境 (IDE) です。</span><span class="sxs-lookup"><span data-stu-id="39d2f-105"> provides a command-line compiler as an alternative to compiling programs from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] integrated development environment (IDE).</span></span> <span data-ttu-id="39d2f-106">コマンド ライン コンパイラは、IDE の機能の完全なセットが不要になる状況向けに設計-などとまたはいる限られたシステムのメモリや記憶域の空き領域を持つコンピューターの記述。</span><span class="sxs-lookup"><span data-stu-id="39d2f-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
 <span data-ttu-id="39d2f-107">コマンドラインからコンパイルするときは、Microsoft を明示的に参照する必要があります[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のランタイム ライブラリ、`/reference`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="39d2f-107">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
 <span data-ttu-id="39d2f-108">内からソース ファイルをコンパイルする、 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE、選択、**ビルド**コマンドを**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="39d2f-108">To compile source files from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="39d2f-109">Visual Studio IDE を使用してプロジェクト ファイルをビルドする場合は、関連付けられたに関する情報を表示できます**vbc**コマンドと出力 ウィンドウでスイッチにします。</span><span class="sxs-lookup"><span data-stu-id="39d2f-109">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="39d2f-110">この情報を表示する、[オプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**または詳細度の高いレベルです。</span><span class="sxs-lookup"><span data-stu-id="39d2f-110">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="39d2f-111">詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39d2f-111">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="39d2f-112">MSBuild を使用して、コマンド プロンプトで、プロジェクト (.vbproj) ファイルをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="39d2f-112">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="39d2f-113">詳細については、次を参照してください。[コマンド ライン リファレンス](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)と[チュートリアル: MSBuild を使用して](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310)します。</span><span class="sxs-lookup"><span data-stu-id="39d2f-113">For more information, see [Command-Line Reference](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39d2f-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="39d2f-114">In This Section</span></span>  
 [<span data-ttu-id="39d2f-115">方法 : コマンド ライン コンパイラを起動する</span><span class="sxs-lookup"><span data-stu-id="39d2f-115">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="39d2f-116">MS-DOS プロンプトまたは固有のサブディレクトリからコマンド ライン コンパイラを起動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d2f-116">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="39d2f-117">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="39d2f-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="39d2f-118">独自の変更できるコマンドラインのサンプルの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="39d2f-118">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="39d2f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="39d2f-119">Related Sections</span></span>  
 [<span data-ttu-id="39d2f-120">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="39d2f-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="39d2f-121">アルファベット順または目的別に整理コンパイラ オプションの一覧を提供します。</span><span class="sxs-lookup"><span data-stu-id="39d2f-121">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="39d2f-122">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="39d2f-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="39d2f-123">コードの特定のセクションをコンパイルする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d2f-123">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="39d2f-124">Visual Studio でのプロジェクトとソリューションのビルドおよびクリーン</span><span class="sxs-lookup"><span data-stu-id="39d2f-124">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="39d2f-125">どのようなさまざまなビルドに含まれる、プロジェクトのプロパティ を選択および適切な順序でプロジェクトをビルドすることを確認整理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39d2f-125">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
