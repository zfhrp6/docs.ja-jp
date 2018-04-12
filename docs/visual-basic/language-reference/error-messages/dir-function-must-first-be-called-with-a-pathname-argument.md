---
title: '&#39; Dir &#39;関数で最初に呼び出さ必要があります、&#39;です。パス名 &#39;引数'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="7160e-102">&#39; Dir &#39;関数で最初に呼び出さ必要があります、&#39;です。パス名 &#39;引数</span><span class="sxs-lookup"><span data-stu-id="7160e-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="7160e-103">初めて呼び出したときに、`Dir`関数には含まれません、`PathName`引数。</span><span class="sxs-lookup"><span data-stu-id="7160e-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="7160e-104">最初に呼び出す`Dir`含める必要があります、`PathName`が後続の呼び出し`Dir`の次の項目を取得するパラメーターを含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7160e-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7160e-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7160e-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="7160e-106">指定、`PathName`関数呼び出しの引数。</span><span class="sxs-lookup"><span data-stu-id="7160e-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7160e-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="7160e-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
