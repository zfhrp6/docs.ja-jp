---
title: "サンプルのコンパイル コマンドライン (Visual Basic) |Microsoft ドキュメント"
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
- command line, compilers
- compilation, command-line
- command-line compilers
- compiling source code, from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
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
ms.openlocfilehash: e58006c05f498ec1a9dbf5194fbc9bcdd281ab63
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="f10ab-102">コンパイル コマンド ラインのサンプル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f10ab-102">Sample Compilation Command Lines (Visual Basic)</span></span>
<span data-ttu-id="f10ab-103">コンパイルする代わりに[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]内からプログラム[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]、実行可能 (.exe) ファイルまたはダイナミック リンク ライブラリ (.dll) ファイルを生成するためのコマンドラインからコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="f10ab-103">As an alternative to compiling [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programs from within [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="f10ab-104">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コマンド ライン コンパイラは、入力呼び出し力ファイル、アセンブリ、およびデバッグを制御するオプションとプリプロセッサのオプションの完全なセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f10ab-104">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="f10ab-105">各オプションは、2 つの交換可能な形式で利用可能:`-``option`と`/``option`です。</span><span class="sxs-lookup"><span data-stu-id="f10ab-105">Each option is available in two interchangeable forms: `-``option` and `/``option`.</span></span> <span data-ttu-id="f10ab-106">このドキュメントの表示のみ、`/``option`フォームです。</span><span class="sxs-lookup"><span data-stu-id="f10ab-106">This documentation shows only the `/``option` form.</span></span>  
  
 <span data-ttu-id="f10ab-107">次の表は、独自の変更できるサンプルのコマンドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="f10ab-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="f10ab-108">目的</span><span class="sxs-lookup"><span data-stu-id="f10ab-108">To</span></span>|<span data-ttu-id="f10ab-109">用途</span><span class="sxs-lookup"><span data-stu-id="f10ab-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="f10ab-110">.Vb というファイルをコンパイルして File.exe を作成します。</span><span class="sxs-lookup"><span data-stu-id="f10ab-110">Compile File.vb and create File.exe</span></span>|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="f10ab-111">.Vb というファイルをコンパイルして作成します</span><span class="sxs-lookup"><span data-stu-id="f10ab-111">Compile File.vb and create File.dll</span></span>|`vbc /target:library File.vb`|  
|<span data-ttu-id="f10ab-112">.Vb というファイルをコンパイルして My.exe を作成します。</span><span class="sxs-lookup"><span data-stu-id="f10ab-112">Compile File.vb and create My.exe</span></span>|`vbc /out:My.exe File.vb`|  
|<span data-ttu-id="f10ab-113">すべてコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ファイルを現在のディレクトリに、最適化を有効にし、`DEBUG`シンボルを定義するには、File2.exe を生成します。</span><span class="sxs-lookup"><span data-stu-id="f10ab-113">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|<span data-ttu-id="f10ab-114">すべてコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ロゴや警告を表示することがなく File2.dll のデバッグ バージョンを作成して、現在のディレクトリ内のファイル</span><span class="sxs-lookup"><span data-stu-id="f10ab-114">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|<span data-ttu-id="f10ab-115">すべてコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Something.dll の現在のディレクトリ内のファイル</span><span class="sxs-lookup"><span data-stu-id="f10ab-115">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory to Something.dll</span></span>|`vbc /target:library /out:Something.dll *.vb`|  
  
 <span data-ttu-id="f10ab-116">コマンドラインからコンパイルするときは、Microsoft を明示的に参照する必要があります[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のランタイム ライブラリ、`/reference`コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="f10ab-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="f10ab-117">Visual Studio IDE を使用して、プロジェクトをビルドする場合は、関連付けられたに関する情報を表示できます**vbc**コマンド、出力ウィンドウには、そのコンパイラ オプションにします。</span><span class="sxs-lookup"><span data-stu-id="f10ab-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="f10ab-118">この情報を表示する、[のオプション ダイアログ ボックス、プロジェクトとソリューションをビルドおよび実行](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)、し、設定、 **MSBuild プロジェクトのビルド出力の詳細度**に**標準**または詳細度の高いレベルです。</span><span class="sxs-lookup"><span data-stu-id="f10ab-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="f10ab-119">詳細については、「[方法: ビルド ログ ファイルを表示、保存、および構成する](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f10ab-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f10ab-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f10ab-120">See Also</span></span>  
 <span data-ttu-id="f10ab-121">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="f10ab-121">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="f10ab-122"> [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span><span class="sxs-lookup"><span data-stu-id="f10ab-122"> [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span></span>
