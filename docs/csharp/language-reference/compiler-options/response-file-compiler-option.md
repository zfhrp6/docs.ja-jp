---
title: "@ (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@'
dev_langs:
- CSharp
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 219c12e4e3c9b847400f00a135d58506c72d2e7f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-c-compiler-options"></a><span data-ttu-id="bf107-102">@ (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="bf107-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="bf107-103">@ オプションを使用すると、コンパイラ オプションおよびコンパイルするソース コード ファイルを含むファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bf107-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf107-104">構文</span><span class="sxs-lookup"><span data-stu-id="bf107-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf107-105">引数</span><span class="sxs-lookup"><span data-stu-id="bf107-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="bf107-106">コンパイラ オプションやコンパイルするソース コード ファイルの一覧を含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="bf107-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf107-107">コメント</span><span class="sxs-lookup"><span data-stu-id="bf107-107">Remarks</span></span>  
 <span data-ttu-id="bf107-108">コンパイラ オプションとソース コード ファイルは、コマンド ラインで指定した場合と同じように、コンパイラによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="bf107-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="bf107-109">コンパイル時に複数の応答ファイルを指定するには、複数の応答ファイル オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="bf107-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="bf107-110">例:</span><span class="sxs-lookup"><span data-stu-id="bf107-110">For example:</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="bf107-111">応答ファイルでは、複数のコンパイラ オプションとソース コード ファイルを 1 行に記述できます。</span><span class="sxs-lookup"><span data-stu-id="bf107-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="bf107-112">1 つのコンパイラ オプションは 1 行に指定する必要があり、複数行にわたって指定できません。</span><span class="sxs-lookup"><span data-stu-id="bf107-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="bf107-113">応答ファイルには、シャープ記号 (#) で始まるコメントを記述できます。</span><span class="sxs-lookup"><span data-stu-id="bf107-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="bf107-114">応答ファイルでのコンパイラ オプションの指定方法は、コマンド ラインでのコンパイラ オプションの指定方法と同じです。</span><span class="sxs-lookup"><span data-stu-id="bf107-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="bf107-115">詳細については、「[Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」(コマンド ラインからのビルド) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf107-115">See [Building from the Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="bf107-116">コンパイラは、検出した順にコマンド オプションを処理します。</span><span class="sxs-lookup"><span data-stu-id="bf107-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="bf107-117">このため、コマンド ライン引数によって、応答ファイルで先に指定したオプションをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="bf107-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="bf107-118">逆に、応答ファイルのオプションが、コマンド ラインや他の応答ファイルで先に指定したオプションをオーバーライドすることもあります。</span><span class="sxs-lookup"><span data-stu-id="bf107-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="bf107-119">C# では、csc.exe ファイルと同じディレクトリに csc.rsp ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="bf107-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="bf107-120">csc.rsp の詳細については、「[/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf107-120">See [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="bf107-121">このコンパイラ オプションは、Visual Studio 開発環境で設定することはできません。また、プログラムで変更することもできません。</span><span class="sxs-lookup"><span data-stu-id="bf107-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf107-122">例</span><span class="sxs-lookup"><span data-stu-id="bf107-122">Example</span></span>  
 <span data-ttu-id="bf107-123">サンプルの応答ファイルの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bf107-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf107-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf107-124">See Also</span></span>  
 [<span data-ttu-id="bf107-125">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="bf107-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

