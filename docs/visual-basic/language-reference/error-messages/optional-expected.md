---
title: '&#39;省略可能な&#39;が必要です'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 52e4288255a246f78730b33beb55f6d2d83ff214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="39optional39-expected"></a><span data-ttu-id="ceb18-102">&#39;省略可能な&#39;が必要です</span><span class="sxs-lookup"><span data-stu-id="ceb18-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="ceb18-103">プロシージャの宣言で省略可能な引数には、必須の引数が続きます。</span><span class="sxs-lookup"><span data-stu-id="ceb18-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="ceb18-104">各引数は次のオプションの引数も省略可能な場合があります。</span><span class="sxs-lookup"><span data-stu-id="ceb18-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="ceb18-105">**エラー ID:** BC30202</span><span class="sxs-lookup"><span data-stu-id="ceb18-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ceb18-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ceb18-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="ceb18-107">引数が必要になるとしている場合は、引数リストの最初の省略可能な引数の前に移動します。</span><span class="sxs-lookup"><span data-stu-id="ceb18-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="ceb18-108">引数は省略可能としている場合を使用して、`Optional`キーワード。</span><span class="sxs-lookup"><span data-stu-id="ceb18-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb18-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceb18-109">See Also</span></span>  
 [<span data-ttu-id="ceb18-110">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="ceb18-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
