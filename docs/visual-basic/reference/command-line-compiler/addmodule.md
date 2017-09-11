---
title: "/addmodule |Microsoft ドキュメント"
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
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
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
ms.openlocfilehash: 2db0db5b5dd94f03e67d8680624e2a4ad23587f7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="addmodule"></a><span data-ttu-id="63b9c-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="63b9c-102">/addmodule</span></span>
<span data-ttu-id="63b9c-103">指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="63b9c-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b9c-104">構文</span><span class="sxs-lookup"><span data-stu-id="63b9c-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="63b9c-105">引数</span><span class="sxs-lookup"><span data-stu-id="63b9c-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="63b9c-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="63b9c-106">Required.</span></span> <span data-ttu-id="63b9c-107">メタデータが含まれますが、アセンブリのマニフェストが含まれていないファイルのコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="63b9c-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="63b9c-108">空白を含むファイル名を引用符で囲む必要があります ("") です。</span><span class="sxs-lookup"><span data-stu-id="63b9c-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63b9c-109">コメント</span><span class="sxs-lookup"><span data-stu-id="63b9c-109">Remarks</span></span>  
 <span data-ttu-id="63b9c-110">示されているファイル、`fileList`パラメーターを使って作成する必要があります、`/target:module`オプション、または別のコンパイラのと同じ`/target:module`します。</span><span class="sxs-lookup"><span data-stu-id="63b9c-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="63b9c-111">追加したすべてのモジュール`/addmodule`実行時に出力ファイルと同じディレクトリにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="63b9c-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="63b9c-112">つまり、コンパイル時に任意のディレクトリにモジュールを指定することができますが、モジュールは、実行時にアプリケーション ディレクトリにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="63b9c-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="63b9c-113">そうでない場合、<xref:System.TypeLoadException>エラー</xref:System.TypeLoadException> 。</span><span class="sxs-lookup"><span data-stu-id="63b9c-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="63b9c-114">(暗黙的または明示的に) を指定する場合、[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外のオプション`/target:module`と`/addmodule`に渡すファイル`/addmodule`プロジェクトのアセンブリの一部になります。</span><span class="sxs-lookup"><span data-stu-id="63b9c-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="63b9c-115">いずれかを含む出力ファイルを実行するアセンブリが必要かで追加された複数のファイル`/addmodule`します。</span><span class="sxs-lookup"><span data-stu-id="63b9c-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="63b9c-116">使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)アセンブリが格納されているファイルからメタデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="63b9c-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63b9c-117">`/addmodule`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="63b9c-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b9c-118">例</span><span class="sxs-lookup"><span data-stu-id="63b9c-118">Example</span></span>  
 <span data-ttu-id="63b9c-119">次のコードでは、モジュールを作成します。</span><span class="sxs-lookup"><span data-stu-id="63b9c-119">The following code creates a module.</span></span>  
  
 <span data-ttu-id="63b9c-120">[!code-vb[VbVbalrCompiler #&47;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="63b9c-120">[!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span></span>  
  
 <span data-ttu-id="63b9c-121">次のコードでは、モジュールの型をインポートします。</span><span class="sxs-lookup"><span data-stu-id="63b9c-121">The following code imports the module's types.</span></span>  
  
 <span data-ttu-id="63b9c-122">[!code-vb[VbVbalrCompiler #&48;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="63b9c-122">[!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span></span>  
  
 <span data-ttu-id="63b9c-123">実行すると`t1`、出力`802`します。</span><span class="sxs-lookup"><span data-stu-id="63b9c-123">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b9c-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="63b9c-124">See Also</span></span>  
 <span data-ttu-id="63b9c-125">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="63b9c-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="63b9c-126"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="63b9c-126"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="63b9c-127"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="63b9c-127"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="63b9c-128"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="63b9c-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
