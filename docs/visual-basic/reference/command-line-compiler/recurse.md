---
title: -recurse
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb1cc114c2882aa82787f94a271dd7684c716b01
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-recurse"></a><span data-ttu-id="f50b1-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="f50b1-102">-recurse</span></span>
<span data-ttu-id="f50b1-103">指定されたディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f50b1-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f50b1-104">構文</span><span class="sxs-lookup"><span data-stu-id="f50b1-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f50b1-105">引数</span><span class="sxs-lookup"><span data-stu-id="f50b1-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="f50b1-106">任意。</span><span class="sxs-lookup"><span data-stu-id="f50b1-106">Optional.</span></span> <span data-ttu-id="f50b1-107">検索を開始するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="f50b1-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="f50b1-108">指定しない場合、プロジェクト ディレクトリ内で検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="f50b1-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="f50b1-109">必須。</span><span class="sxs-lookup"><span data-stu-id="f50b1-109">Required.</span></span> <span data-ttu-id="f50b1-110">検索するファイル。</span><span class="sxs-lookup"><span data-stu-id="f50b1-110">The file(s) to search for.</span></span> <span data-ttu-id="f50b1-111">ワイルドカード文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f50b1-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f50b1-112">コメント</span><span class="sxs-lookup"><span data-stu-id="f50b1-112">Remarks</span></span>  
 <span data-ttu-id="f50b1-113">ファイル名にワイルドカードを使用して、プロジェクト ディレクトリ内のすべての一致するファイルを使用せずにコンパイルできます`-recurse`です。</span><span class="sxs-lookup"><span data-stu-id="f50b1-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="f50b1-114">出力ファイル名が指定されていない場合、コンパイラは処理される最初の入力ファイルに出力ファイル名に基づいて行います。</span><span class="sxs-lookup"><span data-stu-id="f50b1-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="f50b1-115">これは、一般に、アルファベット順に表示されるときにコンパイルされたファイルの一覧の最初のファイルです。</span><span class="sxs-lookup"><span data-stu-id="f50b1-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="f50b1-116">この理由は、使用して出力ファイルを指定することをお、`-out`オプション。</span><span class="sxs-lookup"><span data-stu-id="f50b1-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f50b1-117">`-recurse`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="f50b1-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f50b1-118">例</span><span class="sxs-lookup"><span data-stu-id="f50b1-118">Example</span></span>  
 <span data-ttu-id="f50b1-119">次のコマンドはすべて[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]現在のディレクトリ内のファイルです。</span><span class="sxs-lookup"><span data-stu-id="f50b1-119">The following command compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="f50b1-120">次のコマンドはすべて[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]内のファイル、`Test\ABC`ディレクトリと、その下には、そのディレクトリを生成し、`Test.ABC.dll`です。</span><span class="sxs-lookup"><span data-stu-id="f50b1-120">The following command compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f50b1-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f50b1-121">See Also</span></span>  
 [<span data-ttu-id="f50b1-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="f50b1-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f50b1-123">-除外 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f50b1-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="f50b1-124">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="f50b1-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
