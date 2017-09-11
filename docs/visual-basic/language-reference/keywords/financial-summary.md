---
title: "財務処理の概要 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- financial functions
- payment
ms.assetid: 474f973e-7103-42b7-aa4d-367c935e07e1
caps.latest.revision: 10
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
ms.openlocfilehash: 47224a79942bd2b4adbe652f920be774e9f1c73d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="financial-summary-visual-basic"></a><span data-ttu-id="a0206-102">財務処理の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0206-102">Financial Summary (Visual Basic)</span></span>
<span data-ttu-id="a0206-103">以下の表は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 言語のキーワードとランタイム ライブラリ メンバーを目的および使用方法別に分類したものです。</span><span class="sxs-lookup"><span data-stu-id="a0206-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] language keywords and run-time library members are organized by purpose and use.</span></span>  
  
|<span data-ttu-id="a0206-104">アクション</span><span class="sxs-lookup"><span data-stu-id="a0206-104">Action</span></span>|<span data-ttu-id="a0206-105">言語要素</span><span class="sxs-lookup"><span data-stu-id="a0206-105">Language element</span></span>|  
|------------|----------------------|  
|<span data-ttu-id="a0206-106">減価償却費の計算</span><span class="sxs-lookup"><span data-stu-id="a0206-106">Calculate depreciation.</span></span>|<span data-ttu-id="a0206-107"><xref:Microsoft.VisualBasic.Financial.DDB%2A>, <xref:Microsoft.VisualBasic.Financial.SLN%2A>, <xref:Microsoft.VisualBasic.Financial.SYD%2A></xref:Microsoft.VisualBasic.Financial.SYD%2A></xref:Microsoft.VisualBasic.Financial.SLN%2A></xref:Microsoft.VisualBasic.Financial.DDB%2A></span><span class="sxs-lookup"><span data-stu-id="a0206-107"><xref:Microsoft.VisualBasic.Financial.DDB%2A>, <xref:Microsoft.VisualBasic.Financial.SLN%2A>, <xref:Microsoft.VisualBasic.Financial.SYD%2A></span></span>|  
|<span data-ttu-id="a0206-108">将来価値の計算</span><span class="sxs-lookup"><span data-stu-id="a0206-108">Calculate future value.</span></span>|<span data-ttu-id="a0206-109"><xref:Microsoft.VisualBasic.Financial.FV%2A></xref:Microsoft.VisualBasic.Financial.FV%2A></span><span class="sxs-lookup"><span data-stu-id="a0206-109"><xref:Microsoft.VisualBasic.Financial.FV%2A></span></span>|  
|<span data-ttu-id="a0206-110">利率の計算</span><span class="sxs-lookup"><span data-stu-id="a0206-110">Calculate interest rate.</span></span>|<span data-ttu-id="a0206-111"><xref:Microsoft.VisualBasic.Financial.Rate%2A></xref:Microsoft.VisualBasic.Financial.Rate%2A></span><span class="sxs-lookup"><span data-stu-id="a0206-111"><xref:Microsoft.VisualBasic.Financial.Rate%2A></span></span>|  
|<span data-ttu-id="a0206-112">内部利益率の計算</span><span class="sxs-lookup"><span data-stu-id="a0206-112">Calculate internal rate of return.</span></span>|<span data-ttu-id="a0206-113"><xref:Microsoft.VisualBasic.Financial.IRR%2A>,<xref:Microsoft.VisualBasic.Financial.MIRR%2A></xref:Microsoft.VisualBasic.Financial.MIRR%2A></xref:Microsoft.VisualBasic.Financial.IRR%2A></span><span class="sxs-lookup"><span data-stu-id="a0206-113"><xref:Microsoft.VisualBasic.Financial.IRR%2A>, <xref:Microsoft.VisualBasic.Financial.MIRR%2A></span></span>|  
|<span data-ttu-id="a0206-114">期間の計算</span><span class="sxs-lookup"><span data-stu-id="a0206-114">Calculate number of periods.</span></span>|<span data-ttu-id="a0206-115"><xref:Microsoft.VisualBasic.Financial.NPer%2A></xref:Microsoft.VisualBasic.Financial.NPer%2A></span><span class="sxs-lookup"><span data-stu-id="a0206-115"><xref:Microsoft.VisualBasic.Financial.NPer%2A></span></span>|  
|<span data-ttu-id="a0206-116">支払い額の計算</span><span class="sxs-lookup"><span data-stu-id="a0206-116">Calculate payments.</span></span>|<span data-ttu-id="a0206-117"><xref:Microsoft.VisualBasic.Financial.IPmt%2A>, <xref:Microsoft.VisualBasic.Financial.Pmt%2A>, <xref:Microsoft.VisualBasic.Financial.PPmt%2A></xref:Microsoft.VisualBasic.Financial.PPmt%2A></xref:Microsoft.VisualBasic.Financial.Pmt%2A></xref:Microsoft.VisualBasic.Financial.IPmt%2A></span><span class="sxs-lookup"><span data-stu-id="a0206-117"><xref:Microsoft.VisualBasic.Financial.IPmt%2A>, <xref:Microsoft.VisualBasic.Financial.Pmt%2A>, <xref:Microsoft.VisualBasic.Financial.PPmt%2A></span></span>|  
|<span data-ttu-id="a0206-118">正味現在価値の計算</span><span class="sxs-lookup"><span data-stu-id="a0206-118">Calculate present value.</span></span>|<span data-ttu-id="a0206-119"><xref:Microsoft.VisualBasic.Financial.NPV%2A>,<xref:Microsoft.VisualBasic.Financial.PV%2A></xref:Microsoft.VisualBasic.Financial.PV%2A></xref:Microsoft.VisualBasic.Financial.NPV%2A></span><span class="sxs-lookup"><span data-stu-id="a0206-119"><xref:Microsoft.VisualBasic.Financial.NPV%2A>, <xref:Microsoft.VisualBasic.Financial.PV%2A></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0206-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0206-120">See Also</span></span>  
 <span data-ttu-id="a0206-121">[キーワード](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="a0206-121">[Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="a0206-122"> [Visual Basic ランタイム ライブラリのメンバー](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="a0206-122"> [Visual Basic Runtime Library Members](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>
