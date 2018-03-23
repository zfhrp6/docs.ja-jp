---
title: -filealign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26ff29f00f00d3ea5dbbd0bbf01df4d7858771d0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-filealign"></a><span data-ttu-id="080c3-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="080c3-102">-filealign</span></span>
<span data-ttu-id="080c3-103">出力ファイルでセクションをアラインするサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="080c3-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="080c3-104">構文</span><span class="sxs-lookup"><span data-stu-id="080c3-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="080c3-105">引数</span><span class="sxs-lookup"><span data-stu-id="080c3-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="080c3-106">必須。</span><span class="sxs-lookup"><span data-stu-id="080c3-106">Required.</span></span> <span data-ttu-id="080c3-107">出力ファイルにセクションのアラインメントを指定する値。</span><span class="sxs-lookup"><span data-stu-id="080c3-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="080c3-108">有効値は 512、1024、2048、4096、および 8192 です。</span><span class="sxs-lookup"><span data-stu-id="080c3-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="080c3-109">これらの値はバイト単位です。</span><span class="sxs-lookup"><span data-stu-id="080c3-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="080c3-110">コメント</span><span class="sxs-lookup"><span data-stu-id="080c3-110">Remarks</span></span>  
 <span data-ttu-id="080c3-111">使用することができます、`-filealign`出力ファイルのセクションのアラインメントを指定するにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="080c3-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="080c3-112">セクションは、コードまたはデータを含むポータブル実行可能 (PE) ファイルの連続したメモリのブロックです。</span><span class="sxs-lookup"><span data-stu-id="080c3-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="080c3-113">`-filealign`オプションを使用して、非標準の配置を使用してアプリケーションをコンパイルできます。 ほとんどの開発者は、このオプションを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="080c3-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="080c3-114">各セクションでは、の倍数である境界に整列されます、`-filealign`値。</span><span class="sxs-lookup"><span data-stu-id="080c3-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="080c3-115">固定の既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="080c3-115">There is no fixed default.</span></span> <span data-ttu-id="080c3-116">場合`-filealign`が指定されていない、コンパイラがコンパイル時に、既定値を選択します。</span><span class="sxs-lookup"><span data-stu-id="080c3-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="080c3-117">セクションのサイズを指定すると、出力ファイルのサイズを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="080c3-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="080c3-118">セクションのサイズ変更は、比較的小さなデバイスで実行されるプログラムに対して有効な場合があります。</span><span class="sxs-lookup"><span data-stu-id="080c3-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="080c3-119">`-filealign`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="080c3-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="080c3-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="080c3-120">See Also</span></span>  
 [<span data-ttu-id="080c3-121">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="080c3-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
