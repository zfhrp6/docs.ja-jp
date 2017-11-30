---
title: "引数 &#39;期間 &#39;引数と等しいかそれよりも小さい &#39; にする必要があります。ライフ &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrFinancial_PeriodLELife
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9db4bb58039406f2e98aed50874db73903150ed5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="argument-39period39-must-be-less-than-or-equal-to-argument-39life39"></a><span data-ttu-id="1128b-102">引数 &#39;期間 &#39;引数と等しいかそれよりも小さい &#39; にする必要があります。ライフ &#39;</span><span class="sxs-lookup"><span data-stu-id="1128b-102">Argument &#39;Period&#39; must be less than or equal to argument &#39;Life&#39;</span></span>
<span data-ttu-id="1128b-103">資産の減価償却費計算の対象期間を指定する `Period` 引数の値が `Life` 引数の値より大きくなっています。</span><span class="sxs-lookup"><span data-stu-id="1128b-103">The value of the `Period` argument, which specifies the period for which asset depreciation is calculated, is greater than the value of the `Life` argument.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1128b-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1128b-104">To correct this error</span></span>  
  
-   <span data-ttu-id="1128b-105">`Life` 引数と `Period` 引数の両方が同じ単位で指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1128b-105">Ensure that the `Life` and `Period` arguments are expressed in the same units.</span></span> <span data-ttu-id="1128b-106">たとえば、 `Life` を月単位で指定する場合は、 `Period` も月単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="1128b-106">For example, if `Life` is measured in months, `Period` should be as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1128b-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="1128b-107">See Also</span></span>  
 [<span data-ttu-id="1128b-108">NOT IN BUILD: DDB 関数</span><span class="sxs-lookup"><span data-stu-id="1128b-108">NOT IN BUILD: DDB Function</span></span>](http://msdn.microsoft.com/en-us/c7cf8929-d158-4399-b3cb-31d897d12556)  
 [<span data-ttu-id="1128b-109">NOT IN BUILD: SYD 関数</span><span class="sxs-lookup"><span data-stu-id="1128b-109">NOT IN BUILD: SYD Function</span></span>](http://msdn.microsoft.com/en-us/23c25672-f5dd-49ac-9893-4faa82634181)  
 [<span data-ttu-id="1128b-110">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="1128b-110">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
