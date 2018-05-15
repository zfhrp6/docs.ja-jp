---
title: '&#39;Dir&#39;関数は最初に呼び出されなければなりません、 &#39;PathName&#39;引数'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 3a271d7c2c2f7b98bae8f3f6fa9b67b65e3548f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="c8de5-102">&#39;Dir&#39;関数は最初に呼び出されなければなりません、 &#39;PathName&#39;引数</span><span class="sxs-lookup"><span data-stu-id="c8de5-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="c8de5-103">初めて呼び出したときに、`Dir`関数には含まれません、`PathName`引数。</span><span class="sxs-lookup"><span data-stu-id="c8de5-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="c8de5-104">最初に呼び出す`Dir`含める必要があります、`PathName`が後続の呼び出し`Dir`の次の項目を取得するパラメーターを含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c8de5-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8de5-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c8de5-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c8de5-106">指定、`PathName`関数呼び出しの引数。</span><span class="sxs-lookup"><span data-stu-id="c8de5-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8de5-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8de5-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
