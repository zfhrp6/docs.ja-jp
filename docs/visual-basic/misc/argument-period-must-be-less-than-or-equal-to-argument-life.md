---
title: 引数&#39;期間&#39;引数以下である必要があります&#39;ライフ&#39;
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
ms.openlocfilehash: 5a9336be51a2d8a68ed700b60ced8a62bf2d932d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599032"
---
# <a name="argument-39period39-must-be-less-than-or-equal-to-argument-39life39"></a><span data-ttu-id="46adc-102">引数&#39;期間&#39;引数以下である必要があります&#39;ライフ&#39;</span><span class="sxs-lookup"><span data-stu-id="46adc-102">Argument &#39;Period&#39; must be less than or equal to argument &#39;Life&#39;</span></span>
<span data-ttu-id="46adc-103">資産の減価償却費計算の対象期間を指定する `Period` 引数の値が `Life` 引数の値より大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="46adc-103">The value of the `Period` argument, which specifies the period for which asset depreciation is calculated, is greater than the value of the `Life` argument.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46adc-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="46adc-104">To correct this error</span></span>  
  
-   <span data-ttu-id="46adc-105">`Life` 引数と `Period` 引数の両方が同じ単位で指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="46adc-105">Ensure that the `Life` and `Period` arguments are expressed in the same units.</span></span> <span data-ttu-id="46adc-106">たとえば、 `Life` を月単位で指定する場合は、 `Period` も月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="46adc-106">For example, if `Life` is measured in months, `Period` should be as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46adc-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="46adc-107">See Also</span></span>  
   
   
 [<span data-ttu-id="46adc-108">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="46adc-108">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
