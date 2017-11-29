---
title: "0 による除算 (Visual Basic 実行時エラー)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID11
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a913e3b55b38430c0908f77aac79cb342e78719
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="division-by-zero-visual-basic-run-time-error"></a><span data-ttu-id="6e4cc-102">0 による除算 (Visual Basic 実行時エラー)</span><span class="sxs-lookup"><span data-stu-id="6e4cc-102">Division by zero (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="6e4cc-103">除数として使用する式の値が 0 です。</span><span class="sxs-lookup"><span data-stu-id="6e4cc-103">An expression being used as a divisor has a value of zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e4cc-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6e4cc-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="6e4cc-105">式の変数のスペルを確認します。</span><span class="sxs-lookup"><span data-stu-id="6e4cc-105">Check the spelling of variables in the expression.</span></span> <span data-ttu-id="6e4cc-106">変数名のスペルが間違っていると、0 に初期化される数値型の変数が暗黙的に生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="6e4cc-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
2.  <span data-ttu-id="6e4cc-107">式の変数 (特に、他のプロシージャから引数としてプロシージャに渡されたもの) に対してこれまで実行した操作を確認します。</span><span class="sxs-lookup"><span data-stu-id="6e4cc-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4cc-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e4cc-108">See Also</span></span>  
 [<span data-ttu-id="6e4cc-109">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="6e4cc-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="6e4cc-110">パラメーターの Visual Basic でのメカニズムの変更の引き渡し</span><span class="sxs-lookup"><span data-stu-id="6e4cc-110">Parameter Passing Mechanism Changes in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/0fa2b0dc-aa1c-4797-bbd6-aa13c611cab2)
