---
title: 最適化
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 2f066835c5f864538f281d4c58772e0e60c132f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-optimize"></a><span data-ttu-id="187de-102">最適化</span><span class="sxs-lookup"><span data-stu-id="187de-102">-optimize</span></span>
<span data-ttu-id="187de-103">有効またはコンパイラの最適化を無効にします。</span><span class="sxs-lookup"><span data-stu-id="187de-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="187de-104">構文</span><span class="sxs-lookup"><span data-stu-id="187de-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="187de-105">引数</span><span class="sxs-lookup"><span data-stu-id="187de-105">Arguments</span></span>  
  
|<span data-ttu-id="187de-106">用語</span><span class="sxs-lookup"><span data-stu-id="187de-106">Term</span></span>|<span data-ttu-id="187de-107">定義</span><span class="sxs-lookup"><span data-stu-id="187de-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="187de-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="187de-108">`+` &#124; `-`</span></span>|<span data-ttu-id="187de-109">任意。</span><span class="sxs-lookup"><span data-stu-id="187de-109">Optional.</span></span> <span data-ttu-id="187de-110">`-optimize-`オプションは、コンパイラの最適化を無効になります。</span><span class="sxs-lookup"><span data-stu-id="187de-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="187de-111">`-optimize+`最適化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="187de-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="187de-112">既定では、最適化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="187de-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="187de-113">コメント</span><span class="sxs-lookup"><span data-stu-id="187de-113">Remarks</span></span>  
 <span data-ttu-id="187de-114">コンパイラを最適化すると、出力ファイルのサイズが小さくなり、動作が速くなり、処理の効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="187de-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="187de-115">ただし、出力ファイルでコードの再配置の最適化を行うので、`-optimize+`デバッグが困難です。</span><span class="sxs-lookup"><span data-stu-id="187de-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="187de-116">生成されるすべてのモジュール`-target:module`アセンブリを使用する必要があります同じ`-optimize`アセンブリとして設定します。</span><span class="sxs-lookup"><span data-stu-id="187de-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="187de-117">詳細については、次を参照してください。 [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)です。</span><span class="sxs-lookup"><span data-stu-id="187de-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="187de-118">組み合わせることができます、`-optimize`と`-debug`オプション。</span><span class="sxs-lookup"><span data-stu-id="187de-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="187de-119">Visual Studio 統合開発環境での最適化設定-</span><span class="sxs-lookup"><span data-stu-id="187de-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="187de-120">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="187de-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="187de-121">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="187de-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="187de-122">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="187de-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="187de-123">3.**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="187de-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="187de-124">4.変更、**の最適化を有効にする**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="187de-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="187de-125">例</span><span class="sxs-lookup"><span data-stu-id="187de-125">Example</span></span>  
 <span data-ttu-id="187de-126">次のコードのコンパイル`T2.vb`とコンパイラの最適化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="187de-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="187de-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="187de-127">See Also</span></span>  
 [<span data-ttu-id="187de-128">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="187de-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="187de-129">デバッグ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="187de-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="187de-130">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="187de-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="187de-131">-ターゲット (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="187de-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
