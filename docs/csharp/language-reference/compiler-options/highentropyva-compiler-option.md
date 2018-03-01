---
title: "-highentropyva (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d0b9a7a53545623ae5d5692b52973744adbcc299
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="2cc19-102">-highentropyva (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2cc19-102">-highentropyva (C# Compiler Options)</span></span>
<span data-ttu-id="2cc19-103">**-highentropyva** コンパイラ オプションは、特定の実行可能ファイルで高エントロピ ASLR (Address Space Layout Randomization) をサポートするかどうかを Windows カーネルに示します。</span><span class="sxs-lookup"><span data-stu-id="2cc19-103">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc19-104">構文</span><span class="sxs-lookup"><span data-stu-id="2cc19-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cc19-105">引数</span><span class="sxs-lookup"><span data-stu-id="2cc19-105">Arguments</span></span>  
 <span data-ttu-id="2cc19-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2cc19-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2cc19-107">このオプションは、64 ビットの実行可能ファイルまたは [-platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) コンパイラ オプションによって示される実行可能ファイルで、高エントロピ仮想アドレス空間をサポートすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2cc19-107">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="2cc19-108">既定では、このオプションが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="2cc19-108">The option is disabled by default.</span></span> <span data-ttu-id="2cc19-109">有効にするには、**-highentropyva+** または **-highentropyva** を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2cc19-109">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cc19-110">コメント</span><span class="sxs-lookup"><span data-stu-id="2cc19-110">Remarks</span></span>  
 <span data-ttu-id="2cc19-111">**-highentropyva** オプションを指定すると、適合するバージョンの Windows カーネルで、ASLR の一環としてプロセスのアドレス空間レイアウトをランダム化する際、より高いエントロピを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2cc19-111">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="2cc19-112">より高いエントロピを使うということは、スタックやヒープといったメモリ領域に割り当てることのできるアドレス数が増えることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2cc19-112">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="2cc19-113">これによって特定のメモリ領域の位置を推測しづらくなる効果が得られます。</span><span class="sxs-lookup"><span data-stu-id="2cc19-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="2cc19-114">**-highentropyva** コンパイラ オプションが指定された場合、対象となる実行可能ファイルとその依存モジュールは、64 ビット プロセスとして動作する際に 4 ギガバイト (GB) を超えるポインター値を処理できることが必要です。</span><span class="sxs-lookup"><span data-stu-id="2cc19-114">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
