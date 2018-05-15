---
title: C# コンパイラ オプション
ms.date: 07/20/2015
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: a305daee2349341527b529c7556cc6fa84cc9fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="c-compiler-options"></a><span data-ttu-id="bdc9d-102">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="bdc9d-102">C# Compiler Options</span></span>
<span data-ttu-id="bdc9d-103">コンパイラは、実行可能ファイル (.exe)、ダイナミック リンク ライブラリ (.dll)、またはコード モジュール (.netmodule) を生成します。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="bdc9d-104">すべてのコンパイル オプションは、**-option** および **/option** という 2 つの形で使用できます。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="bdc9d-105">このドキュメントでは、**-option** のみを示しています。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-105">The documentation only shows the **-option** form.</span></span>  
  
 <span data-ttu-id="bdc9d-106">Visual Studio では、コンパイラ オプションは web.config ファイルに設定します。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-106">In Visual Studio, you set compiler options in the web.config file.</span></span> <span data-ttu-id="bdc9d-107">詳細については、「[\<compiler> 要素](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdc9d-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bdc9d-108">In This Section</span></span>  
 [<span data-ttu-id="bdc9d-109">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="bdc9d-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="bdc9d-110">コマンドラインからの Visual C# アプリケーションの構築に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="bdc9d-111">方法: Visual Studio のコマンドラインのための環境変数を設定する</span><span class="sxs-lookup"><span data-stu-id="bdc9d-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="bdc9d-112">vsvars32.bat を実行してコマンドライン ビルドを有効にするための手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="bdc9d-113">カテゴリ別の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="bdc9d-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="bdc9d-114">コンパイラ オプションのカテゴリ別の一覧です。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="bdc9d-115">アルファベット順の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="bdc9d-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="bdc9d-116">コンパイラ オプションのアルファベット順の一覧です。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bdc9d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdc9d-117">Related Sections</span></span>  
 <span data-ttu-id="bdc9d-118">[プロジェクト デザイナーの [ビルド] ページ](/visualstudio/ide/reference/build-page-project-designer-csharp)</span><span class="sxs-lookup"><span data-stu-id="bdc9d-118">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp)</span></span>  
 <span data-ttu-id="bdc9d-119">プロジェクトのコンパイル、ビルド、およびデバッグ方法を制御するプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="bdc9d-120">Visual C# プロジェクトのカスタム ビルド手順に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="bdc9d-121">既定のビルドとカスタム ビルド</span><span class="sxs-lookup"><span data-stu-id="bdc9d-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="bdc9d-122">ビルドの種類と構成に関する情報です。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="bdc9d-123">ビルドの準備と管理</span><span class="sxs-lookup"><span data-stu-id="bdc9d-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="bdc9d-124">Visual Studio 開発環境でビルドするための手順です。</span><span class="sxs-lookup"><span data-stu-id="bdc9d-124">Procedures for building within the Visual Studio development environment.</span></span>
