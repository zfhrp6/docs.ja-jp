---
title: "/optimize |Microsoft ドキュメント"
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
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization, enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: 15
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
ms.openlocfilehash: f01ab17d4a2f5d123538294a7a13d7a6d7a40267
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="optimize"></a><span data-ttu-id="e7cd1-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="e7cd1-102">/optimize</span></span>
<span data-ttu-id="e7cd1-103">有効またはコンパイラの最適化を無効にします。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7cd1-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7cd1-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7cd1-105">引数</span><span class="sxs-lookup"><span data-stu-id="e7cd1-105">Arguments</span></span>  
  
|<span data-ttu-id="e7cd1-106">用語</span><span class="sxs-lookup"><span data-stu-id="e7cd1-106">Term</span></span>|<span data-ttu-id="e7cd1-107">定義</span><span class="sxs-lookup"><span data-stu-id="e7cd1-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="e7cd1-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e7cd1-108">`+` &#124; `-`</span></span>|<span data-ttu-id="e7cd1-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-109">Optional.</span></span> <span data-ttu-id="e7cd1-110">`/optimize-`オプションは、コンパイラの最適化を無効になります。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="e7cd1-111">`/optimize+`の最適化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="e7cd1-112">既定では、最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7cd1-113">コメント</span><span class="sxs-lookup"><span data-stu-id="e7cd1-113">Remarks</span></span>  
 <span data-ttu-id="e7cd1-114">コンパイラの最適化は、小さく、高速、かつ効率的に出力ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="e7cd1-115">ただし、出力ファイルにコードの再配置の最適化を行うので、`/optimize+`デバッグが困難です。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="e7cd1-116">生成されるすべてのモジュール`/target:module`アセンブリは同じで使用する必要があります`/optimize`アセンブリとして設定します。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="e7cd1-117">詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)します。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="e7cd1-118">組み合わせることができます、`/optimize`と`/debug`オプション。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="e7cd1-119">Visual Studio 統合開発環境で/optimize を設定するには</span><span class="sxs-lookup"><span data-stu-id="e7cd1-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="e7cd1-120">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e7cd1-121">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="e7cd1-122">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="e7cd1-123">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="e7cd1-124">3.[詳細設定 **** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="e7cd1-125">4.変更、**の最適化を有効にする**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7cd1-126">例</span><span class="sxs-lookup"><span data-stu-id="e7cd1-126">Example</span></span>  
 <span data-ttu-id="e7cd1-127">次のコードのコンパイル`T2.vb`でき、コンパイラの最適化。</span><span class="sxs-lookup"><span data-stu-id="e7cd1-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7cd1-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7cd1-128">See Also</span></span>  
 <span data-ttu-id="e7cd1-129">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="e7cd1-129">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="e7cd1-130"> [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span><span class="sxs-lookup"><span data-stu-id="e7cd1-130"> [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span></span>  
<span data-ttu-id="e7cd1-131"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="e7cd1-131"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="e7cd1-132"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)</span><span class="sxs-lookup"><span data-stu-id="e7cd1-132"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)</span></span>
