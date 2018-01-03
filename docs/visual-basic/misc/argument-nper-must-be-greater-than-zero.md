---
title: "引数 &#39;NPer &#39;0 より大きくなければなりません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2e0cf124b4d1fac562e5d1697c53ee7328fa759
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="argument-39nper39-must-be-greater-than-zero"></a><span data-ttu-id="f4031-102">引数 &#39;NPer &#39;0 より大きくなければなりません</span><span class="sxs-lookup"><span data-stu-id="f4031-102">Argument &#39;NPer&#39; must be greater than zero</span></span>
<span data-ttu-id="f4031-103">`NPer` 関数 (定期定額払いおよび固定金利に基づいて年金の期間を指定する `Double` を返します) には、0 を超える引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4031-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4031-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f4031-104">To correct this error</span></span>  
  
-   <span data-ttu-id="f4031-105">式の引数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="f4031-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="f4031-106">変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f4031-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="f4031-107">式の変数 (特に、他のプロシージャから引数としてプロシージャに渡されたもの) に対してこれまで実行した操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="f4031-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4031-108">参照</span><span class="sxs-lookup"><span data-stu-id="f4031-108">See Also</span></span>  
 [<span data-ttu-id="f4031-109">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="f4031-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
