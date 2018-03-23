---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12d40e5acda73786ee88d16bacd9bc5f69400be8
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="4c519-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c519-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="4c519-103">示す、64 ビット実行可能ファイルまたは実行可能ファイルでマークされているかどうか、 [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)コンパイラ オプションで高エントロピ ASLR Address Space レイアウトのランダム化 () をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4c519-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c519-104">構文</span><span class="sxs-lookup"><span data-stu-id="4c519-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4c519-105">引数</span><span class="sxs-lookup"><span data-stu-id="4c519-105">Arguments</span></span>  
 <span data-ttu-id="4c519-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4c519-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="4c519-107">任意。</span><span class="sxs-lookup"><span data-stu-id="4c519-107">Optional.</span></span> <span data-ttu-id="4c519-108">オプションは既定で無効または指定したかどうかは`-highentropyva-`します。</span><span class="sxs-lookup"><span data-stu-id="4c519-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="4c519-109">指定したかどうか、オプションで`-highentropyva`または`-highentropyva+`です。</span><span class="sxs-lookup"><span data-stu-id="4c519-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c519-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4c519-110">Remarks</span></span>  
 <span data-ttu-id="4c519-111">このオプションを指定する場合、互換性のあるバージョンの Windows カーネルは、カーネル プロセスのアドレス領域のレイアウトを ASLR の一部としてランダムにときにより高度なエントロピを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c519-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="4c519-112">カーネルより高度なエントロピを使用している場合、アドレスの数が多いをスタックとヒープなどのメモリ領域に割り当てられることができます。</span><span class="sxs-lookup"><span data-stu-id="4c519-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="4c519-113">これによって特定のメモリ領域の位置を推測しづらくなる効果が得られます。</span><span class="sxs-lookup"><span data-stu-id="4c519-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="4c519-114">オプションがオンで、ターゲットの実行可能ファイルとすべてのモジュールは、ポインター値は、これらのモジュールは、64 ビット プロセスとして実行しているときに、4 ギガバイト (GB) より大きいを処理することが依存している必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c519-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c519-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c519-115">See Also</span></span>  
 [<span data-ttu-id="4c519-116">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="4c519-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4c519-117">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="4c519-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
