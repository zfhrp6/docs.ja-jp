---
title: "/filealign |Microsoft ドキュメント"
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
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
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
ms.openlocfilehash: 5e0cd0a2a7e4c88df1087faee963f541c325b272
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="filealign"></a><span data-ttu-id="b8f74-102">/filealign</span><span class="sxs-lookup"><span data-stu-id="b8f74-102">/filealign</span></span>
<span data-ttu-id="b8f74-103">出力ファイルでセクションをアラインするサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8f74-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f74-104">構文</span><span class="sxs-lookup"><span data-stu-id="b8f74-104">Syntax</span></span>  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="b8f74-105">引数</span><span class="sxs-lookup"><span data-stu-id="b8f74-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="b8f74-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="b8f74-106">Required.</span></span> <span data-ttu-id="b8f74-107">出力ファイルにセクションの配置を指定する値。</span><span class="sxs-lookup"><span data-stu-id="b8f74-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="b8f74-108">有効な値は、512、1024、2048、4096、8192 です。</span><span class="sxs-lookup"><span data-stu-id="b8f74-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="b8f74-109">これらの値はバイト単位です。</span><span class="sxs-lookup"><span data-stu-id="b8f74-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8f74-110">コメント</span><span class="sxs-lookup"><span data-stu-id="b8f74-110">Remarks</span></span>  
 <span data-ttu-id="b8f74-111">使用することができます、`/filealign`出力ファイルのセクションの配置を指定するオプションです。</span><span class="sxs-lookup"><span data-stu-id="b8f74-111">You can use the `/filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="b8f74-112">セクションは、コードまたはデータを含むポータブル実行可能 (PE) ファイル内の連続したメモリ ブロックです。</span><span class="sxs-lookup"><span data-stu-id="b8f74-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="b8f74-113">`/filealign`オプションを使用して、非標準の配置を使用してアプリケーションをコンパイルできます。 ほとんどの開発者は、このオプションを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b8f74-113">The `/filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="b8f74-114">各セクションがの倍数では境界に合わせて調整、`/filealign`値。</span><span class="sxs-lookup"><span data-stu-id="b8f74-114">Each section is aligned on a boundary that is a multiple of the `/filealign` value.</span></span> <span data-ttu-id="b8f74-115">固定の既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="b8f74-115">There is no fixed default.</span></span> <span data-ttu-id="b8f74-116">場合`/filealign`が指定されていない、コンパイラがコンパイル時に、既定値を選択します。</span><span class="sxs-lookup"><span data-stu-id="b8f74-116">If `/filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="b8f74-117">セクションのサイズを指定すると、出力ファイルのサイズを変更できます。</span><span class="sxs-lookup"><span data-stu-id="b8f74-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="b8f74-118">セクションのサイズを変更するには、小さなデバイスで実行されるプログラムに対して有効な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8f74-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8f74-119">`/filealign`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="b8f74-119">The `/filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f74-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8f74-120">See Also</span></span>  
 [<span data-ttu-id="b8f74-121">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="b8f74-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
