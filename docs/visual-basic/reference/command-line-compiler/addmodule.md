---
title: -addmodule
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c17d5541fe2d02ba88f4c5ef259b2248f371dfe5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-addmodule"></a><span data-ttu-id="6d4d0-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="6d4d0-102">-addmodule</span></span>
<span data-ttu-id="6d4d0-103">指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d4d0-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d4d0-105">引数</span><span class="sxs-lookup"><span data-stu-id="6d4d0-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="6d4d0-106">必須。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-106">Required.</span></span> <span data-ttu-id="6d4d0-107">メタデータが含まれますが、アセンブリ マニフェストが含まれていないファイルのコンマ区切り一覧。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="6d4d0-108">空白を含むファイル名を引用符で囲む必要があります ("") です。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d4d0-109">コメント</span><span class="sxs-lookup"><span data-stu-id="6d4d0-109">Remarks</span></span>  
 <span data-ttu-id="6d4d0-110">によって示されているファイル、`fileList`パラメーターを使って作成する必要があります、`-target:module`オプション、または別のコンパイラのと同じ`-target:module`です。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="6d4d0-111">追加したすべてのモジュール`-addmodule`実行時に、出力ファイルと同じディレクトリにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="6d4d0-112">つまり、コンパイル時に、任意のディレクトリにモジュールを指定することができますが、モジュールは、実行時にアプリケーションのディレクトリにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="6d4d0-113">そうでない場合、<xref:System.TypeLoadException>エラーです。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="6d4d0-114">(暗黙的または明示的に) を指定する場合、[-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外のオプション`-target:module`で`-addmodule`に渡すファイル`-addmodule`プロジェクトのアセンブリの一部になります。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="6d4d0-115">アセンブリが 1 つの出力ファイルを実行するために必要なまたは以上のファイル追加`-addmodule`です。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="6d4d0-116">使用して[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)アセンブリが格納されているファイルからメタデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d4d0-117">`-addmodule`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d4d0-118">例</span><span class="sxs-lookup"><span data-stu-id="6d4d0-118">Example</span></span>  
 <span data-ttu-id="6d4d0-119">次のコードでは、モジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="6d4d0-120">次のコードでは、モジュールの型をインポートします。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="6d4d0-121">実行すると`t1`、出力`802`です。</span><span class="sxs-lookup"><span data-stu-id="6d4d0-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4d0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d4d0-122">See Also</span></span>  
 [<span data-ttu-id="6d4d0-123">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="6d4d0-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="6d4d0-124">-ターゲット (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d4d0-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="6d4d0-125">-参照 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d4d0-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="6d4d0-126">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="6d4d0-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
