---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 753c92cdf2124ee7fb1b471c7bc543b6db6f3daa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="829fe-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="829fe-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="829fe-103">UTF-8 エンコードを使用してコンパイラ出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="829fe-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="829fe-104">構文</span><span class="sxs-lookup"><span data-stu-id="829fe-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="829fe-105">引数</span><span class="sxs-lookup"><span data-stu-id="829fe-105">Arguments</span></span>  
 <span data-ttu-id="829fe-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="829fe-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="829fe-107">任意。</span><span class="sxs-lookup"><span data-stu-id="829fe-107">Optional.</span></span> <span data-ttu-id="829fe-108">このオプションの既定値は`-utf8output-`、つまり、コンパイラの出力は utf-8 エンコードを使用しません。</span><span class="sxs-lookup"><span data-stu-id="829fe-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="829fe-109">指定する`-utf8output`を指定することと同じ`-utf8output+`です。</span><span class="sxs-lookup"><span data-stu-id="829fe-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="829fe-110">コメント</span><span class="sxs-lookup"><span data-stu-id="829fe-110">Remarks</span></span>  
 <span data-ttu-id="829fe-111">国際対応の構成によっては、コンパイラの出力は、コンソールで正常に表示できません。</span><span class="sxs-lookup"><span data-stu-id="829fe-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="829fe-112">このような状況で使用して`-utf8output`してコンパイラ出力をファイルにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="829fe-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="829fe-113">`-utf8output`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="829fe-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="829fe-114">例</span><span class="sxs-lookup"><span data-stu-id="829fe-114">Example</span></span>  
 <span data-ttu-id="829fe-115">次のコードのコンパイル`In.vb`表示をコンパイラに指示して utf-8 エンコードを使用して出力します。</span><span class="sxs-lookup"><span data-stu-id="829fe-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="829fe-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="829fe-116">See Also</span></span>  
 [<span data-ttu-id="829fe-117">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="829fe-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="829fe-118">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="829fe-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
