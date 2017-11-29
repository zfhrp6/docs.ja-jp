---
title: "&#39; #ElseIf &#39;一致する &#39; #If &#39; の前が必要または &#39; #ElseIf &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords: BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b3a4e809e1108fcd6e116538a1947057e9548ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a><span data-ttu-id="101b9-102">&#39; #ElseIf &#39;一致する &#39; #If &#39; の前が必要または &#39; #ElseIf &#39;</span><span class="sxs-lookup"><span data-stu-id="101b9-102">&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;</span></span>
<span data-ttu-id="101b9-103">`#ElseIf`条件付きコンパイル ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="101b9-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="101b9-104">`#ElseIf`句の前に、対応する必要があります`#If`または`#ElseIf`句。</span><span class="sxs-lookup"><span data-stu-id="101b9-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="101b9-105">**エラー ID:** BC30014</span><span class="sxs-lookup"><span data-stu-id="101b9-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="101b9-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="101b9-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="101b9-107">確認先行`#If`または`#ElseIf`これから分割されたいない`#ElseIf`によって、中間の条件付きコンパイル ブロックや、間違って配置された`#End If`です。</span><span class="sxs-lookup"><span data-stu-id="101b9-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="101b9-108">場合、`#ElseIf`は後に、`#Else`ディレクティブを削除するか、`#Else`に変更して、または、`#ElseIf`です。</span><span class="sxs-lookup"><span data-stu-id="101b9-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="101b9-109">他のすべての順序が正しい場合、 `#If` ディレクティブを条件付きコンパイル ブロックの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="101b9-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101b9-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="101b9-110">See Also</span></span>  
 [<span data-ttu-id="101b9-111">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="101b9-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
