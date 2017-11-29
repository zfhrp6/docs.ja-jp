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
ms.openlocfilehash: fa19f1842bcfa82908fe79f6fda69bbc5dd9499c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="argument-39nper39-must-be-greater-than-zero"></a><span data-ttu-id="0b188-102">引数 &#39;NPer &#39;0 より大きくなければなりません</span><span class="sxs-lookup"><span data-stu-id="0b188-102">Argument &#39;NPer&#39; must be greater than zero</span></span>
<span data-ttu-id="0b188-103">`NPer` 関数 (定期定額払いおよび固定金利に基づいて年金の期間を指定する `Double` を返します) には、0 を超える引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="0b188-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0b188-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0b188-104">To correct this error</span></span>  
  
-   <span data-ttu-id="0b188-105">式の引数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="0b188-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="0b188-106">変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="0b188-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="0b188-107">式の変数 (特に、他のプロシージャから引数としてプロシージャに渡されたもの) に対してこれまで実行した操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="0b188-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b188-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b188-108">See Also</span></span>  
 [<span data-ttu-id="0b188-109">ビルド内にありません: NPer 関数</span><span class="sxs-lookup"><span data-stu-id="0b188-109">NOT IN BUILD: NPer Function</span></span>](http://msdn.microsoft.com/en-us/56567d16-29f7-4928-b05f-b4cd56d4fd42)  
 [<span data-ttu-id="0b188-110">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="0b188-110">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
