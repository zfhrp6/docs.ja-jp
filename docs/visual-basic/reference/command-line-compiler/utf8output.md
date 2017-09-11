---
title: "/utf8output (Visual Basic) |Microsoft ドキュメント"
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
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: 11
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
ms.openlocfilehash: 45361fb1dca34f2cdc849184d0e316b27d9545b6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="utf8output-visual-basic"></a><span data-ttu-id="8b6cb-102">/utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b6cb-102">/utf8output (Visual Basic)</span></span>
<span data-ttu-id="8b6cb-103">UTF-8 エンコードを使用してコンパイラ出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b6cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b6cb-104">Syntax</span></span>  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b6cb-105">引数</span><span class="sxs-lookup"><span data-stu-id="8b6cb-105">Arguments</span></span>  
 <span data-ttu-id="8b6cb-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8b6cb-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="8b6cb-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-107">Optional.</span></span> <span data-ttu-id="8b6cb-108">このオプションの既定値は`/utf8output-`、つまり、コンパイラの出力では、utf-8 エンコーディングは使用されません。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-108">The default for this option is `/utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="8b6cb-109">指定する`/utf8output`を指定することと同じ`/utf8output+`します。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-109">Specifying `/utf8output` is the same as specifying `/utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b6cb-110">コメント</span><span class="sxs-lookup"><span data-stu-id="8b6cb-110">Remarks</span></span>  
 <span data-ttu-id="8b6cb-111">国際対応の構成によっては、コンパイラの出力は、コンソールで正常に表示できません。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="8b6cb-112">このような状況で使用して`/utf8output`してコンパイラの出力をファイルにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-112">In such situations, use `/utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6cb-113">`/utf8output`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-113">The `/utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b6cb-114">例</span><span class="sxs-lookup"><span data-stu-id="8b6cb-114">Example</span></span>  
 <span data-ttu-id="8b6cb-115">次のコードのコンパイル`In.vb`を表示するコンパイラを utf-8 エンコードを使用して出力します。</span><span class="sxs-lookup"><span data-stu-id="8b6cb-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b6cb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b6cb-116">See Also</span></span>  
 <span data-ttu-id="8b6cb-117">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="8b6cb-117">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="8b6cb-118"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="8b6cb-118"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
