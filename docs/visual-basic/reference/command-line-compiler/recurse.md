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
ms.openlocfilehash: 195d4b8f8e88d22e63c29ab9152399eb5c4a19df
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="-recurse"></a><span data-ttu-id="f9159-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="f9159-102">-recurse</span></span>
<span data-ttu-id="f9159-103">指定されたディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f9159-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9159-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9159-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9159-105">引数</span><span class="sxs-lookup"><span data-stu-id="f9159-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="f9159-106">任意。</span><span class="sxs-lookup"><span data-stu-id="f9159-106">Optional.</span></span> <span data-ttu-id="f9159-107">検索を開始するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="f9159-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="f9159-108">指定しない場合、プロジェクト ディレクトリ内で検索を開始します。</span><span class="sxs-lookup"><span data-stu-id="f9159-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="f9159-109">必須。</span><span class="sxs-lookup"><span data-stu-id="f9159-109">Required.</span></span> <span data-ttu-id="f9159-110">検索するファイル。</span><span class="sxs-lookup"><span data-stu-id="f9159-110">The file(s) to search for.</span></span> <span data-ttu-id="f9159-111">ワイルドカード文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9159-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9159-112">コメント</span><span class="sxs-lookup"><span data-stu-id="f9159-112">Remarks</span></span>  
 <span data-ttu-id="f9159-113">ファイル名にワイルドカードを使用して、プロジェクト ディレクトリ内のすべての一致するファイルを使用せずにコンパイルできます`-recurse`です。</span><span class="sxs-lookup"><span data-stu-id="f9159-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="f9159-114">出力ファイル名が指定されていない場合、コンパイラは処理される最初の入力ファイルに出力ファイル名に基づいて行います。</span><span class="sxs-lookup"><span data-stu-id="f9159-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="f9159-115">これは、一般に、アルファベット順に表示されるときにコンパイルされたファイルの一覧の最初のファイルです。</span><span class="sxs-lookup"><span data-stu-id="f9159-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="f9159-116">この理由は、使用して出力ファイルを指定することをお、`-out`オプション。</span><span class="sxs-lookup"><span data-stu-id="f9159-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9159-117">`-recurse`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="f9159-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9159-118">例</span><span class="sxs-lookup"><span data-stu-id="f9159-118">Example</span></span>  
 <span data-ttu-id="f9159-119">次のコマンドは、現在のディレクトリ内のすべての Visual Basic ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f9159-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="f9159-120">次のコマンドですべての Visual Basic ファイルのコンパイル、`Test\ABC`ディレクトリと、その下には、そのディレクトリを生成し、`Test.ABC.dll`です。</span><span class="sxs-lookup"><span data-stu-id="f9159-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9159-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9159-121">See Also</span></span>  
 [<span data-ttu-id="f9159-122">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="f9159-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f9159-123">-除外 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9159-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="f9159-124">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="f9159-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
