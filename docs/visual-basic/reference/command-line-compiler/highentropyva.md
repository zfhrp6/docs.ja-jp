---
title: /highentropyva (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55568808bb94f98ce7a20016fc5a2a0a2ef23a38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="highentropyva-visual-basic"></a><span data-ttu-id="7a40e-102">/highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a40e-102">/highentropyva (Visual Basic)</span></span>
<span data-ttu-id="7a40e-103">示す、64 ビット実行可能ファイルまたは実行可能ファイルでマークされているかどうか、 [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)コンパイラ オプションで高エントロピ ASLR Address Space レイアウトのランダム化 () をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7a40e-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a40e-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a40e-104">Syntax</span></span>  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7a40e-105">引数</span><span class="sxs-lookup"><span data-stu-id="7a40e-105">Arguments</span></span>  
 <span data-ttu-id="7a40e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7a40e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="7a40e-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7a40e-107">Optional.</span></span> <span data-ttu-id="7a40e-108">オプションは既定で無効または指定したかどうかは`/highentropyva-`します。</span><span class="sxs-lookup"><span data-stu-id="7a40e-108">The option is off by default or if you specify `/highentropyva-`.</span></span> <span data-ttu-id="7a40e-109">指定したかどうか、オプションで`/highentropyva`または`/highentropyva+`です。</span><span class="sxs-lookup"><span data-stu-id="7a40e-109">The option is on if you specify `/highentropyva` or `/highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a40e-110">コメント</span><span class="sxs-lookup"><span data-stu-id="7a40e-110">Remarks</span></span>  
 <span data-ttu-id="7a40e-111">このオプションを指定する場合、互換性のあるバージョンの Windows カーネルは、カーネル プロセスのアドレス領域のレイアウトを ASLR の一部としてランダムにときにより高度なエントロピを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7a40e-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="7a40e-112">カーネルより高度なエントロピを使用している場合、アドレスの数が多いをスタックとヒープなどのメモリ領域に割り当てられることができます。</span><span class="sxs-lookup"><span data-stu-id="7a40e-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="7a40e-113">これによって特定のメモリ領域の位置を推測しづらくなる効果が得られます。</span><span class="sxs-lookup"><span data-stu-id="7a40e-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="7a40e-114">オプションがオンで、ターゲットの実行可能ファイルとすべてのモジュールは、ポインター値は、これらのモジュールは、64 ビット プロセスとして実行しているときに、4 ギガバイト (GB) より大きいを処理することが依存している必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a40e-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a40e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a40e-115">See Also</span></span>  
 [<span data-ttu-id="7a40e-116">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="7a40e-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7a40e-117">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="7a40e-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
