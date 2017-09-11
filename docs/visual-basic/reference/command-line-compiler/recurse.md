---
title: "/recurse |Microsoft ドキュメント"
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
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9ceb2f3bc9e4d0f1088258f504b7a49c58a29e35
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="recurse"></a><span data-ttu-id="14ea2-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="14ea2-102">/recurse</span></span>
<span data-ttu-id="14ea2-103">指定されたディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="14ea2-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ea2-104">構文</span><span class="sxs-lookup"><span data-stu-id="14ea2-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="14ea2-105">引数</span><span class="sxs-lookup"><span data-stu-id="14ea2-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="14ea2-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="14ea2-106">Optional.</span></span> <span data-ttu-id="14ea2-107">検索を開始するディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="14ea2-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="14ea2-108">指定されていない場合は、プロジェクト ディレクトリに、検索が開始されます。</span><span class="sxs-lookup"><span data-stu-id="14ea2-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="14ea2-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="14ea2-109">Required.</span></span> <span data-ttu-id="14ea2-110">検索するファイルです。</span><span class="sxs-lookup"><span data-stu-id="14ea2-110">The file(s) to search for.</span></span> <span data-ttu-id="14ea2-111">ワイルドカード文字が許可されています。</span><span class="sxs-lookup"><span data-stu-id="14ea2-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14ea2-112">コメント</span><span class="sxs-lookup"><span data-stu-id="14ea2-112">Remarks</span></span>  
 <span data-ttu-id="14ea2-113">ファイル名にワイルドカードを使用して、プロジェクト ディレクトリ内のすべての一致するファイルを使用せずにコンパイルできる`/recurse`です。</span><span class="sxs-lookup"><span data-stu-id="14ea2-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="14ea2-114">出力ファイル名が指定されていない場合、コンパイラは処理された最初の入力ファイルに出力ファイル名を行います。</span><span class="sxs-lookup"><span data-stu-id="14ea2-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="14ea2-115">これは、一般に、アルファベット順に表示されるときにコンパイルされたファイルの一覧の最初のファイルです。</span><span class="sxs-lookup"><span data-stu-id="14ea2-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="14ea2-116">この理由は、使用して出力ファイルを指定することをお、`/out`オプション。</span><span class="sxs-lookup"><span data-stu-id="14ea2-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14ea2-117">`/recurse`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="14ea2-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14ea2-118">例</span><span class="sxs-lookup"><span data-stu-id="14ea2-118">Example</span></span>  
 <span data-ttu-id="14ea2-119">次のコードでは、すべてをコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]現在のディレクトリ内のファイルです。</span><span class="sxs-lookup"><span data-stu-id="14ea2-119">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="14ea2-120">次のコードでは、すべてをコンパイル[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]にファイルを`Test\ABC`ディレクトリと、その下には、そのディレクトリを生成し、`Test.ABC.dll`です。</span><span class="sxs-lookup"><span data-stu-id="14ea2-120">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="14ea2-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="14ea2-121">See Also</span></span>  
 <span data-ttu-id="14ea2-122">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="14ea2-122">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="14ea2-123"> [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span><span class="sxs-lookup"><span data-stu-id="14ea2-123"> [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span></span>  
<span data-ttu-id="14ea2-124"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="14ea2-124"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
