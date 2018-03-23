---
title: '@ (応答ファイルの指定) (Visual Basic)'
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af66000208dee0896792892a52dc6acdf5cb1e37
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="73818-102">@ (応答ファイルの指定) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73818-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="73818-103">コンパイラ オプションを含むファイルをコンパイルするソース コード ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="73818-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73818-104">構文</span><span class="sxs-lookup"><span data-stu-id="73818-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="73818-105">引数</span><span class="sxs-lookup"><span data-stu-id="73818-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="73818-106">必須。</span><span class="sxs-lookup"><span data-stu-id="73818-106">Required.</span></span> <span data-ttu-id="73818-107">ファイルをコンパイルするには、コンパイラ オプションまたはソース コード ファイルの一覧です。</span><span class="sxs-lookup"><span data-stu-id="73818-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="73818-108">ファイル名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="73818-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73818-109">コメント</span><span class="sxs-lookup"><span data-stu-id="73818-109">Remarks</span></span>  
 <span data-ttu-id="73818-110">コンパイラは、コンパイラ オプションとコマンド ラインで指定した場合、応答ファイルで指定されたソース コード ファイルを処理します。</span><span class="sxs-lookup"><span data-stu-id="73818-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="73818-111">コンパイル時に 1 つ以上の応答ファイルを指定するには、次などの複数の応答ファイル オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="73818-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="73818-112">応答ファイルでは、複数のコンパイラ オプションおよびソース コード ファイルが 1 行に表示されることができます。</span><span class="sxs-lookup"><span data-stu-id="73818-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="73818-113">コンパイラ オプションの 1 つ指定する必要があります (複数行にまたがることはできません) 1 つの行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="73818-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="73818-114">応答ファイルで始まるコメントを持つことができます、`#`シンボル。</span><span class="sxs-lookup"><span data-stu-id="73818-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="73818-115">1 つまたは複数の応答ファイルで指定されたオプションで、コマンドラインで指定できるオプションを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="73818-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="73818-116">コンパイラは、検出すると、それらのコマンド オプションを処理します。</span><span class="sxs-lookup"><span data-stu-id="73818-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="73818-117">したがって、コマンドライン引数は、応答ファイルで指定したオプションをオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="73818-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="73818-118">逆に、応答ファイル内のオプションは、前の表に、コマンドラインで、または他の応答ファイルのオプションをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="73818-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="73818-119">Visual Basic では、Vbc.exe ファイルと同じディレクトリにある Vbc.rsp ファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="73818-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="73818-120">しない限り、既定では、Vbc.rsp ファイルが含まれている、`-noconfig`オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="73818-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="73818-121">詳細については、次を参照してください。 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)です。</span><span class="sxs-lookup"><span data-stu-id="73818-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73818-122">`@`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="73818-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73818-123">例</span><span class="sxs-lookup"><span data-stu-id="73818-123">Example</span></span>  
 <span data-ttu-id="73818-124">次の行は、サンプルの応答ファイルからです。</span><span class="sxs-lookup"><span data-stu-id="73818-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="73818-125">例</span><span class="sxs-lookup"><span data-stu-id="73818-125">Example</span></span>  
 <span data-ttu-id="73818-126">次の例で使用する方法、`@`という名前の応答ファイルを持つオプション`File1.rsp`です。</span><span class="sxs-lookup"><span data-stu-id="73818-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="73818-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="73818-127">See Also</span></span>  
 [<span data-ttu-id="73818-128">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="73818-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="73818-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="73818-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="73818-130">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="73818-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
