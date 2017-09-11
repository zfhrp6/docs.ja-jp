---
title: "/highentropyva (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
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
ms.openlocfilehash: ef482f142e07e96eabf93bd2223b0d24f351553b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="highentropyva-visual-basic"></a><span data-ttu-id="29357-102">/highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29357-102">/highentropyva (Visual Basic)</span></span>
<span data-ttu-id="29357-103">示す、64 ビット実行可能ファイルまたは実行可能ファイルでマークされているかどうか、 [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)コンパイラ オプションは、高エントロピ ASLR Address Space Layout Randomization () をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="29357-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29357-104">構文</span><span class="sxs-lookup"><span data-stu-id="29357-104">Syntax</span></span>  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="29357-105">引数</span><span class="sxs-lookup"><span data-stu-id="29357-105">Arguments</span></span>  
 <span data-ttu-id="29357-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="29357-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="29357-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="29357-107">Optional.</span></span> <span data-ttu-id="29357-108">オプションは既定で無効または指定した`/highentropyva-`します。</span><span class="sxs-lookup"><span data-stu-id="29357-108">The option is off by default or if you specify `/highentropyva-`.</span></span> <span data-ttu-id="29357-109">指定したかどうかに、オプションは、`/highentropyva`または`/highentropyva+`です。</span><span class="sxs-lookup"><span data-stu-id="29357-109">The option is on if you specify `/highentropyva` or `/highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29357-110">コメント</span><span class="sxs-lookup"><span data-stu-id="29357-110">Remarks</span></span>  
 <span data-ttu-id="29357-111">このオプションを指定する場合、Windows カーネルのバージョンに互換性のあるは、カーネル プロセスのアドレス領域のレイアウトを ASLR の一部としてランダムにときにより高度なエントロピーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="29357-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="29357-112">カーネルより高度なエントロピーを使用している場合、スタックとヒープなどのメモリ領域にアドレスの数が多いを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="29357-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="29357-113">その結果、特定のメモリ領域の位置を推測するより困難です。</span><span class="sxs-lookup"><span data-stu-id="29357-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="29357-114">オプションが、ターゲットの実行可能ファイルとすべてのモジュールでのこれらのモジュールは、64 ビット プロセスとして実行しているときに、4 ギガバイト (GB) よりも大きくポインター値を処理できない依存している必要があります。</span><span class="sxs-lookup"><span data-stu-id="29357-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29357-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="29357-115">See Also</span></span>  
 <span data-ttu-id="29357-116">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="29357-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="29357-117"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="29357-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
